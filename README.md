# Alt.Point Components
## How install 
### Pub Dev

In the `pubspec.yaml` of your flutter project, add the following dependency:

```yaml
dependencies:
  alt_point_components: <latest_version>
```


or add dependency via terminal: 

```flutter pub add alt_point_components```

This will add a line like this to your package's pubspec.yaml (and run an implicit flutter pub get):

```yaml
dependencies:
  alt_point_components: <latest version>
  ```
Alternatively, your editor might support flutter pub get. Check the docs for your editor to learn more.

### From AltGit
 
Since the repository is closed, you should do the following

1. run pubspec.yaml
2. paste the following piece of code 
``` Dart
  dependencies:
    alt_point_components:
      git:
        url: https://github.com/vinnikpuhh/alt_point_components.git

```
3. run pub get 

### Import it

In your library add the following import:

```dart
import 'package:alt_point_components/alt_point_components.dart';
```
___

## Example

``` dart
import 'package:flutter/material.dart';
import 'package:alt_point_components/alt_point_components.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      home: App(),
    );
  }
}

class App extends StatelessWidget {
  const App({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            crossAxisAlignment: CrossAxisAlignment.center,
            children: [
              buttonWithBS(
                context,
                'Open bottomsheet switch',
                Center(
                  child: AppSwitch(
                    isActive: true,
                    onToggled: (bool active) {},
                  ),
                ),
              ),
              buttonWithBS(
                context,
                'Open bottomsheet pattern lock',
                PatternLock(width: 3, height: 3, onEntered: (_) {}),
              ),
              buttonWithBS(
                context,
                'Open bottomsheet scrolable calendar',
                CalendarRangePickerDialog(
                  firstDate: DateTime(
                    2020,
                    1,
                    1,
                  ),
                  lastDate: DateTime.now(),
                  onEndDateChanged: (DateTime? date) {
                    /*   setState(() => endDay = date); */
                  },
                  onStartDateChanged: (DateTime? date) {
                    /* setState(() => startDay = date); */
                  },
                  confirmText: '',
                  currentDate: null,
                  helpText: '',
                  onCancel: () {},
                  onConfirm: () {},
                  selectedEndDate: null,
                  selectedStartDate: null,
                  size: MediaQuery.of(context).size,
                  rangeDateTextStyle: const TextStyle(),
                  titleTextStyle: const TextStyle(),
                ),
              ),
              buttonWithBS(
                context,
                'Open bottomsheet loading buttons',
                Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                      LoaderButton(
                        onPressed: () {},
                        type: ButtonType.elevated,
                        loading: true,
                        child: const Text("Loading"),
                      ),
                      LoaderButton(
                        onPressed: () {},
                        type: ButtonType.elevated,
                        loading: false,
                        child: const Text("No Loading"),
                      ),
                    ],
                  ),
                ),
              ),
              buttonWithBS(
                context,
                'Open bottomsheet square buttons',
                Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                      SquareButton.color(
                        borderRadius: 10.0,
                        color: Colors.green,
                        onPressed: () {},
                        child: const Icon(Icons.add),
                      ),
                      const SizedBox(
                        height: 10.0,
                      ),
                      SquareButton.customDecoration(
                        decoration: BoxDecoration(
                            color: Colors.amber,
                            border: Border.all(color: Colors.black)),
                        onPressed: () {},
                        child: const Icon(Icons.add),
                      ),
                      const SizedBox(
                        height: 10.0,
                      ),
                      SquareButton.gradient(
                        gradient: const LinearGradient(
                          colors: [Colors.green, Colors.blue],
                        ),
                        onPressed: () {},
                        borderRadius: 8.0,
                        border: Border.all(color: Colors.purple),
                        child: const Icon(Icons.add),
                      ),
                    ],
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }

  Widget buttonWithBS(BuildContext context, String title, Widget child) {
    return ElevatedButton(
      onPressed: () => openBS(
        paddingBS: 0,
        context: context,
        height: MediaQuery.of(context).size.height,
        heightBS: MediaQuery.of(context).size.height * 0.9,
        width: MediaQuery.of(context).size.width,
        child: child,
      ),
      child: Text(title),
    );
  }
}
```
----
## Square Button

### This class has the following constructors

- color
- gradient
- customDecoration

#### Color constructor
``` dart

SquareButton.color(
  borderRadius: 10.0,                   
  color: Colors.green,                  
  onPressed: () {},                 
  size: 40.0,                   
  border: Border.all(),                 
  child: const Icon(Icons.add),                 
),
```

#### Gradient constructor
``` dart

SquareButton.gradient(
  gradient: const LinearGradient(
    colors: [Colors.green, Colors.blue],
  ),
  onPressed: () {},
  borderRadius: 8.0,
  size: 40.0,
  border: Border.all(color: Colors.purple),
  child: const Icon(Icons.add),
),
```

#### CustomDecoration constructor
``` dart

SquareButton.customDecoration(
  decoration: BoxDecoration(
      color: Colors.amber,
      border: Border.all(color: Colors.black)),
  onPressed: () {},
  child: const Icon(Icons.add),
),
```