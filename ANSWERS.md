# Checkpoint answers

## 1. Why do we write `onPress={handlePress}` and not `onPress={handlePress()}`?

`onPress={handlePress}` passes the function to React Native so it can call it when the press happens. `onPress={handlePress()}` calls the function immediately during rendering and passes its return value instead of a handler.

## 2. What is the difference between `Button` and `Pressable`? When would you choose each one?

`Button` is a simple, ready-made control with limited styling and behavior options. `Pressable` is more flexible, so I would use it for custom layouts, styles, and pressed-state feedback, while choosing `Button` for a quick standard action.

## 3. What does the `style` function of `Pressable` receive and what does it return?

The style function receives an object containing interaction state, including `pressed`, and returns a style object or an array of styles. For example, `style={({ pressed }) => [styles.button, pressed && styles.pressed]}` changes the opacity while the button is pressed.

## 4. Why can you not change a state variable directly?

Direct assignment such as `isFollowing = true` does not notify React and is not a valid way to update component state. We call the setter returned by `useState`, such as `setIsFollowing(true)`, so React stores the value and re-renders the component.

## 5. Why is `followers` not a second `useState`?

`followers` is a derived value because it can always be calculated from the base count and `isFollowing`. Keeping it as a second state could create duplicated data that becomes inconsistent.

## 6. What does controlled input mean for `TextInput`?

A controlled input gets its current value from React state and reports edits through a callback that updates that state. The two props are `value` and `onChangeText`.

## 7. Why is `selectedSkills.push(skill)` wrong when `selectedSkills` is state?

`push` mutates the existing state array and React may not detect that the state changed. The correct approach creates a new array, such as `setSelectedSkills([...selectedSkills, skill])`, or uses the functional setter to add and remove items without mutation.
