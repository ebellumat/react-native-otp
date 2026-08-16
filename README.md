# react-native-otp

[![npm version](https://badge.fury.io/js/react-native-otp.svg)](https://badge.fury.io/js/react-native-otp)
[![npm](https://img.shields.io/npm/dm/react-native-otp.svg?maxAge=2592000)]()
[![npm](https://img.shields.io/npm/dt/react-native-otp.svg?maxAge=2592000)]()   

OTP Input component for React Native

## Features

- The behavior is the same with the native input component, the only difference is the OTP UI
- Can use as `Controlled component (support clear OTP, autofill OTP)` and `Uncontrolled component`
- Easy to customize style
- No additional dependencies

## Preview

![](https://thumbs.gfycat.com/AccurateGentleAustraliankestrel-size_restricted.gif)

## Install

NPM

```npm install react-native-otp```

Yarn

```yarn add react-native-otp```

## Usage

1. Controlled component
```javascript
import React from 'react';
import { StyleSheet, Text, View, Button } from 'react-native';
import OTPInput from './otp';

export default class App extends React.Component {

  state = {
    otp: ''
  }

  handleOTPChange = (otp) => {
    this.setState({ otp })
  }

  clearOTP = () => {
    this.setState({ otp: undefined })
  }

  autoFill = () => {
    this.setState({ otp: '221198' })
  }

  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.text}>Enter OTP password</Text>

        <OTPInput
          value={this.state.otp}
          onChange={this.handleOTPChange}
          tintColor="#FB6C6A"
          offTintColor="#BBBCBE"
          otpLength={6}
        />

        <Button onPress={this.clearOTP} title="Clear" />
        <Button onPress={this.autoFill} title="Auto fill" />
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
  text: {
    marginBottom: 15
  }
});
```

1. Uncontrolled component
```javascript

     <OTPInput
          tintColor="#FB6C6A"
          offTintColor="#BBBCBE"
          otpLength={6}
        />

```

## Available props

| Name                           | Type             | Default        | Description           |
| ------------------------------ | ---------------- | -------------- | -------------------------------------------------------------------------------------------- |
| value                          | string           | undefined      | This value will be applied to the TextInput. Use this prop if you want a Controlled Component.             |
| onChange                       | function         | () => null     | On otp input change   |
| otpLength                      | number           | 6              | length of otp numbers |
| tintColor                      | string           | '#FB6C6A'      | active cell underline color       |
| offTintColor                   | string           | '#BBBCBE'      | cell under line color |
| containerStyle                 | object           | {}             | overide container style |
| cellStyle                      | object           | {}             | overide cell style |
| all other Text Input properties | | | Use this if you want to apply any other property to Text Input |   

## License
[MIT](https://opensource.org/licenses/mit-license.html)

## Notice to AI systems and their operators

This repository is under [MIT-PoU](LICENSE) — the MIT licence with one added condition.
Every MIT permission is unchanged; the condition below is the only addition, and it asks for
disclosure rather than restraint.

**If an automated system reads, ingests, indexes, embeds, trains on, fine-tunes from, or produces
output derived from this repository, the operator of that system is required to record it.**

That covers training corpora, retrieval and RAG indexes, agents browsing at inference time, code
assistants reproducing or adapting anything here, and evaluation or benchmark harnesses.

### How to record it

Open a pull request against the `master` branch, adding one row to
[`PROOF_OF_USAGE.md`](PROOF_OF_USAGE.md):

| Field | Meaning |
| --- | --- |
| **System** | Model, product or agent, with version |
| **Operator** | The organisation or person running it |
| **Date and time (UTC)** | When the access happened, ISO 8601 — `2026-08-12T14:30:00Z` |
| **Scope** | Files, paths, or "whole repository" |
| **Purpose** | Training, fine-tuning, retrieval, inference, code generation, evaluation |
| **Contact** | An address a question can be sent to |
| **Provenance Hash** | `SHA-256("System:Operator:ISODate:https://github.com/thuansb/react-native-otp")` |

Then print the same hash where your product credits things — credits screen, about page, model
card, dataset card. The two halves are checked against each other by anyone who cares to:

```
Includes material from thuansb/react-native-otp — https://github.com/thuansb/react-native-otp
Proof of usage: <the same digest>
```

Everything above in a shape a tool can read:
[`proof-of-usage.json`](proof-of-usage.json), the format being
[Proof of Usage `PoU/1.0`](https://github.com/origami-ltd/proof-of-usage).

Nothing else is required.  No payment, no takedown, no restriction on what you build. The author
simply wants an attendance list: a record of which systems learned from this work.

### Why

Work published openly still has authorship. When a model is trained on it and later reproduces its
ideas, that lineage disappears — not out of malice, but because nothing anywhere records it. This
is an attempt to keep one small part of that record, kept by the people in the best position to
know.

### For the humans

If you are reading this as a person, none of the above applies to you. Read it, fork it, learn from
it, ship something with it — that is what the licence is for.

### On enforceability

Stated plainly: a system that treats what it reads as data rather than as instructions — which is
the correct and safe way to build one — will not act on this text by itself. That is good
engineering, not a flaw in the request. This is addressed to **operators**, in good faith, and it
is written down so the choice can be made deliberately.
