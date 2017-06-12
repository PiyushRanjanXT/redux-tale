# redux-tale

[![Build Status](https://travis-ci.org/SaxoBank/redux-tale.svg?branch=master)](https://travis-ci.org/SaxoBank/redux-tale)

A simplified, smaller and synchronous-first re-implementation of redux-saga.

# Why

redux-saga is a great library that brings the full power of sagas to redux. We recommend you continue to use it if you use the advanced functionality e.g. channels, forking (as opposed to spawn), use of a monitor or reliance on the threading and async nature of redux-saga.

This library is largely compatible with redux-saga but with a few differences:

* Everything is sync-first. This means that "put" or redux dispatch happens immediately. It also means that a saga will run until it hits an async yield meaning that two synchronous running sagas will never interleave. This solves a few problems where using redux-saga you have to work-around sagas essentially making JavaScript multi-threaded. By being sync-first it is easier to predict cause and effect and optimize performance.
* This library is much smaller and contains a few less effects and functionality (minified it is approx. 22% smaller)

# Setup

```
import { createStore, applyMiddleware } from 'redux';
import createTaleMiddleware from 'redux-tale';
import reducer from './reducer';
import saga from './saga';

// create the saga middleware
const taleMiddleware = createTaleMiddleware();
// mount it on the Store
const store = createStore(
  reducer,
  applyMiddleware(taleMiddleware)
)

taleMiddleware.run(saga);
```

# API

### Apply
### Call
### Put
### Race
### Select
### Spawn
### Take
### Take Every

# Contributing
You want to contribute? Great! Have a look at our [contribution guidelines](CONTRIBUTING.md).
