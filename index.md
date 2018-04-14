---
title: Flutter - Beautiful native apps in record time
layout: page
homepage: true
hide_title: true
---

<div class="homepage__illustration">
    <h1 class="homepage__illustration--text">
        <span>Flutter Beta 2가 이제 사용 가능합니다!</span>
        &nbsp;
        <a href="https://medium.com/flutter-io/https-medium-com-flutter-io-announcing-flutters-beta-2-c85ba1557d5e">더 알아보기</a>.
    </h1>
    <img src="images/homepage/header-illustration.png" 
         class="homepage__illustration--image"
         alt="Illustration with a mobile phone, a pencil, and an abstract drawing of widgets.">
</div>

<section class="homepage__key_points card">
    <h1 class="homepage__title">
        빠른시간에 아름다운 native app을 만드세요
    </h1>

    <div class="homepage__tagline">
    Flutter는 iOS 및 Android에서 고품질 네이티브 인터페이스를 만들기 위한 Google의 모바일 UI 프레임 워크입니다.
    Flutter는 기존 코드와 함께 작동하며 전 세계 개발자와 조직에서 사용하며 무료이고, 오픈 소스입니다.
    </div>

    <div class="homepage__button_row">
    <a href="/get-started/install/" class="get-started-button">시작하기</a>
    </div>

    <div class="key-points">

        <div class="homepage__key_point">
            <div class="homepage__key_point_title">빠른 개발</div>

            <p>
            밀리세컨 단위로 app이 Hot Reload 됩니다.
            풍부한 사용자 정의 위젯을 사용하여 단 몇 분만에 기본 인터페이스를 구축하십시오.
            </p>
        </div>

        <div class="homepage__key_point">
            <div class="homepage__key_point_title">표현적이고 유연한 UI</div>

            <p>
            native end-user의 경험에 초점을 맞춰 신속하게 기능을 제공합니다.
            계층화 된 아키텍처로 완벽한 사용자 정의가 가능하므로 매우 빠른 렌더링과 표현력이 풍부하고 유연한 설계가 가능합니다.
            </p>
        </div>

        <div class="homepage__key_point">
            <div class="homepage__key_point_title">Native 성능</div>

            <p>
            Flutter의 위젯은 스크롤링, 탐색, 아이콘 및 글꼴과 같은 중요한 플랫폼의 차이점을 모두 포함하여 iOS 및 Android에서 완전한 성능을 제공합니다.
            </p>
        </div>

    </div>
</section>

<section class="homepage__hot_reload card">
    <h1>빠른 개발</h1>

    <p>
        Flutter의 <em>hot reload</em>는 빠르고 쉽게 실험하고, UI를 작성하고, 기능을 추가하고, 버그를 빠르게 수정하는 데 도움이됩니다.
        iOS 및 Android 용 에뮬레이터, 시뮬레이터 및 하드웨어에서 상태를 잃지 않고 2 초 미만의 reload 시간을 경험하십시오.
    </p>

    <div class="hot-reload-gif-container">
        <img src="/images/intellij/hot-reload.gif" class="hot-reload-gif" alt="Make a change in your code, and your app is changed instantly.">
    </div>
</section>

<section class="homepage__beautiful_uis card ">
    <h1>표현적이고, 아름다운 UI</h1>

    <p>
    Flutter에 내장 된 아름다운 Material Design 및 Cupertino (iOS 향) 위젯, 풍부한 모션 API,  자연스러운 스크롤링 및 플랫폼 인식으로 사용자를 즐겁게 합니다.
    </p>

    <div class="screenshot-list">
        <img class="screenshot" src="/images/homepage/screenshot-1.png" width="270" height="480" alt="Brand-first shopping design">
        <img class="screenshot" src="/images/homepage/screenshot-2.png" width="270" height="480" alt="Fitness app design">
        <img class="screenshot" src="/images/homepage/screenshot-3.png" width="270" height="480" alt="Contact app design">
        <img class="screenshot" src="/images/homepage/ios-friendlychat.png" width="270" height="480" alt="iOS chat app design">
    </div>

    <p>
    <a href="/widgets/">widget catalog</a>를 확인하세요.
    </p>
</section>

<section class="homepage__reactive_framework card">
    <h1>현대적이고, 반응적인 프레임워크</h1>

    <p>
    Flutter의 현대적인 반응형 프레임워크(reactive framework)와 다양한 플랫폼, 레이아웃 및 기초 위젯으로 UI를 손쉽게 작성할 수 있습니다.
    2D, 애니메이션, 제스처, 효과 등을위한 강력하고 유연한 API를 사용하여 어려운 UI 문제를 해결하세요.
    </p>

{% prettify dart %}
class CounterState extends State<Counter> {
  int counter = 0;

  void increment() {
    // Tells the Flutter framework that state has changed,
    // so the framework can run build() and update the display.
    setState(() {
      counter++;
    });
  }

  Widget build(BuildContext context) {
    // This method is rerun every time setState is called.
    // The Flutter framework has been optimized to make rerunning
    // build methods fast, so that you can just rebuild anything that
    // needs updating rather than having to individually change
    // instances of widgets.
    return new Row(
      children: <Widget>[
        new RaisedButton(
          onPressed: increment,
          child: new Text('Increment'),
        ),
        new Text('Count: $counter'),
      ],
    );
  }
}
{% endprettify %}

    <p>
    <a href="/widgets/">widget catalog</a>를 살펴보고 <a href="/widgets-intro/">reactive framework</a>에 대해 자세히 알아보세요.
    </p>

</section>

<section class="homepage__interop card">
    <h1>native 기능과 SDK에 접근</h1>

    <p>
    플랫폼 API, 3rd party SDK 및 native code를 사용하여 앱을 완성하십시오. 
    Flutter를 사용하면 기존 Java, Swift 및 ObjC 코드를 재사용하고 iOS 및 Android에서 native 기능 및 SDK에 액세스 할 수 있습니다.
    </p>

    <p>
    플랫폼 기능에 쉽게 액세스 할 수 있습니다. 여기 <a href="https://github.com/flutter/flutter/tree/master/examples/platform_channel">interop example</a>에 대한 snippet이 있습니다:
    </p>

{% prettify dart %}
Future<Null> getBatteryLevel() async {
  var batteryLevel = 'unknown';
  try {
    int result = await methodChannel.invokeMethod('getBatteryLevel');
    batteryLevel = 'Battery level: $result%';
  } on PlatformException {
    batteryLevel = 'Failed to get battery level.';
  }
  setState(() {
    _batteryLevel = batteryLevel;
  });
}
{% endprettify %}

    <p>
    <a href="/using-packages/">packages</a> 사용 방법이나 <a href="/platform-channels/">platform channels</a> 방법을 배우고 native code, API 및 SDK에 액세스하세요.
    </p>

</section>

<section class="homepage__features card">
    <h1>통합 app 개발</h1>

    <p>
    Flutter에는 iOS 및 Android에서 아이디어를 쉽게 사용할 수 있도록 도와주는 도구와 라이브러리가 있습니다.
    모바일 개발 경험이 없다면 Flutter는 아름다운 모바일 앱을 쉽고 빠르게 만들 수 있습니다.
    숙련 된 iOS 개발자 또는 Android 개발자 인 경우 Flutter를 사용하여 기존 Java / ObjC / Swift의 상당 부분을 활용할 수 있습니다.
    </p>

    <div class="feature-lists">

        <div class="feature-list-group">
            <h3>Build</h3>

            <h4>Beautiful app UIs</h4>

                <ul>
                    <li>Rich 2D GPU-accelerated APIs</li>
                    <li>Reactive framework</li>
                    <li>Animation/motion APIs</li>
                    <li>Material Components and Cupertino widgets</li>
                </ul>

            <h4>Fluid coding experience</h4>

            <ul>
                <li>Sub-second, stateful hot reload</li>
                <li>IntelliJ: refactor, code completion, etc</li>
                <li>Dart language and core libs</li>
                <li>Package manager</li>
            </ul>

            <h4>Full-features apps</h4>

            <ul>
                <li>Interop with mobile OS APIs &amp; SDKs</li>
                <li>Maven/Java</li>
                <li>Cocoapods/ObjC/Swift</li>
            </ul>
        </div>

        <div class="feature-list-group">
            <h3>Optimize</h3>

            <h4>Test</h4>

            <ul>
                <li>Unit testing</li>
                <li>Integration testing</li>
                <li>On-device testing</li>
            </ul>

            <h4>Debug</h4>

            <ul>
                <li>IDE debugger</li>
                <li>Web-based debugger</li>
                <li>async/await aware</li>
                <li>Expression evaluator</li>
            </ul>

            <h4>Profile</h4>

            <ul>
                <li>Timeline</li>
                <li>CPU and memory</li>
                <li>In-app perf charts</li>
            </ul>
        </div>

        <div class="feature-list-group">
            <h3>Deploy</h3>

            <h4>Compile</h4>

            <ul>
                <li>Native ARM code</li>
                <li>Dead code elimination</li>
            </ul>

            <h4>Distribution</h4>

            <ul>
                <li>App Store</li>
                <li>Play Store</li>
            </ul>
        </div>

    </div>

    <p>
    Learn more about what makes Flutter special in the
    <a href="/technical-overview/">technical overview</a>.
    </p>
</section>

<section class="homepage__try_flutter card">

    <div class="homepage__try_today">
    오늘, Flutter를 사용해보세요. 시작은 쉽습니다.</div>

    <div class="homepage__button_row">
    <a href="/get-started/install/" class="get-started-button">시작하기</a>
    </div>

</section>

