# my_first_app
# LAB 1
My first Flutter app, made for Lab 1. It runs on my own phone (a Samsung SM A155F) and greets me by name.

## What the app does
- Shows "Hello, Emerald!" with a second line of text underneath it, inside a `Column` "Welcome to my first Flutter app"
- Uses a custom theme seed colour: teal
- Keeps the counter button from the Flutter template
- Prints the screen width in dp to the debug console(I/flutter (31799): Screen width: 384.0 dp)

## Screenshots
- `docs/app on phone.jpg`: the app running on my phone
- `docs/flutter doctor.jpg`: the output of `flutter doctor`

## Remaining flutter doctor warnings
Chrome and Visual Studio are not set up. They only matter for web and Windows desktop apps, and this lab uses Android only.

## What I learned and what blocked me

Most of this lab was getting everything installed before I could write any code. Once the app ran on my phone, it was satisfying to change the text and theme colour and see the result. I learned how to create a Flutter project, run it on a real device, and use a `Column` to place two `Text` widgets one below the other. I printed my screen width with `debugPrint` and got 384.0 dp, while a classmate's phone showed 380.0 dp, so I learned that screen sizes differ between phones. I also practised Git and GitHub with several commits.

What blocked me: the first build took a long time and the terminal showed many Gradle and Java warnings, so I thought something was broken, but they were only warnings. flutter doctor kept complaining about Chrome and Visual Studio but i could not do anything about it because my laptop did not have sufficient space to install visual studio. Next time I will read the messages more calmly before worrying.

# LAB 2
Flutter app for Chapter 2 (Dart and your first screens). Dart exercises 1 to 4 are in docs/dart.md. Screenshots are in the docs/ folder.

## What I learned and what blocked me:

What I learned. In Dart I learned named parameters with required and default values, null safety with String? and ??, list methods (where, map, fold), and async / await with a Future. In Flutter I learned that the screen is a tree of widgets, that const widgets are created once and reused, and that a parent gives its child constraints (minimum and maximum width and height) while the child chooses its size inside them. This explains my deliberate overflow: a long Text in a Row has no width limit, so it overflowed, and wrapping it in Expanded fixed it by giving it only the remaining space. I also used ListView.builder to show a list of three items, hot reload to change the seed colour live, and the Flutter inspector to read the size and constraints of a widget.

## What blocked me:

First, fold(0, (sum, p) => sum + p) gave a compile error in DartPad because Dart treated sum as an Object; I fixed it with fold<int>. Second, the Android build crashed with "Gradle build daemon disappeared unexpectedly" because org.gradle.jvmargs allowed 8 GB of memory on a laptop with 8 GB of RAM; I lowered it to -Xmx1536M in android/gradle.properties. Third, while editing main.dart I accidentally deleted the MyHomePage class and mixed code inside ProfileCard, so the build failed until I rewrote the file in the right order. Fourth, the Layout Explorer tab does not exist in my DevTools version, so I read the size and constraints in the Widget properties and Render object tabs instead.