# Change Log

## 0.4.0

Added support for enums
Use factory constructors instead of static methods for json serialization

### 0.3.17

Added support for value equality on `Lists`, `Maps` and `Sets`.

### 0.3.16

Class fields can now also be declared after the constructor.
Minor improvements.

### 0.3.6 - 0.3.15

Fixed some bugs.

### 0.3.5

Added support for equatable by setting dart_data_class_generator.useEquatable to true.

Changed setting `dart_data_class_generator.constructor` to `dart_data_class_generator.constructor.enabled`  
Changed setting `dart_data_class_generator.copyWith` to `dart_data_class_generator.copyWith.enabled`  
Changed setting `dart_data_class_generator.toMap` to `dart_data_class_generator.toMap.enabled`  
Changed setting `dart_data_class_generator.fromMap` to `dart_data_class_generator.fromMap.enabled`  
Changed setting `dart_data_class_generator.toJson` to `dart_data_class_generator.toJson.enabled`  
Changed setting `dart_data_class_generator.fromJson` to `dart_data_class_generator.fromJson.enabled`  
Changed setting `dart_data_class_generator.toString` to `dart_data_class_generator.toString.enabled`  
Changed setting `dart_data_class_generator.equality` to `dart_data_class_generator.equality.enabled`  
Changed setting `dart_data_class_generator.hashCode` to `dart_data_class_generator.hashCode.enabled`  

## 0.3.0

Added quick fixes.

## 0.2.0

Added support for @required annotation.  
Changed the default hashCode implementation to bitwise operator.

## 0.1.0

Initial release (Beta).
