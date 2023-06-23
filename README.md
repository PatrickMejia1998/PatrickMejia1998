- 👋 Hi, I’m @PatrickMejia1998
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- import 'package:flutter/material.dart';
import 'dart:async';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Cambiador de Fondos de Pantalla',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: HomePage(),
    );
  }
}

class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  int _currentIndex = 0;
  List<String> _imagePaths = [
    'assets/imagen1.jpg',
    'assets/imagen2.jpg',
    'assets/imagen3.jpg',
  ];
  List<int> _times = [10, 15, 20];
  Timer _timer;

  @override
  void initState() {
    super.initState();
    _startTimer();
  }

  @override
  void dispose() {
    _stopTimer();
    super.dispose();
  }

  void _startTimer() {
    _timer = Timer.periodic(Duration(seconds: _times[_currentIndex]), (_) {
      setState(() {
        _currentIndex = (_currentIndex + 1) % _imagePaths.length;
      });
    });
  }

  void _stopTimer() {
    _timer?.cancel();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Cambiador de Fondos de Pantalla'),
      ),
      body: Center(
        child: Container(
          decoration: BoxDecoration(
            image: DecorationImage(
              image: AssetImage(_imagePaths[_currentIndex]),
              fit: BoxFit.cover,
            ),
          ),
        ),
      ),
    );
  }
}


<!---
PatrickMejia1998/PatrickMejia1998 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
