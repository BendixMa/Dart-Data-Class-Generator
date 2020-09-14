# Dart Data Class Generator (Beta)

Create dart data classes easily, fast and without writing boilerplate or running code generation.  

## Features

The generator can generate the constructor, copyWith, toMap, fromMap, toJson, fromJson, toString, operator == and hashCode methods for a class based on [class properties](#create-data-classes-based-on-class-properties) or [raw JSON](#create-data-classes-based-on-json-beta).

Additionally the generator has a couple of useful quickfixes to speed up your development process. See the [Additional Features Section](#additional-features) for more.

If this extension is helpful to you, consider giving it a star on [GitHub](https://github.com/bnxm/Dart-Data-Class-Generator) or leave a review on the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=BendixMa.dart-data-class-generator) :heart:

## Create Data Classes Based on Class Properties

![](assets/gif_from_class.gif)

### **Usage**

You can generate data classes either by the quick fix dialog or by running a command. In the quick fix dialog you have the option to not only generate whole data classes but also only specific methods. The command has the advantage of being able to generate multiple classes at the same time.

#### **Quick fix**

- Create a class with properties.
- Place your cursor on the first line of the class, the constructor or a field.
- Hit **CTRL + .** to open the quick fix dialog.
- Choose one of the available options.

#### **Command**

- Create a class with properties.
- Hit **CTRL + P** to open the command dialog.
- Search for **Dart Data Class Generator: Generate from class properties** and hit enter.
- When there are multiple classes in the current file, choose the ones you'd like to create data classes of in the dialog.

It is also possible to run the generator on an existing data class (e.g. when some parameters changed). The generator will then try to find the changes and replace the class with its updated version. **Note that custom changes to generated functions may be overriden**.

You can also customize the generator for example to use [Equatable](https://pub.dev/packages/equatable) for value equality. See the [Settings](#-settings) section for more options.

#### **Enums**

In order for `enums` to be correctly serialized from and to JSON, please annotate them using a comment like so:
```dart
// enum
final Enum myEnum;
```

#### Usage with Equatable

Although using the generator is fast, it still doesn't spare you from all the boiler plate necessary, which can be visually distracting. To reduce the amount of boiler plate needed, the generator works with **Equatable**. Just extend the class with `Equatable` or mix with `EquatableMixin` and the generator will use `Equatable` for value equality. 

<img width="512" src="assets/equatable_demo.gif"/>

You can also use the setting `dart_data_class_generator.useEquatable`, if you always want to use `Equatable` for value equality.

## Create Data Classes Based on JSON (Beta)

![](assets/gif_from_json.gif)

### **Usage**

- Create an **empty dart** file.
- Paste the **raw JSON without modifying it** into the otherwise empty file.
- Hit **CTRL + P** to open the command dialog.
- Search for **Dart Data Class Generator: Generate from JSON** and hit enter.
- Type in a class name in the input dialog. This will be the name of the **top level class** if the JSON contains nested objects, all other class names will be infered from the JSON keys.
- When there are nested objects in the JSON, a dialog will be appear if you want to seperate the classes into multiple files or if all classes should be in the same file.

> **Note:**  
> **This feature is still in beta!**  
> **Many API's return numbers like 0 or 1 as an integer and not as a double even when they otherwise are. Thus the generator may confuse a value that is usually a double as an int.**  

## Additional Features

The extension includes some additional quick fixes that might be useful to you:

### Annotate parameters with @required

Quickly annotate parameters with @required while importing `package:meta/meta.dart` if there's no import for it already.

<img width="512" src="assets/required_demo.gif"/>

### Import refactoring

Sort imports alphabetically and bring them into the correct format easily.

<img width="512" src="assets/import_demo.gif"/>


## Settings

You can customize the generator to only generate the functions you want in your settings file.

* `dart_data_class_generator.quick_fixes`: If true, enables quick fixes to quickly generate data classes or specific methods only.
* `dart_data_class_generator.useEquatable`: If true, uses Equatable for value equality and hashCode.
* `dart_data_class_generator.fromMap.default_values`: If true, checks if a field is null when deserializing and provides a non-null default value.
* `dart_data_class_generator.constructor.default_values`: If true, generates default values for the constructor.
* `dart_data_class_generator.constructor.required`: If true, generates @required annotation for every constructor parameter. Note: The generator wont generate default values for the constructor if enabled!
* `dart_data_class_generator.json.seperate`: Whether to seperate a JSON into multiple files, when the JSON contains nested objects. ask: choose manually every time, seperate: always seperate into multiple files, current_file: always insert all classes into the current file.
* `dart_data_class_generator.override.manual`: If true, asks, when overriding a class (running the command on an existing class), for every single function/constructor that needs to be changed whether the generator should override the function or not. This allows you to preserve custom changes you made to the function/constructor that would be otherwise overwritten by the generator.
* `dart_data_class_generator.constructor.enabled`: If true, generates a constructor for a data class.
* `dart_data_class_generator.copyWith.enabled`: If true, generates a copyWith function for a data class.
* `dart_data_class_generator.toMap.enabled`: If true, generates a toMap function for a data class.
* `dart_data_class_generator.fromMap.enabled`: If true, generates a fromMap function for a data class.
* `dart_data_class_generator.toJson.enabled`: If true, generates a toJson function for a data class.
* `dart_data_class_generator.fromJson.enabled`: If true, generates a fromJson function for a data class.
* `dart_data_class_generator.toString.enabled`: If true, generates a toString function for a data class.
* `dart_data_class_generator.equality.enabled`: If true, generates an override of the == (equals) operator for a data class.
* `dart_data_class_generator.stringify.enabled`: If true, generates a override of the stringify function for a data class.
* `dart_data_class_generator.hashCode.enabled`: If true, generates a hashCode function for a data class.
* `dart_data_class_generator.hashCode.use_jenkins`: If true, uses the Jenkins SMI hash function instead of bitwise operator from dart:ui.