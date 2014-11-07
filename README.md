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

## ZXing用法
```
pod 'ZXing',            '~> 2.3'
```

## GoogleToolboxForMac 用法

```
	pod 'GTM', :podspec => 'GTM.podspec'
```

再当前目录下放一个GTM.podspec

```
	#
	# Be sure to run `pod spec lint GTM.podspec' to ensure this is a
	# valid spec and remove all comments before submitting the spec.
	#
	# To learn more about the attributes see http://docs.cocoapods.org/specification.html
	#
	Pod::Spec.new do |s|
	  s.name         = "GTM"
	  s.version      = "0.0.1"
	  s.summary      = "Google Toolbox For Mac - mirror"
	  s.homepage     = "https://github.com/maxme/google-toolbox-for-mac"
	  s.license      = 'Apache License Version 2.0'
	  s.author       = "Google"
	  s.source       = {
	    :git => "https://github.com/maxme/google-toolbox-for-mac.git",
	    :tag => "0.0.1"
	  }
	  s.source_files = 'GTMDefines.h', 'Foundation/', 'iPhone/', 'DebugUtils/'
	  s.exclude_files = '**/*Test.m', '*/*AppleEvent*', '*/*Carbon*', \
	  '*/GTMFourCharCode.*', '*/*AppleScript*', '*/*GTMAbstractDOListener*',
	  '*/*FindFolder*', '*/GTMScriptRunner*', '*/GTMTransientRoot*'
	  s.libraries = 'z', 'sqlite3'
	  s.requires_arc = false
	end

```

这里注意source_files文件，至关重要

