# flutter-deneme2
// ignore_for_file: prefer_const_constructors

import 'package:flutter/material.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(initialRoute: "/",
      routes: {"/": (context) => mainScreen(),
      },
      debugShowCheckedModeBanner: false,
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatelessWidget {
  TextEditingController t1 = TextEditingController();
  MyHomePage({Key? key}) : super(key: key);
  final String firstTitle = 'KahvApp';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(firstTitle),
        backgroundColor: Colors.brown,
      ),
      backgroundColor: Colors.brown,
      bottomNavigationBar: BottomAppBar(color: Colors.brown,child: Row(children: [Text('Don\'t have account?'),TextButton(onPressed: (){}, child: Text('Sing up'))],),),
      
      body: yapi(),
    );
  }
}

class yapi extends StatefulWidget {
  const yapi({Key? key}) : super(key: key);

  @override
  _yapiState createState() => _yapiState();
}

final String firstTitle = 'KahvApp';
TextEditingController t1 = TextEditingController();
TextEditingController t2 = TextEditingController();
bool isHiddenPassword =true;

//Giriş doğruluğu(database yok)


//Şifre görünürlüğü
void passwordToggleView(){
  if (isHiddenPassword==true) {isHiddenPassword=false;
    
  }else{isHiddenPassword = true;}
  
}



class _yapiState extends State<yapi> {
  @override
  Widget build(BuildContext context) {
    
      login() {
  final String email = 'mehmetensar@gmail.com';
  final String password = '123mehmet';
  if (t1.text == email && t2.text == password) {
    Navigator.pushNamed(context, "/");
    print('Giriş Yapıldı');
  } else {
    print('Yanlış Giriş');
  }
}return Center(
      child: Column(
        children: [
          //Cicrle avatar kahveapp yazısı
          Padding(padding: EdgeInsets.all(20)),
          CircleAvatar(
            backgroundColor: Colors.brown[900],
            child: Text(
              firstTitle,
              style: Theme.of(context)
                  .primaryTextTheme
                  .headline6!
                  .copyWith(color: Colors.white),
            ),
            radius: 60,
          ),
          Padding(padding: EdgeInsets.all(25)),
          //mail adres girişi
          Container(
            width: MediaQuery.of(context).size.width * 0.83,
            height: 36,
            child: TextField(
              controller: t1,
              maxLines: 1,
              style: TextStyle(fontSize: 17),
              textAlignVertical: TextAlignVertical.center,
              decoration: InputDecoration(
                filled: true,
                prefixIcon:
                    Icon(Icons.mail, color: Theme.of(context).iconTheme.color),
                border: OutlineInputBorder(
                    borderSide: BorderSide.none,
                    borderRadius: BorderRadius.all(Radius.circular(30))),
                fillColor: Theme.of(context).inputDecorationTheme.fillColor,
                contentPadding: EdgeInsets.zero,
                hintText: 'Email Adress',
              ),
            ),
          ),
          Padding(padding: EdgeInsets.all(15)),
          //şifre giriş bölümü
          Container(
            width: MediaQuery.of(context).size.width * 0.83,
            height: 36,
            child: TextField(
              controller: t2,
              maxLines: 1,
              obscureText: isHiddenPassword,onTap: (){passwordToggleView;},
              style: TextStyle(fontSize: 17),
              textAlignVertical: TextAlignVertical.center,
              decoration: InputDecoration(
                filled: true,
                prefixIcon: Icon(Icons.password,
                    color: Theme.of(context).iconTheme.color),
                border: OutlineInputBorder(
                    borderSide: BorderSide.none,
                    borderRadius: BorderRadius.all(Radius.circular(30))),
                fillColor: Theme.of(context).inputDecorationTheme.fillColor,
                contentPadding: EdgeInsets.zero,
                hintText: 'Password',
              ),
            ),
          ),
          Padding(padding: EdgeInsets.all(15)),
          //giriş yap butonu
          Container(
            width: MediaQuery.of(context).size.width * 0.83,
            child: ElevatedButton(
                onPressed: login,
                child: Text('Log in'),
                style: ButtonStyle(
                  backgroundColor: MaterialStateProperty.all(Colors.brown[400]),
                )),
          ),Padding(padding: EdgeInsets.all(20)),
          Text('__________ OR __________',style: TextStyle(fontSize:MediaQuery.of(context).size.width * 0.035,color: Colors.grey),),
          Padding(padding: EdgeInsets.all(15)),
          TextButton(onPressed: (){}, child: Text('Log in Google')),
        ],
      ),
    );
  }
}

class mainScreen extends StatefulWidget {
  const mainScreen({ Key? key }) : super(key: key);

  @override
  _mainScreenState createState() => _mainScreenState();
}

class _mainScreenState extends State<mainScreen> {
  @override
  Widget build(BuildContext context) {
    return Container(height: 100,width: 100,color: Colors.yellow,child: Center(child:Text('bas bas')),
      
    );
  }
}
