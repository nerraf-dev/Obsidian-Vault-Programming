### Overview of the Project

This project is a Flutter application named `timer_app`. It is designed to help users manage and track time using a countdown timer. The app includes features such as setting a timer, starting, stopping, and resetting the timer, and using preset durations for quick timer setup. The app also ensures that the timer continues running even when the user navigates to other screens.

### Key Concepts in Flutter

1. **Widgets**: In Flutter, everything is a widget. Widgets describe what their view should look like given their current configuration and state. Widgets are the building blocks of a Flutter app's user interface.

2. **State Management**: Managing the state of an application is crucial. This project uses the `Provider` package for state management, which allows different parts of the app to listen to changes in the state and update the UI accordingly.

3. **Navigation**: Flutter provides a way to navigate between different screens using the `Navigator` class. This project uses navigation to move between the main screen and the settings screen.

### Key Components of the Project

1. **Main Entry Point (`main.dart`)**:
   - This is the entry point of the application. It initialises the app by calling `runApp` with the `MainApp` widget.

   ```dart
   import 'package:flutter/material.dart';
   import 'home/main_app.dart';

   void main() {
     runApp(const MainApp());
   }
   ```

2. **Main Application Setup (`main_app.dart`)**:
   - This file contains the `MainApp` class, which sets up the `MultiProvider` for state management and defines the app's theme and home screen.

   ```dart
   import 'package:flutter/material.dart';
   import 'package:provider/provider.dart';
   import '../screens/main_screen.dart';
   import '../state/app_state.dart';
   import '../timer/state/timer_state.dart';

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

3. **Home Screen (`home_screen.dart`)**:
   - This file contains the `HomeScreen` widget, which displays a welcome message and the active timer if it is running.

   ```dart
   import 'package:flutter/material.dart';
   import 'package:provider/provider.dart';
   import '../../timer/state/timer_state.dart';
   import '../../timer/widgets/timer_display.dart';

   class HomeScreen extends StatelessWidget {
     const HomeScreen({super.key});

     @override
     Widget build(BuildContext context) {
       return Center(
         child: Consumer<TimerState>(
           builder: (context, timerState, child) {
             return Column(
               mainAxisAlignment: MainAxisAlignment.center,
               children: [
                 const Text('Welcome to The Daily App!'),
                 const Text('This is the home screen.'),
                 if (timerState.isRunning) ...[
                   const SizedBox(height: 16),
                   const Text(
                     'Active Timer:',
                     style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
                   ),
                   TimerDisplay(
                     remaining: timerState.remaining,
                     textStyle: const TextStyle(
                       fontFamily: 'WorkbenchScan',
                       fontSize: 48, // Smaller font size for home screen
                     ),
                   ),
                 ],
               ],
             );
           },
         ),
       );
     }
   }
   ```

4. **Countdown Timer (`countdown_timer.dart`)**:
   - This file contains the `CountdownTimer` widget, which displays the timer, controls, and presets.

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

5. **Timer Controls (`timer_controls.dart`)**:
   - This file contains the `TimerControls` widget, which provides buttons to start, stop, reset the timer, and open settings.

   ```dart
   import 'package:flutter/material.dart';

   class TimerControls extends StatelessWidget {
     final bool isRunning;
     final VoidCallback startTimer;
     final VoidCallback stopTimer;
     final VoidCallback resetTimer;
     final VoidCallback openSettings;

     const TimerControls({
       super.key,
       required this.isRunning,
       required this.startTimer,
       required this.stopTimer,
       required this.resetTimer,
       required this.openSettings,
     });

     @override
     Widget build(BuildContext context) {
       return ConstrainedBox(
         constraints: BoxConstraints(maxWidth: 400),
         child: Row(
           mainAxisAlignment: MainAxisAlignment.spaceEvenly,
           children: [
             Column(
               children: [
                 ElevatedButton(
                   onPressed: isRunning ? stopTimer : startTimer,
                   child: Icon(isRunning ? Icons.pause : Icons.play_arrow),
                 ),
                 Text(
                   isRunning ? 'Pause' : 'Run',
                   style: TextStyle(fontSize: 10),
                 ),
               ],
             ),
             Column(
               children: [
                 ElevatedButton(
                   onPressed: resetTimer,
                   child: Icon(Icons.replay),
                 ),
                 const Text(
                   'Reset',
                   style: TextStyle(fontSize: 10),
                 ),
               ],
             ),
             Column(
               children: [
                 ElevatedButton(
                   onPressed: openSettings,
                   child: const Icon(Icons.settings),
                 ),
                 const Text(
                   'Settings',
                   style: TextStyle(fontSize: 10),
                 ),
               ],
             ),
           ],
         ),
       );
     }
   }
   ```

6. **Timer Display (`timer_display.dart`)**:
   - This file contains the `TimerDisplay` widget, which formats and displays the remaining time.

   ```dart
   import 'package:flutter/material.dart';

   class TimerDisplay extends StatelessWidget {
     final Duration remaining;
     final TextStyle? textStyle;

     const TimerDisplay({super.key, required this.remaining, this.textStyle});

     String formatDuration(Duration duration) {
       String twoDigits(int n) => n.toString().padLeft(2, '0');
       final hours = twoDigits(duration.inHours);
       final minutes = twoDigits(duration.inMinutes.remainder(60));
       final seconds = twoDigits(duration.inSeconds.remainder(60));
       return '$hours:$minutes:$seconds';
     }

     @override
     Widget build(BuildContext context) {
       return Center(
         child: Text(
           formatDuration(remaining),
           style: textStyle ?? const TextStyle(
             fontFamily: 'WorkbenchScan',
             fontSize: 92,
           ),
         ),
       );
     }
   }
   ```

7. **Timer Presets (`timer_presets.dart`)**:
   - This file contains the `TimerPresets` widget, which displays preset durations as buttons.

   ```dart
   import 'package:flutter/material.dart';

   class TimerPresets extends StatelessWidget {
     final Function(Duration) updateDuration;
     final List<Duration> presets;

     const TimerPresets({
       super.key, 
       required this.updateDuration, 
       required this.presets
       });

     @override
     Widget build(BuildContext context) {
       return Row(
         mainAxisAlignment: MainAxisAlignment.spaceEvenly,
         children: presets.map((preset) {
           return ElevatedButton(
             onPressed: () {
               updateDuration(preset);
             },
             child: Text('${preset.inMinutes} minutes'),
           );
         }).toList(),
       );
     }
   }
   ```

8. **Timer State (`timer_state.dart`)**:
   - This file manages the timer's state, including starting, stopping, and resetting the timer. It uses `ChangeNotifier` to notify listeners of state changes.

   ```dart
   import 'dart:async';
   import 'package:flutter/material.dart';

   class TimerState extends ChangeNotifier {
     Duration duration = const Duration(minutes: 50);
     Duration remaining = const Duration(minutes: 50);
     bool isRunning = false;

     Timer? timer; // Initialize as null

     void startTimer() {
       isRunning = true;
       timer = Timer.periodic(const Duration(seconds: 1), (timer) {
         if (remaining.inSeconds > 0) {
           remaining -= const Duration(seconds: 1);
           notifyListeners();
         } else {
           timer.cancel();
           isRunning = false;
           notifyListeners();
           // Trigger Alarm
           // playAlarm(); for example
         }
       });
       notifyListeners();
     }

     void stopTimer() {
       isRunning = false;
       timer?.cancel(); // Check for null
       notifyListeners();
     }

     void resetTimer() {
       remaining = duration;
       isRunning = false;
       timer?.cancel(); // Check for null
       notifyListeners();
     }

     void updateDuration(Duration newDuration) {
       duration = newDuration;
       remaining = duration;
       notifyListeners();
     }

     void updatePresets(List<Duration> newPresets) {
       presets = newPresets;
       notifyListeners();
     }

     List<Duration> presets = [
       const Duration(minutes: 90),
       const Duration(minutes: 50),
       const Duration(minutes: 25),
     ];
   }
   ```

### Summary

This project demonstrates how to build a Flutter application with a countdown timer feature. It uses `Provider` for state management, allowing the timer state to be shared across different screens. The app includes a home screen, a countdown timer screen, and a settings screen for configuring the timer duration and presets. The project showcases key Flutter concepts such as widgets, state management, and navigation.
