CocoaPods-practice
==================

推荐
http://www.exiatian.com/cocoapods%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8%E5%8F%8A%E9%85%8D%E7%BD%AE%E7%A7%81%E6%9C%89%E5%BA%93/

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

## cocoapods提示ld: library not found for -lPods？

用上cocoapods来管理依赖后遇到一个问题，编译的时候提示 `objc ld: library not found for -lPods`

原来是打开的方式不对，之前一直打开的是.xcodeproj，其实需要打开的是.xcworkspace

http://stackoverflow.com/questions/9863836/library-not-found-for-lpods#comment25471410_9988853


## 增加splash图片

最新版的xcode6 GM版新建项目，什么都不做，然后真机跑起来（iPhone 5s、itouch 5），显示的却是 320 * 480 大小，

只要把res/splash丢到项目里就可以了


## pod install速度特别慢的解决办法

每次都要升级cocoapods的spec仓库，在命令执行时添加参数可以略过此步。

珍爱生命吧！

安装方法

	sudo npm install -g cocoapods-cli
 
目前有2个命令podi和podu

- `podi` = `pod install --verbose --no-repo-update`
- `podu` = `pod update --verbose --no-repo-update`
	
更多见https://github.com/i5ting/cocoapods-cli
	