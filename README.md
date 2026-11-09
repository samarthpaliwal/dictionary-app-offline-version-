# Pocket Dictionary (offline version)

A small React Native app, built with Expo, that looks up a word in a hard-coded dictionary and shows its part of speech and definition. It needs no network connection: the ten entries it knows about live in a plain JavaScript object inside the project. It was created in Expo Snack and exported, which is why the project sits one folder down in `dictionary-app (offline-version)/`.

## Requirements

- Node.js and npm (or yarn)
- The Expo CLI, run through `npx expo`
- To test on a phone: the Expo Go app for iOS or Android. To test on a computer: a browser (the `web` script), or an iOS Simulator / Android emulator.

## Setup

```sh
cd "dictionary-app (offline-version)"
npm install
```

## Usage

```sh
npm start          # starts the Expo dev server and shows a QR code
npm run web        # opens the app in a browser
npm run android    # opens it in a connected Android device or emulator
npm run ios        # opens it in the iOS Simulator (macOS only)
```

Scan the QR code with Expo Go to run the app on a phone. In the app, type a word into the box and press Search. If the word is in the built-in list, the screen shows the word, its type (noun, adverb, and so on) and its definition. If it is not, an alert says the word is not available in the offline dictionary and the box is cleared.

Words currently in the dictionary: the, India, externally, hello, welcome, almost, she, tree, wonderful, ordinary. Lookup is case-insensitive.

## How it works

`App.js` renders a single `HomeScreen`. `screens/HomeScreen.js` keeps the typed text in component state; when Search is pressed it lower-cases the text and indexes into the `dictionary` object exported by `database.js`. Each entry has `word`, `lexicalCategory` and `definition` fields, which are copied into state and rendered. A missing key throws, which is caught and turned into the "not available" alert. The header comes from `react-native-elements`.

`components/AssetExample.js` is the unused sample component that Expo Snack generates. The `README.md` inside the nested folder is also the stock Snack text.

## Project layout

```
dictionary-app (offline-version)/
  App.js                 root component, renders HomeScreen
  database.js            the ten-word dictionary object
  screens/HomeScreen.js  search box, button and result display
  components/            Snack sample component (unused)
  assets/                icon, splash and favicon images
  app.json               Expo configuration
  package.json           Expo 51 / React Native 0.74 dependencies and scripts
  babel.config.js
```
