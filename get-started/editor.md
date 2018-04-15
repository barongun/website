---
layout: page
title: "시작하기: Editor 설정하기"
permalink: /get-started/editor/
---

우리의 command-line tools와 결합 된 텍스트 editor를 사용하여 Flutter로 을 만들 수 있습니다. 그러나 더 나은 환경을 위해 editor 플러그인 중 하나를 사용하는 것이 좋습니다. editor 플러그인을 사용하면 코드 완성, 구문 강조, 위젯 편집 보조, 실행 및 디버그 지원 등을 얻을 수 있습니다.

Android Studio, IntelliJ 또는 VS 코드 용 editor 플러그인을 추가하기 전에 다음 단계를 따르세요. 다른 editor를 사용해도 무방합니다. 넘기시려면 [다음 단계: 최초 app을 만들어보기](/get-started/test-drive/) 로 넘어가세요.

<div id="tab-set-install">

<ul class="tabs__top-bar">
    <li class="tab-link current" data-tab="tab-install-androidstudio">Android Studio</li>
    <li class="tab-link" data-tab="tab-install-vscode">VS Code</li>
</ul>

<div id="tab-install-androidstudio" class="tabs__content current" markdown="1">

## Android Studio 설정하기

*Android Studio:* Flutter를 위한 완벽한 통합 IDE의 경험을 제공합니다.

### Android Studio 설치하기

   * [Android Studio](https://developer.android.com/studio/index.html), version 3.0 or later.

또는, IntelliJ를 사용할 수도 있습니다:

   * [IntelliJ IDEA Community](https://www.jetbrains.com/idea/download/), version 2017.1 or later.
   * [IntelliJ IDEA Ultimate](https://www.jetbrains.com/idea/download/), version 2017.1 or later.

### Flutter 와 Dart plugins을 설치하기

Flutter는 두가지 plugin을 지원합니다:

   * Flutter plugin으로 개발자 워크플로우가 더욱 강력 해졌습니다.(실행, 디버깅, hot reload 등)
   * `Dart` plugin은 코드 분석기능을 제공합니다.(타이핑할 때 유효성 검사, 코드완성 등)

설치는 아래와 같이 하세요:

   1. Android Studio를 실행하세요.
   1. plugin preferences를 여세요 (macOS에서는 **Preferences>Plugins**를,
      Windows & Linux 에서는 **File>Settings>Plugins**를 여세요).
   1. **Browse repositories…**를 선택하세요,  Flutter plug-in을 선택하고 `install` 을 클릭하세요.
   1. 다트 플러그인을 설치하라는 메시지가 나타나면 `Yes`를 클릭하십시오.
   1. 메시지가 나타나면 `Restart`을 클릭하십시오.

</div>

<div id="tab-install-vscode" class="tabs__content" markdown="1">

## Visual Studio Code (VS Code) setup

*VS Code:* Flutter 실행 및 디버그를 지원하는 경량 편집기 입니다.

### VS Code를 설치하기

  * [VS Code](https://code.visualstudio.com/), version 1.20.1 or later.

### Dart Code plugin을 설치하기

  1. VS Code를 실행합니다.
  1. **View>Command Palette...**를 호출합니다.
  1. 'install'을 입력 한 후 **'Extensions: Install Extension'** 액션을 선택합니다.
  1. 검색 필드에서 `dart code`를 입력하고, 목록에서 'Dart Code'를 선택한 후 **Install** 을 클릭하세요.
  1. 'OK'를 선택하고 VS Code를 재구동 합니다.

## Flutter Doctor로 설정을 확인

  1. **View>Command Palette...**를 호출합니다.
  1. 'doctor'를 입력 한 후 **'Flutter: Run Flutter Doctor'** 액션을 선택합니다.
  1. 'OUTPUT'창에서 출력을 확인하여 문제가 없는지 봅니다.

</div>

</div>

## 다음 단계

Test Drive를 위한 Flutter를 시작해 봅니다: 첫 project를 생성하고, 실행하고, 'hot reload'fmf 경험해 봅니다.

[다음 단계: Test drive Flutter](/get-started/test-drive/)
