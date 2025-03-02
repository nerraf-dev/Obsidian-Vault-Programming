### Main Entry Point
- **`lib/main.dart`**: The main entry point of the application. It initialises the app by calling `runApp` with the `MainApp` widget.

### Application Setup
- **`lib/home/main_app.dart`**: Contains the `MainApp` class, which sets up the `MultiProvider` for state management and defines the app's theme and home screen.

### Screens
- **`lib/home/screens/home_screen.dart`**: Contains the `HomeScreen` widget, which displays a welcome message and the active timer if it is running.
- **`lib/timer/screens/settings_screen.dart`**: Contains the `SettingsScreen` widget, which allows users to set the timer duration and presets.

### Timer Widgets
- **`lib/timer/widgets/countdown_timer.dart`**: Contains the `CountdownTimer` widget, which displays the timer, controls, and presets.
- **`lib/timer/widgets/timer_controls.dart`**: Contains the `TimerControls` widget, which provides buttons to start, stop, reset the timer, and open settings.
- **`lib/timer/widgets/timer_display.dart`**: Contains the `TimerDisplay` widget, which formats and displays the remaining time.
- **`lib/timer/widgets/timer_presets.dart`**: Contains the `TimerPresets` widget, which displays preset durations as buttons.

### State Management
- **`lib/timer/state/timer_state.dart`**: Manages the timer's state, including starting, stopping, and resetting the timer. It uses `ChangeNotifier` to notify listeners of state changes.

### Example Code Snippets
#### `main.dart`
```dart
import 'package:flutter/material.dart';
import 'home/main_app.dart';

void main() {
  runApp(const MainApp());
}
```

#### `main_app.dart`
```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';
import '../screens/main_screen.dart';
import '../state/app_state.dart';
import '../timer/state/timer_state.dart';

void main() {
  runApp(const MainApp());
}

class MainApp extends StatelessWidget {
  const MainApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MultiProvider(
      providers: [
        ChangeNotifierProvider(create: (context) => AppState()),
        ChangeNotifierProvider(create: (context) => TimerState()),
      ],
      child: MaterialApp(
        title: 'The Daily App',
        theme: ThemeData(
          useMaterial3: true,
          colorScheme: ColorScheme.fromSeed(
            seedColor: Color(0xFF000FDF),
          ),
        ),
        home: const MainScreen(),
      ),
    );
  }
}
```

#### 

countdown_timer.dart


```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';
import 'timer_controls.dart';
import 'timer_display.dart';
import 'timer_presets.dart';
import '../state/timer_state.dart';
import '../screens/settings_screen.dart';

class CountdownTimer extends StatefulWidget {
  const CountdownTimer({super.key});

  @override
  CountdownTimerState createState() => CountdownTimerState();
}

class CountdownTimerState extends State<CountdownTimer> {
  @override
  Widget build(BuildContext context) {
    final timerState = Provider.of<TimerState>(context);

    return Padding(
      padding: const EdgeInsets.all(16),
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        mainAxisSize: MainAxisSize.min,
        children: [
          // Timer
          Flexible(
            child: TimerDisplay(remaining: timerState.remaining),
          ),
          const SizedBox(height: 16),
          // Buttons
          TimerControls(
            isRunning: timerState.isRunning,
            startTimer: timerState.startTimer,
            stopTimer: timerState.stopTimer,
            resetTimer: timerState.resetTimer,
            openSettings: () async {
              final newPresets = await Navigator.push(
                context,
                MaterialPageRoute(
                  builder: (context) => SettingsScreen(
                    onDurationSelected: (newDuration) {
                      timerState.updateDuration(newDuration);
                    },
                    currentDuration: timerState.duration,
                    presets: timerState.presets,
                  ),
                ),
              );
              if (newPresets != null) {
                timerState.updatePresets(newPresets);
              }
            },
          ),
          const SizedBox(height: 16),
          // Presets
          TimerPresets(
            updateDuration: timerState.updateDuration,
            presets: timerState.presets,
          ),
          const SizedBox(height: 16),
          // Recents
          const Text(
            'Recent Timers',
            style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
          ),
        ],
      ),
    );
  }
}
```

