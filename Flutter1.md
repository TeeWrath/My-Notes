# **Flutter**
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/f7619736-a13d-4c2d-b623-4edc8b271927.png)
Flutter is of two main parts - firstly it is a UI framework to build beautiful mobile interfaces and secondly then flutter converts this single codebase into machine code that can be run on different platforms making flutter cross platform suitable.

### **Target Platforms**
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/391bb574-0f4d-4db6-bc97-ba9c30aee9cb.png)

## **Compilation**
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/326ca0ba-4dbb-4a89-a104-f0241242e6f7.png)
First the code is parsed from top to bottom then it is converted by dart and flutter tools to convert to a language that is understandable by the machines where app must be run.

## **Positional and Named Arguements in Function**
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/0f6a80c8-b774-49bb-835d-19b753e4fa7d.png)
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/498d1135-7aeb-4973-8bbf-c6485c433ec7.png)
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/357139f6-b478-4012-8854-169253f161ef.png)



## **'c****onst'  Keyword**
const keyword helps in making our applications memory efficient.
When we run our apps, our widgets are stored in the memory devices during runtime, by adding const, the same instance saved in memory device is used again and again as and when we re-run our application thus saving memory.
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/2b29630d-2833-488c-a0f1-900fe56987ba.png)



### **Data Types in Dart**
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/f58aefa8-9e16-4296-8cd0-3330bc1918dc.png)
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/405dc77d-cc49-40d1-8eb3-46ad2579b8d5.png)
### **Variables**
They are data containers
declared using ' **var** ' keyword
```dart
// Type inference
var num = 25;
var startAlignment = Alignment.topleft ;

// Explicit Type inference
Alignment startAlignment = Alignment.topleft ;
```
Do not use const for the variables as variables can be changed, so it is not wise for flutter to keep them const and store in memory.
Using var keyword, dart does implicit type detection.
To explicitly infer the type of variable, use the name of type of the variable where you declare it.

### **Difference between var, const and final keyword**
check out this **[article](https://www.funwithflutter.dev/flutter-dart-when-to-use-var-final-const-static/)** lays out clear difference :)
### **Reusable Configurable Widgets**
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/baaf8f41-bbf4-441a-9490-099ff714bebf.png)
In the above widget, we can see that altho the StyledText Widget is reusable, it will give us the same hardcoded text - Hello world. But in reality, widgets should be customisable, hence we make it such that it accepts value when we call this widget and pass the text that we want to see but the style should be constant.
Following is a way of doing that :
### **Using Positional Argument**
```dart
//  STYLED TEXT WIDGET
import 'package:flutter/material.dart';

class StyledText extends StatelessWidget {
  // Enter a positional arguement in the widget constructor
  const StyledText(this.text, {super.key});
  // Create a variable with the same name (bcuz we used this.text, so it will look for variable named text)
  final String text;

  @override
  Widget build(BuildContext context) {
    return Center(
      // use the variable in the widget tree
      child: Text(text, style: const TextStyle(color: Colors.white, fontSize: 58)),
    );
  }
}
```
 What we have done above is declared a positional argument by `this.text` which will look for variable named `text` in the whole class and assign its value to that, later it is used at its place.
Also we have declared text as `final` because we don't know its value at compile time but it will be surely known during runtime. PS, we haven't changed value of text hence it is final.
```dart
// Widget where the above widget is used
import 'package:flutter/material.dart';
import 'styled_text.dart';

const startAlignment = Alignment.bottomRight;
const endAlignment = Alignment.topLeft;

class GradientContainer extends StatelessWidget {
  const GradientContainer({super.key});

  @override
  Widget build(context) {
    return Container(
      decoration: const BoxDecoration(
        gradient: LinearGradient(
          colors: [Colors.deepPurple, Colors.black],
          begin: startAlignment,
          end: endAlignment,
        ),
      ),
      // Use the variable where u want to
      child: const StyledText('Subroto'),
    );
  }
}
```
above we have simply passed the text that we want the widget to display on our UI as a positional argument and on reloading it will be displayed.
### **Using Named Arguement**
```dart
import 'package:flutter/material.dart';
import 'styled_text.dart';

const startAlignment = Alignment.bottomRight;
const endAlignment = Alignment.topLeft;

class GradientContainer extends StatelessWidget {
  // Passing named arguement
  const GradientContainer({super.key, required this.colorList});
//  Initiating variables for the named arguements
  final List<Color> colorList;

  @override
  Widget build(context) {
    return Container(
      decoration: BoxDecoration(
        gradient: LinearGradient(
// Use the variables now
          colors: colorList,
          begin: startAlignment,
          end: endAlignment,
        ),
      ),
      // Use the variable where u want to
      child: const StyledText('Github'),
    );
  }
}
```

### **Column and Row widget**
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/2e3d1bdb-85fa-4fab-acd4-e0f01b592560.png)
### **Buttons**
There are following three types of buttons :
1. Floating Button
1. Eleviated Button
1. Text Button

### **Adding space between two child widgets**
Two ways :
1. By adding padding : 
```dart
padding: const EdgeInsets.only(top: 20),
```
2. Using SizedBox() widget
  
```dart
 const SizedBox(height: 20,),
```

## **Statefulwidget**
Those widgets where data inside the widget changes internally, is stateful widget.
```dart
import 'package:flutter/material.dart';

// Declaration of widget
class DiceRoller extends StatefulWidget {
  const DiceRoller({super.key});
   
   // function which helps  in  playing with the state of the widget
  @override
  State<DiceRoller> createState() => _DiceRollerState();
}

// State function, where you put the widget tree to be displayed by the widget
class _DiceRollerState extends State<DiceRoller> {

    // Declaring state
    var activeDiceRoller = 'assets/dice-1.png';

    void rollDice() {
       // this function helps in actually rebuilding the UI of the widget when the state is changed.
      setState(() {
      activeDiceRoller = 'assets/dice-2.png';
    });
  }
  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisSize: MainAxisSize.min,
      children: [
        Image.asset(
          activeDiceRoller,
          width: 200,
        ),
        const SizedBox(
          height: 20,
        ),
        TextButton(
          onPressed: rollDice,
          style: TextButton.styleFrom(
              foregroundColor: Colors.white,
              // padding: const EdgeInsets.only(top: 20),
              textStyle: const TextStyle(
                fontSize: 28,
              )),
          child: const Text('Roll the dice'),
        )
      ],
    );
  }
}
```

![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/1e41abe8-399b-4f41-82df-9598e5b8e649.png)

## **Adding Transparency to Widgets**
There are two ways :
1. Wrap your widget in Opacity() widget
```
Opacity(
            opacity: 0.5,
            child: Image.asset(
              'assets/images/quiz-logo.png',
              width: 300,
            ),
          ),
```
This approach is performance intensive, you should avoid using it.
2. Use opacity in colors only
```
Image.asset(
              'assets/images/quiz-logo.png',
              width: 300,
              color: const Color.fromARGB(150, 255, 255, 255),
),
```
Here, the A - 150 makes it a bit transparent.

## **Flutter Widget Lifecycle**
![](/home/subroto/.var/app/io.appflowy.AppFlowy/data/AppFlowy/data/images/e1b674f0-4623-4678-918d-5bf0f5fe95f4.png)

## **Using Fonts**
There exists a google_fonts package in flutter which we can use to use Google Fonts.
Steps:
* Install google_fonts package into your project, enter this on terminal
```
flutter pub add google_fonts 
```
* Import it in your dart file
```dart
import 'package:google_fonts/google_fonts.dart';
```
* Then you can add it in the style argument of Text() widget and give the text styling, eg: 
```dart
Text(
              currentQues.text,
              style: GoogleFonts.abel(textStyle: Theme.of(context).textTheme.labelSmall, color: Colors.white, fontSize: 18, fontWeight: FontWeight.bold),
              textAlign: TextAlign.center,
            ),
```
In this way you can use Google Fonts in your flutter project.
To check further(for adding custom fonts) - [link](https://pub.dev/packages/google_fonts)

## **'widget' Property in Stateful Widgets**
In stateful widget, if you create an argument for the Stateful class, then how to pass it to State class ? Well, there exists an inbuilt property called widget, which can be used to do so. eg:
```
class QuestionsScreen extends StatefulWidget {
  const QuestionsScreen({super.key, required this.onSelectAnswers});
  final void Function(String answer) onSelectAnswers;

  @override
  State<QuestionsScreen> createState() => _QuestionsScreenState();
}
// StatefullWidget class has function named onSelectAnswers, we pass it to the State Class by following way 
class _QuestionsScreenState extends State<QuestionsScreen> {
  var currentQuestionIndex = 0;

  void answerQuestion(String selectedAnswer) {
    widget.onSelectAnswers(selectedAnswer);
    setState(() {
      currentQuestionIndex == 5
          ? currentQuestionIndex = 0
          : currentQuestionIndex++;
    });
  }
```

## **Expanded Widget**
If some widget goes beyond screen boundaries, this widget helps it shrink down and adjust its size within screen boundaries.
It also makes sure that the contents inside it are restricted to the widht and height of the parent widget of expanded widget.

