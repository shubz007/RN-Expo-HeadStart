# RN-Expo-HeadStart
This guide walks you through setting up an **Expo** project with **NativeWind (Tailwind CSS for React Native)** along with essential configurations.

---

## 🚀 **1. Install Expo CLI**
Ensure you have **Node.js** installed:
```sh
node -v
```
If not installed, download it from [nodejs.org](https://nodejs.org/).

Then install the Expo CLI globally:
```sh
npm install -g expo-cli
```

---

## 📂 **2. Create a New Expo Project**
Run the following command to create a new Expo project:
```sh
npx create-expo-app MyApp
```
Navigate into the project directory:
```sh
cd MyApp
```

---

## 📦 **3. Install Dependencies**

### **(i) Install NativeWind (Tailwind CSS)**
```sh
npm install nativewind tailwindcss
```

### **(ii) Install React Native Vector Icons**
```sh
npm install react-native-vector-icons
```

### **(iii) Install Expo Router (Optional)**
For navigation:
```sh
npm install expo-router
```
Then wrap your app with `<ExpoRouter />` in `App.js`.

---

## ⚙️ **4. Configure TailwindCSS**
Initialize Tailwind configuration:
```sh
npx tailwindcss init
```
This will create a `tailwind.config.js` file. Modify it as follows:
```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./App.{js,jsx,ts,tsx}", "./components/**/*.{js,jsx,ts,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

---

## 🔧 **5. Configure Babel for NativeWind**
Modify `babel.config.js` to enable `nativewind` plugin:
```js
module.exports = function (api) {
  api.cache(true);
  return {
    presets: ["babel-preset-expo"],
    plugins: ["nativewind/babel"],
  };
};
```

---

## 🎨 **6. Use Tailwind Classes in Components**
Example usage in `App.js`:
```js
import { View, Text } from "react-native";

export default function App() {
  return (
    <View className="flex-1 justify-center items-center bg-blue-500">
      <Text className="text-white text-lg font-bold">Hello, Expo + NativeWind!</Text>
    </View>
  );
}
```

---

## ▶️ **7. Run the Project**
To start the project:
```sh
npm start
```
or
```sh
expo start
```
This will open Expo Developer Tools in the browser, allowing you to scan the QR code with your mobile device.

---

## 📝 **8. Additional Configurations**

### **(i) Using Custom Fonts**
1. Install Fonts:
```sh
npx expo install expo-font
```
2. Load Fonts in `App.js`:
```js
import { useFonts } from 'expo-font';
import { Text } from 'react-native';

export default function App() {
  const [fontsLoaded] = useFonts({
    'Poppins-Regular': require('./assets/fonts/Poppins-Regular.ttf'),
  });

  if (!fontsLoaded) return null;

  return <Text style={{ fontFamily: 'Poppins-Regular' }}>Custom Font</Text>;
}
```

### **(ii) Adding Icons**
Use `react-native-vector-icons`:
```js
import { View } from "react-native";
import { MaterialIcons } from '@expo/vector-icons';

export default function App() {
  return (
    <View>
      <MaterialIcons name="home" size={32} color="black" />
    </View>
  );
}
```

### **(iii) Configuring Environment Variables**
Install `expo-constants`:
```sh
npm install expo-constants
```
Use in your project:
```js
import Constants from 'expo-constants';
console.log(Constants.expoConfig.extra.API_KEY);
```

---

## 🎉 **You're All Set!**
Now you have an Expo project configured with NativeWind and other essential features! 🚀

