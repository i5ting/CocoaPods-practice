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
	
# creating and configuring new Xcode projects

##  liftoff

CLI for creating and configuring new Xcode projects

https://github.com/thoughtbot/liftoff

for oc project(see http://stackoverflow.com/questions/26777519/project-template-in-liftoff)
 
 liftoff --template objc
 
the default is using swift


```
 bbbbb  liftoff --template objc
Project name? sdfjlk
Company name? sdf
Company identifier? |com.sdf| sdf
Prefix? 
Generating the 'objc' project template

/Users/sang/.rvm/gems/ruby-2.1.2/bin/pod
Running pod install
Analyzing dependencies




^C/usr/local/Cellar/liftoff/1.4.1/rubylib/liftoff/cocoapods_setup.rb:26:in `system': Interrupt
	from /usr/local/Cellar/liftoff/1.4.1/rubylib/liftoff/cocoapods_setup.rb:26:in `run_pod_install'
	from /usr/local/Cellar/liftoff/1.4.1/rubylib/liftoff/cocoapods_setup.rb:7:in `install_cocoapods'
	from /usr/local/Cellar/liftoff/1.4.1/rubylib/liftoff/launchpad.rb:49:in `install_cocoapods'
	from /usr/local/Cellar/liftoff/1.4.1/rubylib/liftoff/launchpad.rb:16:in `block in liftoff'
	from /usr/local/Cellar/liftoff/1.4.1/rubylib/liftoff/file_manager.rb:5:in `chdir'
	from /usr/local/Cellar/liftoff/1.4.1/rubylib/liftoff/file_manager.rb:5:in `create_project_dir'
	from /usr/local/Cellar/liftoff/1.4.1/rubylib/liftoff/launchpad.rb:14:in `liftoff'
	from /usr/local/Cellar/liftoff/1.4.1/rubylib/liftoff/cli.rb:10:in `run'
	from /usr/local/bin/liftoff:14:in `<main>'
[!] Cancelled
```

此时一定要中断，然后

```
bbbbb  cd sdfjlk 
➜  sdfjlk  podi
  Preparing

Analyzing dependencies

Inspecting targets to integrate
  Using `ARCHS` setting to build architectures of target `Pods`: (``)
  Using `ARCHS` setting to build architectures of target `Pods-unit_tests`: (``)

Resolving dependencies of `Podfile`
Resolving dependencies for target `Pods' (iOS 8.0)
Resolving dependencies for target `unit_tests' (iOS 8.0)
  - Specta
  - Expecta
  - OCMock
  - OHHTTPStubs
    - OHHTTPStubs/Core

Comparing resolved specification to the sandbox manifest
  A Expecta
  A OCMock
  A OHHTTPStubs
  A Specta

Downloading dependencies

-> Installing Expecta (0.3.1)
 > Git download
 > Git download
     $ /usr/bin/git clone https://github.com/specta/expecta.git /Users/sang/workspace/github/bbbbb/sdfjlk/Pods/Expecta --single-branch --depth 1 --branch v0.3.1
     Cloning into '/Users/sang/workspace/github/bbbbb/sdfjlk/Pods/Expecta'...
     Note: checking out '60388f9dec0292bf8e45c120f43515c52b6ca507'.
     
     You are in 'detached HEAD' state. You can look around, make experimental
     changes and commit them, and you can discard any commits you make in this
     state without impacting any branches by performing another checkout.
     
     If you want to create a new branch to retain commits you create, you may
     do so (now or later) by using -b with the checkout command again. Example:
     
       git checkout -b new_branch_name
     

-> Installing OCMock (3.1.1)
 > Git download
 > Git download
     $ /usr/bin/git clone https://github.com/erikdoe/ocmock.git /Users/sang/workspace/github/bbbbb/sdfjlk/Pods/OCMock --single-branch --depth 1 --branch v3.1.1
     Cloning into '/Users/sang/workspace/github/bbbbb/sdfjlk/Pods/OCMock'...
     Note: checking out '971b00bd06bc8e1e31f340c38046f6b45afaa638'.
     
     You are in 'detached HEAD' state. You can look around, make experimental
     changes and commit them, and you can discard any commits you make in this
     state without impacting any branches by performing another checkout.
     
     If you want to create a new branch to retain commits you create, you may
     do so (now or later) by using -b with the checkout command again. Example:
     
       git checkout -b new_branch_name
     

-> Installing OHHTTPStubs (3.1.6)
 > Git download
 > Git download
     $ /usr/bin/git clone https://github.com/AliSoftware/OHHTTPStubs.git /Users/sang/workspace/github/bbbbb/sdfjlk/Pods/OHHTTPStubs --single-branch --depth 1 --branch 3.1.6
     Cloning into '/Users/sang/workspace/github/bbbbb/sdfjlk/Pods/OHHTTPStubs'...
     Note: checking out '769aadd66e3707355b66ee4820710c56728bf275'.
     
     You are in 'detached HEAD' state. You can look around, make experimental
     changes and commit them, and you can discard any commits you make in this
     state without impacting any branches by performing another checkout.
     
     If you want to create a new branch to retain commits you create, you may
     do so (now or later) by using -b with the checkout command again. Example:
     
       git checkout -b new_branch_name
     

-> Installing Specta (0.2.1)
 > Git download
 > Git download
     $ /usr/bin/git clone https://github.com/specta/specta.git /Users/sang/workspace/github/bbbbb/sdfjlk/Pods/Specta --single-branch --depth 1 --branch v0.2.1
     Cloning into '/Users/sang/workspace/github/bbbbb/sdfjlk/Pods/Specta'...
     Note: checking out 'ea97fe9d7fb8be860b0fa1ffde31887d0764546e'.
     
     You are in 'detached HEAD' state. You can look around, make experimental
     changes and commit them, and you can discard any commits you make in this
     state without impacting any branches by performing another checkout.
     
     If you want to create a new branch to retain commits you create, you may
     do so (now or later) by using -b with the checkout command again. Example:
     
       git checkout -b new_branch_name
     
  - Running pre install hooks

Generating Pods project
  - Creating Pods project
  - Adding source files to Pods project
  - Adding frameworks to Pods project
  - Adding libraries to Pods project
  - Adding resources to Pods project
  - Linking headers
  - Installing targets
    - Installing target `Pods-unit_tests-Expecta` iOS 8.0
    - Installing target `Pods-unit_tests-OCMock` iOS 8.0
    - Installing target `Pods-unit_tests-OHHTTPStubs` iOS 8.0
    - Installing target `Pods-unit_tests-Specta` iOS 8.0
    - Installing target `Pods-unit_tests` iOS 8.0
  - Running post install hooks
  - Writing Xcode project file to `Pods/Pods.xcodeproj`
  - Writing Lockfile in `Podfile.lock`
  - Writing Manifest in `Pods/Manifest.lock`

Integrating client project

[!] From now on use `sdfjlk.xcworkspace`.

Integrating target `Pods-unit_tests` (`sdfjlk.xcodeproj` project)

[!] The use of implicit sources has been deprecated. To continue using all of the sources currently on your machine, add the following to the top of your Podfile:

    source 'https://github.com/CocoaPods/Specs.git'
Success: pod install --verbose --no-repo-update execute success
➜  sdfjlk  

```

很快就搞定了


# awesome-ios

https://github.com/vsouza/awesome-ios

# ios官方入门教程
https://developer.apple.com/library/ios/referencelibrary/GettingStarted/RoadMapiOS/FirstTutorial.html#//apple_ref/doc/uid/TP40011343-CH3-SW1