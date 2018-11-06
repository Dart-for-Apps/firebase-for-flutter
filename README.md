# firebase for flutter

구글 코드랩스의 [firebase for flutter](https://codelabs.developers.google.com/codelabs/flutter-firebase/#0)
강의에 대한 소스코드 리포지토리 입니다.
주석 및 설명은 모두 한글을 기본으로 사용합니다.

[startup_namer](https://github.com/flutter-tutorial/startup_namer) 부터 
순서대로 연습하는것을 추천합니다.

## Introduction

플러터 (flutter) 와 파이어베이스 (firebase) 는 매우 밀접히 연결되어 있어서 개발자가 빠르게 앱을 개발할 수 있도록 돕습니다.
[플러터](https://flutter.io/) 는 iOS와 안드로이드의 앱을 만들기 위해 google이 제공하는 SDK 입니다.
[파이어베이스](https://firebase.google.com/) 는 모바일 애플리케이션을 위한 백엔드 서비스들을 쉽게 구축하고 사용할 수 있도록
도와주는 서비스로, 인증/스토리지/데이터베이스/호스팅 등의 다양한 기능을 개인 서버 구축을 하지 않고 사용할 수 있도록 합니다.

이번 코드랩에서는 파이어베이스를 사용하는 플러터 앱을 만드는 방법을 다룹니다. 실제로 만들어볼 앱은 새로 태어날 아기의 이름을
주변 지인들의 투표로 결정하는 앱입니다. 앱에서는 [클라우드 파이어스토어(Cloud Firestore)](https://firebase.google.com/products/firestore/)
데이터베이스를 사용하여 데이터를 관리하게 됩니다.

안드로이드와 iOS에서 보여질 앱의 전체 형태는 아래와 같습니다. 아래에서 볼 수 있듯이, 플러터를 사용하면
iOS와 안드로이드 앱을 동시에 같은 코드로 개발할 수 있습니다.

![ios-intro](./imgs-for-doc/ios-intro.png) ![android-intro](./imgs-for-doc/android-intro.png)

비슷한 동영상 강좌는 [이 링크](https://youtu.be/DqJ_KjFzL9I?list=PLOU2XLYxmsIJ7dsVN4iRuA7BT8XHzGtCr)에서 확인하실 수 있습니다.
해당 동영상에서는 본 코드랩 강의 전체적인 스텝을 쉽게 이해할 수 있도록 돕는 좋은 영상입니다.

## 플러터 개발 환경 세팅하기

플러터 개발 환경 세팅은 [이 링크](https://codelabs.developers.google.com/codelabs/flutter-firebase/index.html?index=..%2F..%2Findex#2)
를 참조하기 바랍니다.

## 새로운 플러터 앱 환경 만들고 패키지 의존성 설정하기

1. 플러터를 이용하여 새로운 앱을 개발하기 위해, [Get started](https://flutter.io/get-started/test-drive/) 가이드를
참조하여 플러터 프로젝트를 생성합니다. 앱의 이름은 `baby_names`로 설정합니다.
새로운 플러터 프로젝트를 생성하고 설정하는 것은 사용하는 코드 에디터에 따라 다르므로 매뉴얼을 참고하기 바랍니다.
> 안드로이드 스튜디오를 사용하는 경우 [플러그인](https://flutter.io/get-started/editor/#androidstudio) 을 설치하면
> 더욱 쉽게 개발할 수 있습니다.

2. 앱을 실행하기 전에 3, 4번 단계를 먼저 수행합니다.
3. `pubspec.yaml`을 연 뒤 dependencies 태그에 `cloud_firestore` 를 추가합니다. 
```yaml
dependencies:
    flutter:
        sdk: flutter
    cloud_firestore: ^0.8.2  #새롭게 추가할 코드
```
> cloud firestore의 최신 버전은 [여기](https://pub.dartlang.org/packages/cloud_firestore)에서 확인할 수 있습니다. 패키지 의존성 설정 관련해서는 [이 링크](https://www.dartlang.org/tools/pub/dependencies)
> 를 참조하기 바랍니다.

4. 사용하는 IDE에서나 커맨드 라인에서 `flutter packages get` 을 실행합니다.

새로운 `dependencies` 를 추가 할때는 tab이 아닌 스페이스를 사용하기 바랍니다. 

#### 안드로이드 sdk 버전 설정하기 

본 프로젝트를 위해서 안드로이드 에서는 **multi dex**를 지원해야 합니다. 
안드로이드 sdk 버전 21부터 지원되므로 아래의 순서로 안드로이드 컴파일 설정을 수정해야 합니다.
1. `android/app/build.gradle` 파일을 연뒤 `minSdkVersion 16` 부분을 찾습니다.
2. 해당 부분을 `minSdkVersion 21` 로 변경합니다.
3. 파일을 저장 합니다.

#### iOS를 위한 Xcode 빌드 에러 방지하기

1. 플러터 프로젝트의 최상위 폴더에서 `open ios/Runner.xcworkspace` 명령을 통해 Xcode 프로젝트를 엽니다.
2. Xcode가 열리면 `File > Workspace Settings` 메뉴에서 **build system** 을 `Legacy Build System` 으로 변경 합니다. (아래의 스크린샷 참조)

![iOS 세팅](imgs-for-doc/ios-xcode-setting.png)