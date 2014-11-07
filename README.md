CocoaPods-practice
==================


## inimum requirement

如果出现问题：

```
The platform of the target `Pods` (iOS 4.3) is not compatible with `AFNetworking (2.0.3)` which has a minimum requirement of OS X 10.8 - iOS 6.0.
```

可以修改Podfile为：

```
platform :ios, '6.0'
```

