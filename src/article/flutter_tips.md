{
"title":"Flutter Tips",
"updatedAt":"2022-03-12",
"excerpt":"Flutter Tips Collection",
"published":true
}

---

flutter tips collection.

## ![](/paper/images/flutter_tips_excerpt.svg?w=725&h=434)

## 1. Custom Widget

### Spacing design 8 rule

#### What is the 8 rule?

The theory is quite simple: the idea is that all the elements in your design are a multiple of 8 in terms of width and height, just as their spacing.

```dart
class AppSpacer extends StatelessWidget {
  final double? width;
  final double? height;

  const AppSpacer._({Key? key, this.width, this.height}) : super(key:key);

  factory APpSpacer.p32() => const AppSpacer._(height:32, width:32);
  factory APpSpacer.p24() => const AppSpacer._(height:24, width:24);
  factory APpSpacer.p16() => const AppSpacer._(height:16, width:16);
  factory APpSpacer.p8() => const AppSpacer._(height:8, width:8);

  @override
  Widget build(BuildContext context) {
    return SizedBox(
      width:width,
      height:height,
    );
  }
}
```

### Rounded Corners for Images

```dart
ClipRect(
  borderRadius: BorderRadius.circular(8.0),
  child: Image.network(
    'https://example.com/image.jpg',
    height: 150.0,
    width: 150.0,
    fix: BoxFit.cover,
  ),
)
```

### Theme color widget

```dart
import 'dart:ui';

class AppColors {
  static const Color textColor = Color(0xFFccc7c5);
  static const Color mainColor = Color(0xFF89dad0);
  static const Color iconColor1 = Color(0xFFffd28d);
  static const Color iconColor2 = Color(0xFFfcab88);
  static const Color paraColor = Color(0xFF8f837f);
  static const Color buttonBackgroundColor = Color(0xFFf7f6f4);
  static const Color signColor = Color(0xFFa9a29f);
  static const Color titleColor = Color(0xFF5c524f);
  static const Color mainBlackColor = Color(0xFF332d2b);
  static const Color yellowColor = Color(0xFFffd379);
}
```

## 2. Optimize code

### Simplify styling code and reduce nesting

```dart
class HStack extends Column {
  HStack(
    this.childList, {
    Key? key,
    MainAxisAlignment main = MainAxisAlignment.start,
    CrossAxisAlignment cross = CrossAxisAlignment.center,
  }) : super(
          key: key,
          children: childList,
          mainAxisAlignment: main,
          crossAxisAlignment: cross,
        );

  final List<Widget> childList;
}

class VStack extends Row {
  VStack(
    this.childList, {
    Key? key,
    MainAxisAlignment main = MainAxisAlignment.start,
    CrossAxisAlignment cross = CrossAxisAlignment.center,
  }) : super(
          key: key,
          children: childList,
          mainAxisAlignment: main,
          crossAxisAlignment: cross,
        );

  final List<Widget> childList;
}

Padding(child, all: 12, top: '12', right: ,bottom: ,left: , vertical: horizontal: )

```

### Create widgets configurations

![](/paper/images/create_widgets_configurations.jpeg?w=1600&h=900)

keyword：factory

### How to store sensitive data on phone?

Don't locally store passwords or other sensitives data in clear text

Using flutter_secure_storage plugin

```dart
// Create storage
final storage = new FlutterSecureStorage();
// Read value
String value = await storage.read(key:key);
// Write value
await storage.write(key:key, value:value);
```

## 3. Cool Style

### Glass Effect

![](/paper/images/glass_effect.jpeg?w=1728&h=895)

If you've seen that cool Glass effect in UI design and wanted to add it to your app, you can easily do so with the BlackdropFilter widget.

```dart
ClipRect(
  child: BackdropFilter(
    filter: ImageFilter.blur(
      sigmaX: 15,
      sigmaY: 15,
    ),
    child: Child(),
  ),
)
```

### Change Text Field Height & Width

You can change the height and width of the TextField widget using the following methods.

```dart
SizedBox(
  height: 50,
  child: TextField(),
)

TextField(
  decoration: const InputDecoration(
    isDense: true,
    contentPadding: const EdgeInsets.symmetric(
      vertical: 40.0,
      horizontal: 20.0
    ),
  ),
)
```

### Implement Animation Guide

![](/paper/images/flutter_tips_animation_guide.jpeg?w=1019&h=1125&border=true)

## 4. Package

## 5. Source Code Analyze

## 6. Debug And Test

### Waiting for another flutter command to release

Did you ever encounter the following issue while trying to run a Flutter app?

This is How to fix it👇

```dart
// 1. Try restarting the IDE
// 2. Run following command in terminal
killall -9 dart
```

### Search iOS Simulator Device

```bash
xcrun simctl list | grep '(Booted)'
```
