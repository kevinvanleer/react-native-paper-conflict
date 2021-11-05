#react-native-paper bug report

This repository is intended to provide a minimal example of conflicts between `react-native-paper`, `@storybook/react-native`, and `@types/react-test-renderer`. The initial commit in the repository will compile and run, displaying the react-native-paper text and button components. The second commit will fail to compile displaying the following errors:

```
$ tsc --noEmit -p . --pretty --resolveJsonModule
App.tsx:78:12 - error TS2322: Type '{ children: string; }' is not assignable to type 'IntrinsicAttributes & PropsWithChildren<(Pick<Pick<any, "children" | "ref" | "style" | "pointerEvents" | "onLayout" | "testID" | "nativeID" | "accessible" | "accessibilityActions" | ... 45 more ... | "onTouchEndCapture"> & { ...; } & { ...; }, "children" | ... 65 more ... | "contentStyle"> & { ...; }) | (Pick<...> &...'.
  Type '{ children: string; }' is missing the following properties from type 'Pick<Pick<any, "children" | "ref" | "style" | "pointerEvents" | "onLayout" | "testID" | "nativeID" | "accessible" | "accessibilityActions" | "accessibilityLabel" | "accessibilityRole" | ... 43 more ... | "onTouchEndCapture"> & { ...; } & { ...; } & { ...; }, "children" | ... 65 more ... | "contentStyle">': ref, style, pointerEvents, onLayout, and 50 more.

78           <Button>KVL BUTTON</Button>
              ~~~~~~

App.tsx:79:12 - error TS2740: Type '{ children: string; }' is missing the following properties from type 'Pick<any, "ref" | "style" | "onLayout" | "testID" | "nativeID" | "accessible" | "accessibilityActions" | "accessibilityLabel" | "accessibilityRole" | "accessibilityState" | "accessibilityHint" | ... 28 more ... | "android_hyphenationFrequency">': ref, style, onLayout, testID, and 36 more.

79           <PaperText>KVL TEXT</PaperText>
              ~~~~~~~~~


Found 2 errors.

error Command failed with exit code 2.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
```

# Steps to reproduce:

1. Clone this repository
2. Run
```
./reset
```
3. Observe the failure
4. Run

```
git checkout HEAD~1
./reset
```
5. Observe that the app compiles successfully.
