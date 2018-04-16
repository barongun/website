## Android 설정하기

<aside class="alert alert-success" markdown="1">
<i class="fa fa-lightbulb-o"> </i> **Note:**
Flutter는 안드로이드 플랫폼의 의존성을 제공하기 위해 안드로이드 스튜디오의 전체 설치에 의존합니다.하지만 여러 editor들로 Flutter 앱을 만들 수 있습니다. 이것은 나중에 언급하기로 하겠습니다.
</aside>

### Android Studio 설치하기

1. [Android Studio](https://developer.android.com/studio/index.html)를 다운로드 후 설치합니다.

1. Android Studio를 시작하고, 'Android Studio Setup Wizard'를 실행 합니다. Android 용으로 개발할 때 Flutter에서 필요로하는 최신 Android SDK, Android SDK Platform-Tools 및 Android SDK Build-Tools가 설치될 것입니다.

### Android device 설정하기

Android 기기에서 Flutter 앱을 실행하고 테스트하려면 Android 4.1 (API 레벨 16) 이상을 실행하는 Android 기기가 필요합니다.

1. 장치에서 **Developer options** 및 **USB debugging** 을 사용합니다. 자세한 지침은 [Android documentation](https://developer.android.com/studio/debug/dev-options.html)에서 확인할 수 있습니다.
3. USB 케이블을 사용하여 단말을 컴퓨터에 연결하십시오. 장치에서 메시지가 나타나면 컴퓨터에서 장치에 액세스 할 수 있도록 권한을 부여하십시오.
4. 터미널에서 `flutter devices` 명령을 실행하여 Flutter가 연결된 Android 장치를 인식하는지 확인합니다.
5. `flutter run`을 실행해 app을 시작하세요.

기본적으로 Flutter는 `adb` 도구의 기반이되는 Android SDK 버전을 사용합니다. Flutter에서 Android SDK의 다른 설치를 사용하려면 `ANDROID_HOME` 환경 변수를 해당 설치 디렉토리로 설정해야합니다.

### Android emulator 설정하기

Android 에뮬레이터에서 Flutter app을 실행하고 테스트하려면 다음 단계를 따르세요:

1. 장치에서 [VM acceleration](https://developer.android.com/studio/run/emulator-acceleration.html) 를 활성화 하세요.
1. **Android Studio>Tools>Android>AVD Manager** 를 실행한 후 **Create Virtual Device** 를 선택하세요.
1. device definition를 고른 후 **Next**을 눌러주세요.
1. 에뮬레이트를 원하는 Android 버전에 대한 하나 이상의 시스템 이미지를 선택한 후 **Next**을 선택하세요. _x86_ 이나 _x86\_64_ 이미지를 사용하는 것이 좋습니다.
1. Emulated Performance에서 **Hardware - GLES 2.0**를 선택해
[hardware acceleration](https://developer.android.com/studio/run/emulator-acceleration.html)를 활성화 하세요. 
1. AVD 구성이 올바른지 확인하고 **Finish**를 선택하십시오.

   더 자세한 내용은 [Managing AVDs](https://developer.android.com/studio/run/managing-avds.html)를 확인해 주세요.
1. Android 가상 장치 관리자에서 도구 모음의 **Run**을 클릭합니다. 에뮬레이터가 시작되고 선택한 OS 버전 및 장치에 대한 기본 캔버스가 표시됩니다.
1. `flutter run`로 app을 시작합니다. 연결된 장치 이름은 `<platform>에 생성된 Android SDK`입니다. _platform_ 은 x86과 같은 칩 제품군입니다.
