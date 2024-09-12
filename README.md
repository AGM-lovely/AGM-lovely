import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'TOKO VERONICA',
      theme: ThemeData(
        primarySwatch: Colors.green,
      ),
      home: const MainPage(title: 'TOKO VERONICA'),
      debugShowCheckedModeBanner: false,
    );
  }
}

class MainPage extends StatefulWidget {
  const MainPage({required this.title, super.key});

  final String title;

  @override
  State<MainPage> createState() => _MainPageState();
}

class _MainPageState extends State<MainPage> {

  final data = Product(
    'AQUA BOTOL BESAR',
    '100.000',
    'KOTAK',
    'images/aquabesarkotak.jpeg',
    'AQUA BERASAL DARI PEGUNUNGAN'
  );

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        elevation: 1,
        backgroundColor: Colors.white,
        leading: const Icon(
          Icons.menu,
          color: Colors.black,
        ),
        title: Text(
          widget.title, // Use widget.title to access the title property
          style: const TextStyle(color: Colors.black),
        ),
        actions: [
          Row(
            children: [
              const Icon(
                Icons.search,
                color: Colors.black,
              ),
              Stack(
                children: [
                  IconButton(
                    onPressed: (() {}),
                    icon: const Icon(
                      Icons.shopping_cart,
                      color: Colors.black,
                    ),
                  ),
                Positioned(
                  top: 0,
                  right: 3,
                  child: Container(
                    height: 20,
                    width: 20,
                    decoration: const BoxDecoration(
                      shape: BoxShape.circle,
                      color: Colors.orange,
                    ),
                  child: const Center(
                    child: Text(
                      "7"
                        style: TextStyle(
                        color: Colors.white,
                        fontWeight: FontWeight.w700,
                      ),
                    )
                  )
                  )
                )
                ]
              )
            ],
          ),
        ],
      ),
    body: Container(
      padding: const EdgeInsets.all(10),
      child: GridView.count(
        mainAxisSpacing: 10,
        crossAxisSpacing: 3,
      crossAxisCount: 3,
      childAspectRatio: 0.6,
      children: [
        Card(
          elevation: 3,
          shadowColor: Colors.blue,
          shape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(20),
          ),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Hero(
              tag: data.image,
              child: SizedBox(
                width: 130,
                child: Image.asset(data.image),
              ),
            ),
          const SizedBox(
            height: 7,
          ),
          Text(
            '${data.price}',
            style: const TextStyle(
              color: Colors.blue,
              fontSize: 20,
              fontWeight: FontWeight.w500,
            ),
          ),
          const SizedBox(
            height: 3,
          ),
          Text(
            data.name,
            style: const TextStyle(
              fontSize: 20,
              fontWeight: FontWeight.w500, 
            ),
          ),
          const SizedBox(
            height: 3,
          ),
          Text(
            data.quantity,
            style: const TextStyle(
              fontSize: 20,
              fontWeight: FontWeight.w300,
            )
          ),
          const SizedBox(
            height: 5,
          ),
          const Divider(
            height: 3,
            color: Colors.grey,
          ),
          const SizedBox(
            height: 10,
          )
          Row(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              Row(
                children: const [
                  Icon(
                    Icons.add_shopping_cart,
                    size: 20,
                    color: Colors.blue,
                  )
                SizedBox(
                  width: 3,
                )
                Text(
                  "BUY"
                  style: TextStyle(
                    color: Colors.blue,
                    fontSize: 17,
                  )
                )
                ]
              )
            const SizedBox(
              width: 7,
            )
            Row(
              children: const [
                Icon(
                  Icons.remove_circle_outline,
                  size: 17,
                  color: Colors.blue,
                ),
                Padding(
                  padding: EdgeInsets.symetric(horizontal: 5),
                  child: Text("0"),
                ),
                Icon(
                  Icons.add_circle_outline,
                  size: 17,
                  color: Colors.blue,
                )
                ),
                )
              ]
            )
            ],
          )
          ],
        ),
        ),
      ]
      )
    )
    )
  }
}
