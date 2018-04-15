## Flutter SDK 구하기 {#get-sdk}

1. Flutter SDK의 최신 베타 릴리스를 얻으려면 다음 설치 번들을 다운로드하세요.(다른 릴리스 채널 및 이전 빌드의 경우 [SDK
archive](/sdk-archive/) 페이지를 확인해 주세요.)
{% if page.url contains "linux" %}
    * [(loading...)](#){:.download-latest-link-linux}
{% else %}
    * [(loading...)](#){:.download-latest-link-macos}
{% endif %}<br><br>
1. 원하는 위치에 파일 압축을 풀어주세요. 예..:
    {% commandline %}
    cd ~/development
{% if page.url contains "linux" %}
    tar xf ~/Downloads/<span class="download-latest-link-filename-linux">flutter_linux_xxx.tar.xz</span>
{% else %}
    unzip ~/Downloads/<span class="download-latest-link-filename-macos">flutter_macos_xxx.zip</span>
{% endif %}
    {% endcommandline %}

1. path에 `flutter`를 추가해주세요:
    {% commandline %}
    export PATH=`pwd`/flutter/bin:$PATH
    {% endcommandline %}

위의 명령은 PATH 변수를 현재 터미널 창에 대해 임시로 설정합니다. Flutter를 경로에 영구적으로 추가하려면 [Update your path](#update-your-path)를 참조하세요.

이제 Flutter 명령을 실행할 준비가되었습니다!

기존 버전의 Flutter를 업데이트하려면 [Upgrading Flutter](/upgrading/)를 참조하십시오.

### flutter doctor 실행하기

다음 명령을 실행하여 설치를 완료하기 위해 설치할 종속성이 있는지 확인하세요:

{% commandline %}
flutter doctor
{% endcommandline %}

이 명령은 환경설정을 점검하고 터미널 창에 리포트를 표시합니다. Dart SDK는 Flutter와 번들로 제공되고, 별도로 Dart를 설치할 필요가 없습니다. 수행해야 할 설치 또는 추가 작업이 필요한 소프트웨어가 있는지 출력을 주의깊게 확인하세요.(**굵은** 문자를 확인하세요).

예를 들면:
<pre>
[-] Android toolchain - develop for Android devices
    • Android SDK at /Users/obiwan/Library/Android/sdk
    <strong>✗ Android SDK is missing command line tools; download from https://goo.gl/XxQghQ</strong>
    • Try re-installing or updating your Android SDK,
      visit https://flutter.io/setup/#android-setup for detailed instructions.
</pre>

다음 섹션에서는 이러한 작업을 수행하고 설치 프로세스를 완료하는 방법에 대해 설명합니다.

잘못된 dependency를 설치했으면 `flutter doctor` 명령을 다시 실행하여 모든 것을 올바르게 설정했는지 확인하십시오.

`flutter` 도구는 Google Analytics를 사용하여 기능 사용통계 및 기본 오류레포트를 익명으로 보고합니다. 이 데이터는 시간이 지남에 따라 Flutter 도구를 개선하는 데 사용됩니다.
Analytics는 첫 번째 실행시 또는 `flutter config`과 관련된 모든 실행시에는 전송되지 않으므로 데이터를 보내기 전에 애널리틱스를 사용하지 않도록 선택할 수 있습니다. 보고기능을 사용하지 않으려면 `flutter config --no-analytics` 를 입력하고 현재 설정을 표시하려면 `flutter config`를 입력하십시오.Google의 개인 정보 취급 방침을 참조하세요. : www.google.com/intl/ko/policies/privacy
{: .alert-warning}
