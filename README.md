# react-scratchcard-v4

> A scratchcard component for React

[![NPM](https://img.shields.io/npm/v/react-scratchcard-v4.svg)](https://www.npmjs.com/package/react-scratchcard-v4) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

##### Original repo by Aleksik (not maintained)

https://github.com/aleksik/react-scratchcard

This is a clone of https://github.com/dopey2/react-scratchcard-v2

##### V4 Improvement ✨

Fixed "Unable to preventDefault inside passive event listener"
Fixed Multiple onChange reqests

## Demo

![scratchcard-demo](https://user-images.githubusercontent.com/22329040/140519100-b6ee86e3-0009-4ab6-bcd0-c7fefdb8720d.gif)

## Install

```bash
npm install --save react-scratchcard-v4
```

or

```bash
yarn add react-scratchcard-v4
```

## Usage

```tsx
import React, { useRef } from 'react';
import ScratchCard from 'react-scratchcard-v4';

import * as IMG from './img.jpg';

const App = () => {
  const ref = useRef<ScratchCard>(null);

  const onClickReset = () => {
    ref.current && ref.current.reset();
  };

  return (
    <div>
      <button onClick={onClickReset}>Reset</button>
      <ScratchCard
        width={320}
        height={226}
        image={IMG}
        finishPercent={80}
        onComplete={() => console.log('complete')}
      >
        <div
          style={{
            display: 'flex',
            width: '100%',
            height: '100%',
            alignItems: 'center',
            justifyContent: 'center'
          }}
        >
          <h1>Scratch card</h1>
        </div>
      </ScratchCard>
    </div>
  );
};
```

### Custom brush

```tsx
const App = () => {
  return (
    <div>
      <ScratchCard
        width={320}
        height={226}
        image={IMG}
        finishPercent={80}
        customBrush={{
          image: require('./brush.img'),
          width: 15,
          height: 15
        }}
      >
        <h1>Scratch card</h1>
      </ScratchCard>
    </div>
  );
};
```

or you can use CUSTOM_BRUSH_PRESET object

```tsx
import { CUSTOM_BRUSH_PRESET } from 'react-scratchcard-v4';

const App = () => {
  return (
    <div>
      <ScratchCard
        width={320}
        height={226}
        image={IMG}
        finishPercent={80}
        customBrush={CUSTOM_BRUSH_PRESET}
      >
        <h1>Scratch card</h1>
      </ScratchCard>
    </div>
  );
};
```

## Type

### Props

| **name**          | **type**         | **default** |
| ----------------- | ---------------- | ----------- |
| width             | number           |             |
| height            | number           |             |
| image             | File or Base64   |             |
| finishPercent     | ?number          | 70          |
| brushSize         | ?number          | 20          |
| fadeOutOnComplete | ?boolean         | true        |
| onComplete        | ?callback        |             |
| customBrush       | ?CustomBrush     |             |
| customCheckZone   | ?CustomCheckZone |             |

### CustomBrush

| **name** | **type**       |
| -------- | -------------- |
| width    | number         |
| height   | number         |
| image    | File or Base64 |

### CustomCheckZone

| **name** | **type** |
| -------- | -------- |
| x        | number   |
| y        | number   |
| width    | number   |
| height   | number   |

## License

MIT © [gshudhanshu](https://github.com/gshudhanshu)
