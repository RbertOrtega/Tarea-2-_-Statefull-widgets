import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Calculadora',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'Operaciones Aritméticas'),
      debugShowCheckedModeBanner: false,
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key? key, required this.title}) : super(key: key);

  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  final _formKey = GlobalKey<FormState>();
  TextEditingController _primerValorController = TextEditingController();
  TextEditingController _segundoValorController = TextEditingController();
  String _resultado = '';
  String? _operacion;

  void _calcular() {
    if (_formKey.currentState!.validate() && _operacion != null) {
      double primerValor = double.parse(_primerValorController.text);
      double segundoValor = double.parse(_segundoValorController.text);

      switch (_operacion) {
        case 'Suma':
          _resultado = (primerValor + segundoValor).toStringAsFixed(0);
          break;
        case 'Resta':
          _resultado = (primerValor - segundoValor).toStringAsFixed(0);
          break;
        case 'Multiplicacion':
          _resultado = (primerValor * segundoValor).toStringAsFixed(0);
          break;
        case 'Division':
          if (segundoValor == 0) {
            _resultado = 'No se puede dividir entre 0';
          } else {
            _resultado = (primerValor / segundoValor).toString();
          }
          break;
      }
      setState(() {});
    } else {
      setState(() {
        _resultado = 'Seleccione una operación';
      });
    }
  }

  // **Función para limpiar los campos y el resultado**
  void _limpiar() {
    _primerValorController.clear();
    _segundoValorController.clear();
    _operacion = null;
    _resultado = '';
    setState(() {});
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          widget.title,
          style: TextStyle(
            color: Colors.white,
            fontWeight: FontWeight.bold,
          ),
        ),
        backgroundColor: Colors.blue,
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Form(
          key: _formKey,
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.stretch,
            children: <Widget>[
              TextFormField(
                controller: _primerValorController,
                decoration: InputDecoration(
                  labelText: 'Primer Valor',
                  border: OutlineInputBorder(),
                ),
                keyboardType: TextInputType.number,
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return 'Por favor ingrese el primer valor';
                  }
                  return null;
                },
              ),
              SizedBox(height: 16),
              TextFormField(
                controller: _segundoValorController,
                decoration: InputDecoration(
                  labelText: 'Segundo Valor',
                  border: OutlineInputBorder(),
                ),
                keyboardType: TextInputType.number,
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return 'Por favor ingrese el segundo valor';
                  }
                  return null;
                },
              ),
              SizedBox(height: 16),
              InputDecorator(
                decoration: InputDecoration(
                  labelText: 'Operación',
                  border: OutlineInputBorder(),
                ),
                child: DropdownButtonHideUnderline(
                  child: DropdownButton<String>(
                    value: _operacion,
                    hint: Text('Seleccione una operación'),
                    items: <String>[
                      'Suma',
                      'Resta',
                      'Multiplicacion',
                      'Division'
                    ].map<DropdownMenuItem<String>>((String value) {
                      return DropdownMenuItem<String>(
                        value: value,
                        child: Text(value),
                      );
                    }).toList(),
                    onChanged: (String? newValue) {
                      setState(() {
                        _operacion = newValue;
                      });
                    },
                  ),
                ),
              ),
              SizedBox(height: 16),
              ElevatedButton(
                onPressed: _calcular,
                child: Text('Calcular'),
              ),
              SizedBox(height: 16),
              // **Botón para limpiar**
              ElevatedButton(
                onPressed: _limpiar,
                child: Text('Limpiar'),
              ),
              SizedBox(height: 16),
              Text('Resultado: $_resultado', style: TextStyle(fontSize: 20)),
            ],
          ),
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _calcular,
        tooltip: 'Calcular',
        child: Icon(Icons.play_arrow),
      ),
    );
  }
}