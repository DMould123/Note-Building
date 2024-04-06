# React Native Basics 📱

React Native is a framework for building mobile applications using JavaScript and React. It allows developers to create mobile apps for both iOS and Android platforms using a single codebase.

## App Structure 📄

A basic React Native app structure includes:

```
import { View, Text } from 'react-native';

const App = () => {
  return (
    <View>
      <Text>Hello, React Native!</Text>
    </View>
  );
};

export default App;
```

- `import { View, Text } from 'react-native'`: Imports components from React Native for building the user interface.
- `const App = () => { ... }`: Defines the main component of the app..
- `<View>`: Acts as a container for other components, similar to <div> in HTML.
- `<Text>`: Renders text, similar to <p> in HTML.

## React Native Components 🧩

React Native components are similar to HTML elements but are specifically designed for mobile development. Some commonly used components include:

- `<View>`: Container for other components, used for layout purposes.
- `<Text>`: Renders text.
- `<Image>`: Displays images.
- `<TextInput>`: Allows users to input text.
- ´<ScrollView>´: Provides scrolling functionality for content that exceeds the screen size.
- `<TouchableOpacity>`: Creates a touchable area that responds to user taps.

### Styling 🎨

Styling in React Native is done using JavaScript objects instead of CSS. Properties like flex, margin, padding, etc., are used to style components.

```
<View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
  <Text style={{ fontSize: 20, fontWeight: 'bold' }}>Styled Text</Text>
</View>
```

### Comments 💬

Just like in HTML, comments in React Native can be used to provide notes to developers and are ignored during app execution.

Example:

```
{/* This is a comment */}
```

React Native provides a powerful and flexible way to build mobile applications using familiar JavaScript and React concepts.
