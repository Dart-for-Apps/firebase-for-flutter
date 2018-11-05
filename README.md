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
