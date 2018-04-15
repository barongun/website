## iOS 설정

### Xcode 설치

iOS 용 Flutter app을 개발하려면 Xcode 9.0 이상이 설치된 Mac이 필요합니다.

1. Xcode 9.0 이상을 설치합니다. (via [web download](https://developer.apple.com/xcode/) or
the [Mac App Store](https://itunes.apple.com/us/app/xcode/id497799835)).

1. 명령 줄에서 `sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer` 를 실행하여 Xcode의 새 버전을 사용하도록 Xcode command-line tools를 설정하세요.

   Xcode의 최신 버전을 사용하려는 경우 대부분 올바른 경로입니다. 다른 버전을 사용해야하는 경우 대신 해당 경로를 지정하십시오.
1. Xcode 사용권 계약이 Xcode를 한 번 열었거나 명령줄에서 `sudo xcodebuild -license`를 실행하여 서명하였는지 확인해 주세요.

Xcode를 사용하면 iOS 기기 또는 시뮬레이터에서 Flutter app을 실행할 수 있습니다.

### iOS 시뮬레이터 설정하기

iOS 시뮬레이터에서 Flutter app을 실행하고 테스트하려면 다음 단계를 따르세요:

1. Mac의 경우엔,  Spotlight나 다음 명령을 사용하여 시뮬레이터를 찾으십시오.

{% commandline %}
open -a Simulator
{% endcommandline %}

2. 시뮬레이터의 **Hardware > Device** 메뉴에서 설정을 확인하여 시뮬레이터가 64 비트 장치 (iPhone 5s 이상)를 사용하고 있는지 확인하세요.

3. 개발 컴퓨터의 화면 크기에 따라 시뮬레이트 된 높은 화면 밀도(high-screen-density)의 iOS 장치가 화면을 오버 플로우시킬 수 있습니다. 시뮬레이터의 **Window > Scale** 메뉴 아래에 device scale을 설정하십시오.

4. `flutter run`을 실행하여 app을 시작합니다.


### iOS 기기에 배포하기

Flutter app을 실제 iOS 기기에 배포하려면 몇 가지 추가 도구와 Apple 계정이 필요합니다. 또한 Xcode에서 실단말을 설정해야합니다.

1. [homebrew](http://brew.sh/)를 설치하세요.
1. 터미널을 열고 다음 명령을 실행하여 Flutter app을 iOS 기기에 배포하기위해 도구를 설치하십시오.

{% commandline %}
brew update
brew install --HEAD libimobiledevice
brew install ideviceinstaller ios-deploy cocoapods
pod setup
{% endcommandline %}

   이러한 명령 중 하나라도 오류와 함께 실패하면 `brew doctor`를 실행하고 지시 사항에 따라 문제를 해결하세요.

1. Follow the Xcode signing flow to provision your project:
    1. Flutter 프로젝트 디렉토리의 터미널 창에서 `open ios/Runner.xcworkspace`를 실행하여 프로젝트에서 기본 Xcode workspace를 엽니다.
    1. Xcode에서 왼쪽 탐색 패널의 `Runner` 프로젝트를 선택하십시오.
    1. `Runner` 타겟 설정 페이지에서 **General > Signing > Team** 에서 개발 팀이 선택되어 있는지 확인하십시오. 팀을 선택하면 Xcode에서 개발 인증서를 생성 및 다운로드하고 장치를 계정에 등록하며 프로비저닝 프로파일을 작성 및 다운로드합니다. (필요시에)
        * 첫 iOS 개발 프로젝트를 시작하려면 Apple ID로 Xcode에 로그인이 필요합니다.<br>
        ![Xcode account add](/images/setup/xcode-account.png)<br>
        개발 및 테스트는 모든 Apple ID에서 지원됩니다. 앱을 App Store에 배포하려면 Apple Developer Program에 등록해야합니다. [Apple 맴버십 타입의 차이점](https://developer.apple.com/support/compare-memberships) 를 확인해 보세요.
        * 처음 iOS 개발을 위해 연결된 실단말을 사용할 때, 해당 장치에서 Mac과 개발 인증서를 모두 신뢰가 필요합니다. iOS 장비를 Mac에 처음 연결할 때 대화 상자에서 `Trust`를 선택하십시오.<br>
        ![Trust Mac](/images/setup/trust-computer.png)<br>
        그런 다음 iOS 기기의 설정 앱으로 이동하여 **General > Device Management**를 선택하고 인증서를 신뢰합니다.
        * Xcode에서 자동 서명이 실패하면 프로젝트의 **General > Identity > Bundle Identifier** 값이 고유한지 확인하십시오. <br>
        ![Check the app's Bundle ID](/images/setup/xcode-unique-bundle-id.png)
1. `flutter run` 을 실행해 app을 구동합니다.
