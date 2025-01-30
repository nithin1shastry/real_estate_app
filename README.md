## Project Setup
- npx create-expo-app@latest ./
- npx expo start

- app.json - newArchEnabled => allow bridgeless communication

- fabric for rendering, jsi for direct sync bw js and native code

- reset the project to scratch by following commands

- npm run reset-project

- npx expo start

## Setup Routes

![img.png](img.png)

- **plugin** - modern react snippets
- created sign-in.tsx file
- rnfe => react native functional comp with exports

```aiignore
const Property = () => {
    const { id } = useLocalSearchParams()

    return (
        <View>
            <Text>Property {id}</Text>
        </View>
    )
}
```
- created explore, tabs, profile, properties tabs


## Setup Nativewind
- Its a styling library

## Setup native wind
- go through official docs
- changes that I did are
```aiignore
tailwind.config.js file

//added  "./components/**/*.{js,jsx,ts,tsx}"
/** @type {import('tailwindcss').Config} */
module.exports = {
    // NOTE: Update this to include the paths to all of your component files.
    content: ["./app/**/*.{js,jsx,ts,tsx}", "./components/**/*.{js,jsx,ts,tsx}"],
    presets: [require("nativewind/preset")],
    theme: {
        extend: {},
    },
    plugins: [],
}

- In metro.config.js file
- changed module.exports { input: './app/globals.css' }
- imported import "./globals.css" in _layout.tsx for importing native wind into the application

```
## Setup fonts and assets
- added assets and constants folder
- added fonts to app.json
- in app.json changed expo flash screen props
- in _layout.tsx added fonts and if fonts are loaded hide splash screen logic
- tailwind.config.js
```aiignore
/** @type {import('tailwindcss').Config} */
module.exports = {
    // NOTE: Update this to include the paths to all of your component files.
    content: ["./app/**/*.{js,jsx,ts,tsx}", "./components/**/*.{js,jsx,ts,tsx}"],
    presets: [require("nativewind/preset")],
    theme: {
        extend: {
            fontFamily: {
                "rubik-bold": ["Rubik-Bold", "sans-serif"],
                "rubik-extrabold": ["Rubik-ExtraBold", "sans-serif"],
                "rubik-medium": ["Rubik-Medium", "sans-serif"],
                "rubik-semibold": ["Rubik-SemiBold", "sans-serif"],
                "rubik-light": ["Rubik-Light", "sans-serif"],
            }
        },
        colors:{
            "primary":{
                100: '#0061FF0A',
                200: '#0061FF0A',
                300: '#0061FF',
            },
            accent: {
                100: '#FBFBFD'
            },
            black: {
                DEFAULT: '#000000',
                100: '#8C8E98',
                200: '#666876',
                300: '#191d31',
            },
            danger: '#F75555'
        }
    },
    plugins: [],
}
```
> issue with loading fonts due to mismatched path
- Changed fonts path accordingly

> TS2307: Cannot find module @/ assets/ icons/ star. png or its corresponding type declarations.
- Steps to fix
- create image.t.ds
- declared types for all file formats

## Sign in page
> Remove (root)/(tabs)/index from screen
- in _layout.tsx 
- return <Stack screenOptions={{headerShown: false}}/>;
- **SafeAreaView** - Ensures that all texts abides within the border of the screen
- 
