---
layout: page
title: "시작하기: Test Drive"
permalink: /get-started/test-drive/
---

이 페이지에서는 Flutter의 "test drive"방법에 대해 설명합니다: 템플릿에서 새로운 Flutter 앱을 만들고, 실행하고, Hot Reload로 변경하는 방법을 배웁니다.

Flutter는 유연한 툴킷이므로 Flutter 앱을 작성, 제작 및 실행하기위한 개발 도구를 선택하여 시작하십시오.

<div id="tab-set-install">

<ul class="tabs__top-bar">
    <li class="tab-link current" data-tab="tab-install-androidstudio">Android Studio</li>
    <li class="tab-link" data-tab="tab-install-vscode">VS Code</li>
    <li class="tab-link" data-tab="tab-install-terminal">Terminal + editor</li>
</ul>

<div id="tab-install-androidstudio" class="tabs__content current" markdown="1">

*Android Studio:* Flutter를위한 완벽한 통합 IDE 경험을 제공합니다.

## 새로운 app 만들기 {#create-app}

   1. **File>New Flutter Project**를 선택합니다.
   1. project type에서 **Flutter application**를 선택하고 Next를 누릅니다.
   1. project name을 입력하고 (e.g. `myapp`) Next를 누릅니다.
   1. **Finish**를 클릭합니다.
   1. Android Studio가 SDK를 설치하고 프로젝트를 만들 때까지 기다립니다.

위의 명령은 [Material Components](https://material.io/guidelines/)를 사용하는 간단한 데모를 포함하는 `myapp`이라는 Flutter 프로젝트 디렉토리를 만듭니다.

프로젝트 디렉토리에서 앱의 코드는 `lib/main.dart`에 있습니다.

## app 실행하기

   1. main Android Studio toolbar에 위치하고 있습니다:<br>
      ![Main IntelliJ toolbar](/images/intellij/main-toolbar.png)
   1. **target selector**에서 app을 구동하기 위한 Android device를 선택해주세요.
   사용가능 목록이 표시되지 않을 경우엔, **Tools>Android>AVD Manager**를 선택하고 그곳에서 생성하세요. 자세한 내용은 [Managing
      AVDs](https://developer.android.com/studio/run/managing-avds.html)를 확인하세요.
   1. 도구 막대에서 **Run icon**을 클릭하거나 **Run >
      Run**를 호출하세요.
   1. 정상적으로 작동이 되었을 때, app을 생성한 후에는 기기 또는 시뮬레이터에 시작 app이 표시 되어야 합니다:<br>
      ![Starter App on Android](/images/flutter-starter-app-android.png)

## Hot reload 시도하기

Flutter는 _hot reload_ 가 빠른 개발주기를 제공하며 앱을 재구동하거나 잃지 상태를 잃지 않고도 실행중인 앱의 코드를 다시로드 할 수 있습니다. 단순히 소스 코드를 변경하고, 새로 고침을 원하는 IDE 또는 command-line tool에 알려주고 시뮬레이터, 에뮬레이터 또는 장치의 변경 사항을 확인하십시오.

  1. `'You have pushed the button this many times:'`를<br>
  `'You have clicked the button this many times:'`로 바꿔보세요.
  1. 'Stop' 버튼을 누르지 마시고 app을 계속 구동하세요.
  1. 변경 내용을 보려면 **Save All** (`cmd-s` / `ctrl-s`)버튼이나 **Hot Reload button** (번개 아이콘의 버튼) 버튼을 클릭하세요.

실행중인 app에서 업데이트 된 문자열이 거의 즉시 보일 것입니다.

</div>

<div id="tab-install-vscode" class="tabs__content" markdown="1">

*VS Code:* Flutter 실행 및 디버그를 지원하는 경량 편집기 입니다.

## 새로운 app 만들기

  1. VS Code를 실행합니다.
  1. **View>Command Palette...**를 실행합니다.
  1. 'flutter'라고 입력 하고 **'Flutter: New Project'** 액션을 선택합니다.
  1. project name을 입력하고 (e.g. `myapp`) Enter를 누릅니다.
  1. project 경로를 지정하고 파란색 OK button을 클릭합니다.
  1. project가 생성되고 `main.dart` 파일이 나올 때까지 기다립니다.

위의 명령은 [Material Components](https://material.io/guidelines/)를 사용하는 간단한 데모를 포함하는 `myapp`이라는 Flutter 프로젝트 디렉토리를 만듭니다.

프로젝트 디렉토리에서 앱의 코드는 `lib/main.dart`에 있습니다.

## app 실행하기

  1. VS Code의 오른쪽 하단에 대상 장치가 선택되어 있는지 확인해 주세요.
  1. 키보드의 F5 버튼을 클릭하거나 **Debug>Start Debugging**를 호출하세요.
  1. app이 시작될 때까지 기다려 주세요.
  1. 정상적으로 작동이 되었을 때, app을 생성한 후에는 기기 또는 시뮬레이터에 시작 app이 표시 되어야 합니다:<br>
      ![Starter App on Android](/images/flutter-starter-app-android.png)

## Hot reload 시도하기

Flutter는 _hot reload_ 가 빠른 개발주기를 제공하며 앱을 재구동하거나 잃지 상태를 잃지 않고도 실행중인 앱의 코드를 다시로드 할 수 있습니다. 단순히 소스 코드를 변경하고, 새로 고침을 원하는 IDE 또는 command-line tool에 알려주고 시뮬레이터, 에뮬레이터 또는 장치의 변경 사항을 확인하십시오.

  1. 좋아하는 Dart code editor에서 `lib/main.dart` 파일을 열어보세요.
  1. `'You have pushed the button this many times:'`를 <br>
  `'You have clicked the button this many times:'` 로 바꿔보세요.
  1. 'Stop' 버튼을 누르지 마시고 app을 계속 구동하세요.
  1. 변경 내용을 보려면 **Save** (`cmd-s` / `ctrl-s`)버튼이나 **Hot Reload button** (녹색 원형 화살표 버튼) 버튼을 클릭하세요.

실행중인 app에서 업데이트 된 문자열이 거의 즉시 보일 것입니다.

</div>

<div id="tab-install-terminal" class="tabs__content" markdown="1">

*Terminal + editor:* Your editor-of-choice combined with Flutter's terminal tool
for running and building.

## 새로운 app 만들기

   1. `flutter create` 명령어를 사용하여 새 프로젝트를 만드세요:
   {% commandline %}
   flutter create myapp
   cd myapp
   {% endcommandline %}

위의 명령은 [Material Components](https://material.io/guidelines/)를 사용하는 간단한 데모를 포함하는 myapp이라는 Flutter 프로젝트 디렉토리를 만듭니다.

프로젝트 디렉토리에서 앱의 코드는 `lib/main.dart`에 있습니다.

## app 실행하기

   * Android 기기가 실행 중인지 확인합니다. 아무것도 보이지 않는다면, [setup](/get-started/install/) 을 확인하세요.
   {% commandline %}
   flutter devices
   {% endcommandline %}
   * `flutter run` 명령으로 앱을 실행합니다.
   {% commandline %}
   flutter run
   {% endcommandline %}
   * 정상적으로 작동이 되었을 때, app을 생성한 후에는 기기 또는 시뮬레이터에 시작 app이 표시 되어야 합니다:<br> 
      ![Starter App on Android](/images/flutter-starter-app-android.png)

## Hot reload 시도하기

Flutter는 _hot reload_ 가 빠른 개발주기를 제공하며 앱을 재구동하거나 잃지 상태를 잃지 않고도 실행중인 앱의 코드를 다시로드 할 수 있습니다. 단순히 소스 코드를 변경하고, 새로 고침을 원하는 IDE 또는 command-line tool에 알려주고 시뮬레이터, 에뮬레이터 또는 장치의 변경 사항을 확인하십시오.

  1. `lib/main.dart` 파일을 열어보세요.
  1. `'You have pushed the button this many times:'`
     를<br>`'You have clicked the button this many times:'`로 바꿔보세요.
  1. 'Stop'버튼을 누르지 마시고 app을 계속 구동하세요.
  1. 변경 내용을 보려면 **Save All** (`cmd-s` / `ctrl-s`) 버튼이나
     **Hot Reload button** (번개 아이콘이있는 버튼) 버튼을 클릭하세요.

실행중인 app에서 업데이트 된 문자열이 거의 즉시 보일 것입니다.

</div>

</div>

## 다음 단계

작은 app을 만들어 Flutter의 핵심 개념을 배우세요.
Let's learn some core Flutter concepts, by creating a small app.

[다음 단계: 최초의 Flutter App 작성하기](/get-started/codelab/)
