# provider counter

```dart
class Counter with ChangeNotifier {
  int _count;
  int get count => _count;

  Counter(this._count);

  void increment() {
    _count++;
    notifyListeners();
  }

  void decrement() {
    _count--;
    notifyListeners();
  }
}

void main() {
  runApp(MultiProvider(
      providers: [ChangeNotifierProvider(create: (context) => Counter(0))],
      child: CounterApp()));
}

class CounterApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final counter = Provider.of<Counter>(context);

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text("CounterApp")),
        body: Center(child: Text(counter.count.toString())),
        floatingActionButton: FloatingActionButton(
          onPressed: () => counter.increment(),
          child: Icon(Icons.add),
        ),
      ),
    );
  }
}
```
