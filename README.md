# my_first_app

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