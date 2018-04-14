---
layout: tutorial
title: Write Your First Flutter App
permalink: /get-started/codelab/
---

<figure class="right-figure" style="max-width: 260px; padding-right: 10px">
    <img src="images/startup-namer-app.gif"
         alt="Animated GIF of the app that you will be building."
         style="border: 10px solid #333; border-radius: 10px; margin-bottom: 10px" >
</figure>

이것은 첫 번째 Flutter 앱을 만드는 방법입니다.
변수, 루프 및 조건과 같은 객체 지향 코드 및 기본 프로그래밍 개념에 익숙한 경우에 이 자습서를 완료 할 수 있습니다.
Dart 또는 모바일 프로그래밍의 경험은 필요하지 않습니다.

{% comment %}
TODO: (maybe, but later)
- Retake screenshots on the Android emulator? (Tao)
  Maybe alternate between Android and iOS emulators?
- Somehow cross link from code to text so people can restart
  and find their place more easily? (Tao)
{% endcomment %}

* TOC
{:toc}

<p class="h2-like">무엇을 만들것인가</p>
스타트업 회사에 제안 된 이름을 생성하는 간단한 모바일 앱을 구현해 봅니다.
사용자는 이름을 선택하고 선택을 해제하여 가장 좋은 이름을 저장할 수 있습니다.
이 코드는 한 번에 10개의 이름을 생성합니다. 사용자가 스크롤하면 새로운 이름 배치가 생성됩니다. 사용자는 앱 표시 줄 오른쪽 상단에있는 목록 아이콘을 탭하여 즐겨찾기 된 이름만 나열된 새 경로로 이동할 수 있습니다.

이 애니메이션 GIF는 완성 된 앱의 작동 방식을 보여줍니다.

<div class="whats-the-point" markdown="1">

<b> <a id="whats-the-point" class="anchor" href="#whats-the-point" aria-hidden="true"><span class="octicon octicon-link"></span></a>배우게 될 것:</b>

* Flutter app의 기본구조.
* 패키지를 찾아서 사용하여 기능을 확장합니다.
* 더 빠른 개발 사이클을 위해 hot reload를 사용합니다. 
* 상태위젯을 구현하는 방법.
* 무한한 lazily loaded 목록을 만드는 법.
* 두 번째 화면을 만들고 탐색하는 방법.
* 테마를 사용하여 app의 모양을 변경하는 방법.

</div>

<div class="whats-the-point" markdown="1">

<b> <a id="whats-the-point" class="anchor" href="#whats-the-point" aria-hidden="true"><span class="octicon octicon-link"></span></a>사용할 것들:</b>

다음을 설치해야 합니다:

<ul markdown="1">
<li markdown="1"> Flutter SDK<br>
    Flutter SDK에는 Flutter의 엔진, 프레임 워크, 위젯, 도구 및 Dart SDK가 포함되어 있습니다. 이 codelab은 v0.1.4 이상이 필요합니다.
</li>
<li markdown="1"> Android Studio IDE<br>
    이 codelab에는 Android Studio IDE가 있지만 다른 IDE를 사용하거나 명령 줄에서 작업 할 수 있습니다.
</li>
<li markdown="1"> 당신의 IDE의 Plugin<br>
    Flutter와 Dart 플러그인은 IDE에 별도로 설치해야합니다. Android Studio 외에 Flutter 및 Dart 플러그인도 [VS Code](https://code.visualstudio.com/download) 및 [IntelliJ](https://www.jetbrains.com/idea/download/#section=mac) IDE에서 사용할 수 있습니다.
</li>
</ul>

환경 설정 방법에 대한 정보는 [Flutter 설치 및 설정](/get-started/install/)을 참조하십시오.


</div>

# Step 1: Flutter 시작 app 만들기

[첫 Flutter app 시작하기](/get-started/test-drive/#create-app)의 지침에 따라 간단한 템플릿 기반 Flutter app을 만듭니다. 프로젝트의 이름을 **startup_namer** 로 지정하십시오 (_myapp_ 대신). 완료된 앱을 만들려면 이 시작 앱을 수정해야합니다.

이 codelab에서는 다트 코드에 있는 **lib/main.dart** 를 주로 편집하게됩니다.


<aside class="alert alert-success" markdown="1">
<i class="fa fa-lightbulb-o"> </i> **Tip:**
앱에 코드를 붙여 넣을 때 들여 쓰기가 왜곡 될 수 있습니다. <br>
이 문제는 Flutter 도구를 사용하여 자동으로 수정할 수 있습니다:

* Android Studio / IntelliJ IDEA: 마우스 오른클릭 후 **Reformat Code with dartfmt** 를 선택합니다.
* VS Code: 마우스 오른클릭 후 **Format Document** 를 선택합니다.
* Terminal: `flutter format <filename>` 를 실행합니다.
</aside>

<ol markdown="1">

<li markdown="1"> `lib/main.dart` 를 변경합니다.<br>
    **lib/main.dart**의 모든 코드를 삭제합니다. 그리고 화면 중앙에 "Hello World"를 표시하는 아래의 코드로 바꿉니다.

{% prettify dart %}
import 'package:flutter/material.dart';

void main() => runApp(new MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new MaterialApp(
      title: 'Welcome to Flutter',
      home: new Scaffold(
        appBar: new AppBar(
          title: new Text('Welcome to Flutter'),
        ),
        body: new Center(
          child: new Text('Hello World'),
        ),
      ),
    );
  }
}
{% endprettify %}
</li>

<li markdown="1"> app을 실행하면 다음 화면이 나타납니다.

<center><img src="images/hello-world-screenshot.png" alt="screenshot of hello world app"></center>
</li>
</ol>

<p class="h2-like">관찰</p>

  <ul markdown="1">
  <li markdown="1"> 이 예제는 Material app을 만듭니다. 
      [Material](https://material.io/guidelines/)은 모바일과 웹에서 표준인 시각적인 디자인 언어 입니다. Flutter는 다양한 Material 위젯을 제공합니다.
  </li>
  <li markdown="1"> main 메소드는 굵은 화살표 (`=>`) 표기법을 지정하는데, 이는 한 줄짜리 함수 나 메소드에 단축으로 사용됩니다.
  </li>
  <li markdown="1"> 이 앱은 StatelessWidget을 확장하여 앱 자체를 위젯으로 만듭니다. Flutter에서는 거의 모든 위젯이 alignment, 패딩 및 레이아웃을 포함한 위젯입니다.
  </li>
  <li markdown="1"> Material 라이브러리의 Scaffold 위젯은 기본 앱 표시 줄, 제목 및 홈 화면의 위젯 트리를 포함하는 본문 속성을 제공합니다. 위젯 하위 트리는 상당히 복잡 할 수 있습니다.
  </li>
  <li markdown="1"> 위젯의 주된 역할은 다른 하위 레벨 위젯의 관점에서 위젯을 표시하는 방법을 설명하는 `build()` 메소드를 제공하는 것입니다.
  </li>
  <li markdown="1"> 이 예제의 위젯 트리는 Text 자식 위젯을 포함하는 Center 위젯으로 구성됩니다.Center 위젯은 하위 트리를 화면 가운데로 맞춥니다.
  </li>
</ul>
{% comment %}
  Removing this for now. A) It might be confusing and B) the code as shown here is wrong.
  <li markdown="1"> Moving the “hello world” text into a separate widget,
      HelloWorld, results in an identical widget tree as the code above.
      (This code is informational only. You are starting with the Hello
      World code above.)

  <!-- skip -->
  {% prettify dart %}
  import 'package: flutter/material.dart';

  class MyApp extends StatelessWidget {
   @override
   Widget build(BuildContext context) {
     return new MaterialApp(
       title: 'Welcome to Flutter',
       home: new Scaffold(
         appBar: new AppBar(
           title: new Text('Welcome to Flutter'),
         ),
         body: new Center(
           child: new Text('Hello World')
         ),
       ),
     );
   }
  }
  {% endprettify %}

  Update with this code:

  class HelloWorld extends StatelessWidget {
   @override
   Widget build(BuildContext context) {
     return new Center(
       child: new Text('Hello World'),
     );
   }
  }
  </li>
{% endcomment %}

---

# Step 2: 외부 패키지 사용하기

이번 단계에서는 **english_words** 라는 open-source package를 사용하기 시작합니다. 이 패키지에는 가장 많이 사용되는 영어 단어 몇 가지와 약간의 유틸리티 함수가 포함되어 있습니다.

[pub.dartlang.org](https://pub.dartlang.org/flutter/)에서 [english_words](https://pub.dartlang.org/packages/english_words) 패키지와 다른 많은 오픈 소스 패키지를 찾을 수 있습니다.

<ol markdown="1">

<li markdown="1"> pubspec 파일은 Flutter app의 asset을 관리합니다. **pubspec.yaml**에서 dependencies 목록에 **english_words** (3.1.0 이상)를 추가하십시오. 아래에서 새로운 줄이 강조 표시됩니다.

<!-- skip -->
{% prettify dart %}
dependencies:
  flutter:
    sdk: flutter

  cupertino_icons: ^0.1.0
  [[highlight]]english_words: ^3.1.0[[/highlight]]
{% endprettify %}
</li>

<li markdown="1"> Android Studio의 편집기보기에서 pubspec을 보면서 오른쪽 상단에있는 **Packages get** 을 클릭합니다. 이 작업은 패키지를 프로젝트로 가져오게 됩니다. 콘솔에서는 아래와 같이 확인할 수 있습니다:

<!-- skip -->
{% prettify dart %}
flutter packages get
Running "flutter packages get" in startup_namer...
Process finished with exit code 0
{% endprettify %}
</li>

<li markdown="1"> **lib/main.dart** 에서 강조 표시된 행처럼 `english_words` import를 추가하세요:

<!-- skip -->
{% prettify dart %}
import 'package:flutter/material.dart';
[[highlight]]import 'package:english_words/english_words.dart';[[/highlight]]
{% endprettify %}

Android Studio에서 입력 할 때, Android Studio는 import를 할 라이브러리에 대한 제안사항을 제공합니다. 회색으로 보여지는 import 문자열은 import된 라이브러리가 사용되지 않고 있음을 알려줍니다.
</li>

<li markdown="1"> "Hello World" 문자열을 사용하는 대신 English words 패키지를 사용하여 텍스트를 생성하세요.

<aside class="alert alert-success" markdown="1">
<i class="fa fa-lightbulb-o"> </i> **Tip:**
"Pascal case" ("upper camel case"로 알려진)는 첫 번째 문자열을 포함하여 문자열의 각 단어가 대문자로 시작함을 의미합니다. 그래서, "uppercamelcase" 는 
"UpperCamelCase" 가 됩니다.
</aside>

아래에 강조 표시된대로 다음과 같이 변경하세요:

<!-- skip -->
{% prettify dart %}
import 'package:flutter/material.dart';
import 'package:english_words/english_words.dart';

void main() => runApp(new MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    [[highlight]]final wordPair = new WordPair.random();[[/highlight]]
    return new MaterialApp(
      title: 'Welcome to Flutter',
      home: new Scaffold(
        appBar: new AppBar(
          title: new Text('Welcome to Flutter'),
        ),
        body: new Center(
          //child: new Text([[highlight]]'Hello World'[[/highlight]]), // Replace the highlighted text...
          child: new Text([[highlight]]wordPair.asPascalCase[[/highlight]]),  // With this highlighted text.
        ),
      ),
    );
  }
}
{% endprettify %}
</li>

<li markdown="1"> 앱이 실행중인 경우 hot reload 버튼 (<img src="images/hot-reload-button.png" alt="lightning bolt icon">)을 사용하여 실행중인 앱을 업데이트합니다. hot reload를 클릭하거나 프로젝트를 저장할 때마다 실행중인 앱에서 임의로 선택한 다른 단어 쌍을 볼 수 있습니다. 이는 MaterialApp에서 렌더링이 필요하거나 Flutter Inspector에서 플랫폼을 토글 할 때마다 실행되는 build 메소드 내에서 단어 페어링이 생성되기 때문입니다.

<center><img src="images/step2-screenshot.png" alt="screenshot at completion of second step"></center>
</li>

</ol>

<p class="h2-like">문제점?</p>

앱이 제대로 실행되지 않는 경우 오타를 찾으세요. 필요하다면, 다음 링크의 코드를 사용해 보세요.

* [**pubspec.yaml**](https://gist.githubusercontent.com/Sfshaza/bb51e3b7df4ebbf3dfd02a4a38db2655/raw/57c25b976ec34d56591cb898a3df0b320e903b99/pubspec.yaml)
(**pubspec.yaml** file은 다시 변경되지 않습니다.)
* [**lib/main.dart**](https://gist.githubusercontent.com/Sfshaza/bb51e3b7df4ebbf3dfd02a4a38db2655/raw/57c25b976ec34d56591cb898a3df0b320e903b99/main.dart)

---

# Step 3: 상태기반 위젯 추가

상태가 <em>없는</em> 위젯은 불변이므로, 해당 속성을 변경할 수 없음을 뜻하며, 모든 값은 최종값입니다.

상태<em>기반</em> 위젯은 위젯 lifetime 동안 변경될 수 있는 상태를 유지합니다. 상태기반 위젯을 구현하려면 최소 두개의 class가 필요합니다: 1) a StatefulWidget class
that creates an instance of 2) a State class. StatefulWidget 클래스 자체는 불변이지만 State 클래스는 위젯 수명 기간 동안 지속됩니다.

이 단계에서, State 클래스 인 RandomWordsState를 생성하는 상태기반 위젯인, RandomWords를 추가합니다. State 클래스는 결국 위젯에 대해 제안되고 좋아하는 단어 쌍을 유지합니다.

<ol markdown="1">
<li markdown="1"> main.dart에 상태기반 RandomWords 위젯을 추가 합니다. 이것은 MyApp 외부의 파일에서 어디든 갈 수 있지만, 이 해결책은 파일의 맨 아래에 배치합니다. RandomWords 위젯은 State 클래스를 생성하는 것 외에는 거의하지 않습니다:

<!-- skip -->
{% prettify dart %}
class RandomWords extends StatefulWidget {
  @override
  createState() => new RandomWordsState();
}
{% endprettify %}
</li>

<li markdown="1"> RandomWordsState 클래스 추가합니다. 대부분의 앱 코드는 RandomWords 위젯의 상태를 유지하는 클래스에 상주합니다. This class will save the generated word pairs,
    which grow infinitely as the user scrolls, and also favorite
    word pairs, as the user adds or removes them from the list by
    toggling the heart icon.

이 클래스는 비트 단위로 빌드합니다. 시작하려면, 강조 표시된 텍스트를 추가하여 최소 클래스를 만듭니다:

<!-- skip -->
{% prettify dart %}
[[highlight]]class RandomWordsState extends State<RandomWords> {[[/highlight]]
[[highlight]]}[[/highlight]]
{% endprettify %}
</li>

<li markdown="1"> 상태 클래스가 추가된 후, IDE는 클래스는 build 메서드가 빠져있는 걸 알려줍니다. 다음으로 단어 생성 코드를 MyApp에서 RandomWordsState로 이동하여 단어 쌍을 생성하는 기본 build 메서드를 추가합니다.

강조표시된 텍스트와 같이, RandomWordState에 build 메서드를 추가합니다:

<!-- skip -->
{% prettify dart %}
class RandomWordsState extends State<RandomWords> {
  [[highlight]]@override[[/highlight]]
  [[highlight]]Widget build(BuildContext context) {[[/highlight]]
    [[highlight]]final wordPair = new WordPair.random();[[/highlight]]
    [[highlight]]return new Text(wordPair.asPascalCase);[[/highlight]]
  [[highlight]]}[[/highlight]]
}
{% endprettify %}
</li>

<li markdown="1"> 아래에서 강조표시된 변경사항을 적용하여 MyApp에서 단어 생성 코드를 제거하십시오.

<!-- skip -->
{% prettify dart %}
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    [[strike]]final wordPair = new WordPair.random();[[/strike]]  // Delete this line

    return new MaterialApp(
      title: 'Welcome to Flutter',
      home: new Scaffold(
        appBar: new AppBar(
          title: new Text('Welcome to Flutter'),
        ),
        body: new Center(
          //child: new [[highlight]]Text(wordPair.asPascalCase),[[/highlight]] // Change the highlighted text to...
          child: new [[highlight]]RandomWords(),[[/highlight]] // ... this highlighted text
        ),
      ),
    );
  }
}
{% endprettify %}
</li>

</ol>

앱을 다시 시작합니다. hot reload를 시도 시, 경고가 표시 될 수 있습니다:

{% prettify sh %}
Reloading...
Not all changed program elements ran during view reassembly; consider
restarting.
{% endprettify %}

거짓양성(false positive)일 수도 있지만, 변경 사항이 앱의 UI에 반영되었는지 확인하기 위해 다시 시작하는 것이 좋습니다.

app을 hot reload 하거나 저장할 때마다 단어가 페어링되어 이전과 같이 작동해야 합니다.

<center><img src="images/step3-screenshot.png" alt="screenshot at completion of third step"></center>

<p class="h2-like">문제점?</p>

app이 제대로 실행되지 않는다면, 다음 링크의 코드를 사용해 보세요:

* [**lib/main.dart**](https://gist.githubusercontent.com/Sfshaza/d7f13ddd8888556232476be8578efe40/raw/329c397b97309ce99f834bf70ebb90778baa5cfe/main.dart)

---

# Step 4: 무한 스크롤 ListView 만들기

이 단계에서는 RandomWordsState를 확장하여 단어 쌍 list를 생성하고 표시합니다. 사용자가 스크롤 할 때 ListVie 위젯에 표시된 list는 무한히 커집니다. ListView의 `builder` factory 생성자를 사용하면 필요할 때 list view를 lazy 하게 build 할 수 있습니다.

<ol markdown="1">

<li markdown="1"> 단어 쌍을 저장하기 위해 `_suggestions` list를 RandomWordsState class를 추가하세요. The variable begins with
an underscore (`_`)&mdash;prefixing an identifier with an underscore enforces
privacy in the Dart language.

또한 글꼴 크기를 더 크게 지정하려면 `biggerFont` 변수를 추가합니다.

<!-- skip -->
{% prettify dart %}
class RandomWordsState extends State<RandomWords> {
  [[highlight]]final _suggestions = <WordPair>[];[[/highlight]]

  [[highlight]]final _biggerFont = const TextStyle(fontSize: 18.0);[[/highlight]]
  ...
}
{% endprettify %}
</li>

<li markdown="1"> RandomWordsState 클래스에 `_buildSuggestions()` 함수를 추가하세요. 이 메서드는 제안된 단어 쌍을 표시하는 ListView를 build 합니다.

ListView 클래스는 익명 함수로 지정된 factory builder 및 콜백 함수 인 builder property인 `itemBuilder`를 제공합니다.
함수에 두 개의 매개 변수&mdash; 즉 BuildContext와 행 반복자, `i` 가 전달됩니다. 이 이터레이터는 0으로 시작하여 함수가 호출 될 때마다, 제안 된 모든 단어 쌍에 대해 한 번씩 증가합니다. 이 모델은 사용자가 스크롤 할 때 제안된 list를 무한대로 확장 할 수 있게 허용합니다.

아래에 강조 표시된 행을 추가하세요:

<!-- skip -->
{% prettify dart %}
class RandomWordsState extends State<RandomWords> {
  ...
  [[highlight]]Widget _buildSuggestions() {[[/highlight]]
    [[highlight]]return new ListView.builder([[/highlight]]
      [[highlight]]padding: const EdgeInsets.all(16.0),[[/highlight]]
      // The itemBuilder callback is called once per suggested word pairing,
      // and places each suggestion into a ListTile row.
      // For even rows, the function adds a ListTile row for the word pairing.
      // For odd rows, the function adds a Divider widget to visually
      // separate the entries. Note that the divider may be difficult
      // to see on smaller devices.
      [[highlight]]itemBuilder: (context, i) {[[/highlight]]
        // Add a one-pixel-high divider widget before each row in theListView.
        [[highlight]]if (i.isOdd) return new Divider();[[/highlight]]

        // The syntax "i ~/ 2" divides i by 2 and returns an integer result.
        // For example: 1, 2, 3, 4, 5 becomes 0, 1, 1, 2, 2.
        // This calculates the actual number of word pairings in the ListView,
        // minus the divider widgets.
        [[highlight]]final index = i ~/ 2;[[/highlight]]
        // If you've reached the end of the available word pairings...
        [[highlight]]if (index >= _suggestions.length) {[[/highlight]]
          // ...then generate 10 more and add them to the suggestions list.
          [[highlight]]_suggestions.addAll(generateWordPairs().take(10));[[/highlight]]
        [[highlight]]}[[/highlight]]
        [[highlight]]return _buildRow(_suggestions[index]);[[/highlight]]
      [[highlight]]}[[/highlight]]
    [[highlight]]);[[/highlight]]
  [[highlight]]}[[/highlight]]
}
{% endprettify %}
</li>

<li markdown="1"> `_buildSuggestions` 함수는 단어 쌍당 한 번 `_buildRow` 를 호출합니다. 이 함수는 ListTile에 각 새로운 쌍을 표시하여 다음 단계에서 행을보다 매력적으로 만듭니다.

RandomWordsState에 `_buildRow` 함수를 추가합니다:

<!-- skip -->
{% prettify dart %}
class RandomWordsState extends State<RandomWords> {
  ...

  [[highlight]]Widget _buildRow(WordPair pair) {[[/highlight]]
    [[highlight]]return new ListTile([[/highlight]]
      [[highlight]]title: new Text([[/highlight]]
        [[highlight]]pair.asPascalCase,[[/highlight]]
        [[highlight]]style: _biggerFont,[[/highlight]]
      [[highlight]]),[[/highlight]]
    [[highlight]]);[[/highlight]]
  [[highlight]]}[[/highlight]]
}
{% endprettify %}
</li>

<li markdown="1"> 단어 생성 라이브러리를 직접 호출하는 것보다는, `_buildSuggestions()`을 사용하도록 RandomWordsState의 build 메서드를 update 하십시오. 강조 표시된 변경사항을 작성하세요:

<!-- skip -->
{% prettify dart %}
class RandomWordsState extends State<RandomWords> {
  ...
  @override
  Widget build(BuildContext context) {
    [[strike]]final wordPair = new WordPair.random();[[/strike]] // Delete these two lines.
    [[strike]]return new Text(wordPair.asPascalCase);[[/strike]]
    [[highlight]]return new Scaffold ([[/highlight]]
      [[highlight]]appBar: new AppBar([[/highlight]]
        [[highlight]]title: new Text('Startup Name Generator'),[[/highlight]]
      [[highlight]]),[[/highlight]]
      [[highlight]]body: _buildSuggestions(),[[/highlight]]
    [[highlight]]);[[/highlight]]
  }
  ...
}
{% endprettify %}
</li>

<li markdown="1"> MyApp의 build 메서드를 update 하세요. MyApp에서 Scaffold와 AppBar 인스턴스를 제거합니다. 이것들은 RandomWordsState에서 관리될 것입니다. RandomWordsState은 사용자가 다음 단계에, 한 화면에서 다른 화면으로 이동할 때 app bar에서 경로 이름을 변경하는 것을 더 쉽게 합니다.

app이 제대로 실행되지 않는다면, 다음 링크의 코드를 사용해 보세요:

<!-- skip -->
{% prettify dart %}
class MyApp extends StatelessWidget {
  @override
  [[highlight]]Widget build(BuildContext context) {[[/highlight]]
    [[highlight]]return new MaterialApp([[/highlight]]
      [[highlight]]title: 'Startup Name Generator',[[/highlight]]
      [[highlight]]home: new RandomWords(),[[/highlight]]
    [[highlight]]);[[/highlight]]
  [[highlight]]}[[/highlight]]
}
{% endprettify %}
</li>

</ol>

app을 재구동하세요. 단어 페어링의 list가 표시되어야합니다. 계속 아래로 스크롤 하면, 새로운 단어 쌍이 계속해서 표시됩니다.

<center><img src="images/step4-screenshot.png" alt="screenshot at completion of fourth step"></center>

<p class="h2-like">문제점?</p>

app이 제대로 실행되지 않는다면, 다음 링크의 코드를 사용해 보세요:

* [**lib/main.dart**](https://gist.githubusercontent.com/Sfshaza/d6f9460a04d3a429eb6ac0b0f07da564/raw/34fe240f4122435c871bb737708ee0357741801c/main.dart)

---

# Step 5: 상호작용 추가하기

이 단계에서는 탭이 가능한 하트 아이콘을 각 행에 추가합니다. 사용자가 목록의 항목을 탭하여 "즐겨 찾기"상태로 전환하면 해당 단어 쌍이 저장된 즐겨 찾기 모음에 추가되거나 제거됩니다.

<ol markdown="1">
<li markdown="1"> RandomWordsState에 `_saved` Set을 추가합니다. 이 Set은 사용자가 즐겨찾기된 단어 한 쌍을 저장합니다. 제대로 구현 된 Set은 중복 된 항목을 허용하지 않기 때문에 Set을 List보다 우선시 합니다.

<!-- skip -->
{% prettify dart %}
class RandomWordsState extends State<RandomWords> {
  final _suggestions = <WordPair>[];

  [[highlight]]final _saved = new Set<WordPair>();[[/highlight]]

  final _biggerFont = const TextStyle(fontSize: 18.0);
  ...
}
{% endprettify %}
</li>

<li markdown="1"> `_buildRow` 함수에서 `alreadySaved` check를 추가하여 단어 쌍이 이미 즐겨찾기에 추가되지 않았는지 확인하세요.

<!-- skip -->
{% prettify dart %}
  Widget _buildRow(WordPair pair) {
    [[highlight]]final alreadySaved = _saved.contains(pair);[[/highlight]]
    ...
  }
{% endprettify %}
</li>

<li markdown="1"> 또한 `_buildRow()`에서 하트 모양의 아이콘을 ListTiles에 추가하여 즐겨 찾기를 가능하게 합니다.

아래에 강조 표시된 행을 추가하세요:

<!-- skip -->
{% prettify dart %}
  Widget _buildRow(WordPair pair) {
    final alreadySaved = _saved.contains(pair);
    return new ListTile(
      title: new Text(
        pair.asPascalCase,
        style: _biggerFont,
      ),
      [[highlight]]trailing: new Icon([[/highlight]]
        [[highlight]]alreadySaved ? Icons.favorite : Icons.favorite_border,[[/highlight]]
        [[highlight]]color: alreadySaved ? Colors.red : null,[[/highlight]]
      [[highlight]]),[[/highlight]]
    );
  }
{% endprettify %}
</li>

<li markdown="1"> app을 재구동 하세요.각 행마다 하트를 볼 수 있지만, 아직 상호작용은 하지 않습니다.
</li>

<li markdown="1"> `_buildRow` 함수에서 이름 추천 타일을 탭이 가능하게 만드세요. 만약 단어 항목이 이미 즐겨찾기에 추가 된 경우라면, 다시 단어를 탭을 하면 즐겨 찾기에서 제거됩니다. 타일을 탭하게 되면, 함수는 `setState()` 를 호출하여 상태가 변경되었음을 프레임 워크에 알립니다.

아래에 강조 표현된 행을 추가하세요:

<!-- skip -->
{% prettify dart %}
  Widget _buildRow(WordPair pair) {
    final alreadySaved = _saved.contains(pair);
    return new ListTile(
      title: new Text(
        pair.asPascalCase,
        style: _biggerFont,
      ),
      trailing: new Icon(
        alreadySaved ? Icons.favorite : Icons.favorite_border,
        color: alreadySaved ? Colors.red : null,
      ),
      [[highlight]]onTap: () {[[/highlight]]
        [[highlight]]setState(() {[[/highlight]]
          [[highlight]]if (alreadySaved) {[[/highlight]]
            [[highlight]]_saved.remove(pair);[[/highlight]]
          [[highlight]]} else {[[/highlight]]
            [[highlight]]_saved.add(pair);[[/highlight]]
          [[highlight]]}[[/highlight]]
        [[highlight]]});[[/highlight]]
      [[highlight]]},[[/highlight]]
    );
  }
{% endprettify %}
</li>
</ol>

<aside class="alert alert-success" markdown="1">
<i class="fa fa-lightbulb-o"> </i> **Tip:**
Flutter의 반응형 프레임 워크는, `setState()` 를 호출하면 State 객체에 대한 build () 메서드가 호출되어 UI가 업데이트됩니다.
</aside>

app을 hot reload 합니다. 어떠한 타일도 즐겨찾기를 하거나 즐겨찾기를 해제할 수 있어야 합니다. 타일을 탭하는 것은 당신이 탭했던 곳에서 나오는 암묵적인 잉크 스플래시 애니메이션을 생성합니다.

<center><img src="images/step5-screenshot.png" alt="screenshot at completion of 5th step"></center>

<p class="h2-like">저점?</p>

app이 제대로 실행되지 않는다면, 다음 링크의 코드를 사용해 보세요:

* [**lib/main.dart**](https://gist.githubusercontent.com/Sfshaza/936ce0059029a8c6e88aaa826a3789cd/raw/a3065d5c681a81eff32f75a9cd5f4d9a5b24f9ff/main.dart)

---

# Step 6: 새로운 화면으로 이동

이 단계에서는 즐겨찾기를 표시하는 새 화면 (Flutter에 _route_라고 함)을 추가합니다. home 경로와 새 경로 사이를 탐색하는 방법을 배우게됩니다.

Flutter에서 Navigator는 app의 경로가 포함 된 스택을 관리합니다. Navigator의 스택으로 경로를 push하면 디스플레이가 해당 경로로 업데이트됩니다. Navigator의 스택에서 경로를 제거하면 디스플레이가 이전 경로로 돌아갑니다.

<ol markdown="1">
<li markdown="1"> RandomWordsState의 build 메서드에서 AppBar에 list 아이콘을 추가 합니다. 사용자가 list 아이콘을 클릭하면 즐겨찾기 항목이 포함 된 새 경로가 네비게이터로 푸시되고 아이콘이 표시됩니다.

<aside class="alert alert-success" markdown="1">
<i class="fa fa-lightbulb-o"> </i> **Tip:**
Some widget properties take a single widget (`child`), and other properties,
such as `action`, take an array of widgets (`children`),
as indicated by the square brackets (`[]`).
</aside>

아래에 build 메서드와 해당 action을 추가하세요:

<!-- skip -->
{% prettify dart %}
class RandomWordsState extends State<RandomWords> {
  ...
  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: new AppBar(
        title: new Text('Startup Name Generator'),
        [[highlight]]actions: <Widget>[[[/highlight]]
          [[highlight]]new IconButton(icon: new Icon(Icons.list), onPressed: _pushSaved),[[/highlight]]
        [[highlight]]],[[/highlight]]
      ),
      body: _buildSuggestions(),
    );
  }
  ...
}
{% endprettify %}
</li>

<li markdown="1"> `_pushSaved()` 함수를 RandomWordsState 클래스에 추가하세요.

<!-- skip -->
{% prettify dart %}
class RandomWordsState extends State<RandomWords> {
  ...
  [[highlight]]void _pushSaved() {[[/highlight]]
  [[highlight]]}[[/highlight]]
}
{% endprettify %}

app을 hot reload 하세요. list 아이콘에 app bar가 나타납니다. `_pushSaved` 함수가 비어 있기 때문에 탭을 하여도 아무 일도 생기지 않습니다.
</li>

<li markdown="1"> 사용자가 app bar의 list 아이콘을 탭하면 경로를 푸시하고 네비게이터의 스택으로 푸시합니다. 이 작업은 새 경로를 표시하도록 화면을 변경합니다.

새 페이지의 내용은 MaterialPageRoute의 `builder` 속성에 익명 함수로 작성됩니다.

Navigator.push에 호출을 추가하면, 강조 표시된 코드는 Navigator의 스택에 경로를 푸시합니다.

<!-- skip -->
{% prettify dart %}
  [[highlight]]void _pushSaved() {[[/highlight]]
    [[highlight]]Navigator.of(context).push([[/highlight]]
    [[highlight]]);[[/highlight]]
  [[highlight]]}[[/highlight]]
{% endprettify %}
</li>

<li markdown="1"> MaterialPageRoute 및 그 builder를 추가하세요. 지금은 ListTile 행을 생성하는 코드를 추가하세요. ListTile의 `divideTiles()` 메서드는 각 ListTile 사이에 가로 간격을 추가합니다. `분할된(divided)` 변수는 편의 함수에 의해리스트로 변환 된 마지막 행을 `toList()`로 유지합니다.

<!-- skip -->
{% prettify dart %}
  void _pushSaved() {
    Navigator.of(context).push(
      [[highlight]]new MaterialPageRoute([[/highlight]]
        [[highlight]]builder: (context) {[[/highlight]]
          [[highlight]]final tiles = _saved.map([[/highlight]]
            [[highlight]](pair) {[[/highlight]]
              [[highlight]]return new ListTile([[/highlight]]
                [[highlight]]title: new Text([[/highlight]]
                  [[highlight]]pair.asPascalCase,[[/highlight]]
                  [[highlight]]style: _biggerFont,[[/highlight]]
                [[highlight]]),[[/highlight]]
              [[highlight]]);[[/highlight]]
            [[highlight]]},[[/highlight]]
          [[highlight]]);[[/highlight]]
          [[highlight]]final divided = ListTile[[/highlight]]
            [[highlight]].divideTiles([[/highlight]]
              [[highlight]]context: context,[[/highlight]]
              [[highlight]]tiles: tiles,[[/highlight]]
            [[highlight]])[[/highlight]]
            [[highlight]].toList();[[/highlight]]
        [[highlight]]},[[/highlight]]
      [[highlight]]),[[/highlight]]
    );
  }
{% endprettify %}
</li>

<li markdown="1"> builder 속성은 "Saved Suggestions"라는 새 경로의 app bar가 포함 된 Scaffold를 반환합니다. 새 라우트의 본문은 ListTiles 행을 포함하는 ListView로 구성됩니다. 각 행은 구분선으로 구분됩니다.

아래에 강조 표시된 코드를 추가하세요:

<!-- skip -->
{% prettify dart %}
  void _pushSaved() {
    Navigator.of(context).push(
      new MaterialPageRoute(
        builder: (context) {
          final tiles = _saved.map(
            (pair) {
              return new ListTile(
                title: new Text(
                  pair.asPascalCase,
                  style: _biggerFont,
                ),
              );
            },
          );
          final divided = ListTile
            .divideTiles(
              context: context,
              tiles: tiles,
            )
            .toList();

          [[highlight]]return new Scaffold([[/highlight]]
            [[highlight]]appBar: new AppBar([[/highlight]]
              [[highlight]]title: new Text('Saved Suggestions'),[[/highlight]]
            [[highlight]]),[[/highlight]]
            [[highlight]]body: new ListView(children: divided),[[/highlight]]
          [[highlight]]);[[/highlight]]
        },
      ),
    );
  }
{% endprettify %}
</li>

<li markdown="1"> app을 hot reload 하세요. 선택 항목 중 일부를 즐겨 찾기에 추가하고 app bar의 list 아이콘을 탭합니다. 즐겨찾기가 포함 된 새로운 경로가 나타납니다. 네비게이터는 app bar에 "뒤로가기" 버튼을 추가합니다. `Navigator.pop` 을 명시적으로 구현할 필요가 없습니다. 뒤로가기 버튼을 탭하여, 홈으로 이동합니다.
</li>
</ol>

<center><img src="images/step6a-screenshot.png" alt="screenshot at completion of 6th step"><img src="images/step6b-screenshot.png" alt="second route"></center>

<p class="h2-like">문제점?</p>

app이 제대로 실행되지 않는다면, 다음 링크의 코드를 사용해 보세요:

* [**lib/main.dart**](https://gist.github.com/Sfshaza/bc5547e112e4dc3a1aa87afdf917caeb)

---
# Step 7: UI 테마 변경하기

마지막 단계로, app의 테마와 함께 할 것입니다. _theme_ 는 app의 look and feel을 제어합니다. 물리적 장치 또는 에뮬레이터에 종속적인 기본 테마를 사용하거나 당신의 브랜딩을 반영하도록 테마를 사용자 정의 할 수 있습니다.

<ol markdown="1">
<li markdown="1"> ThemeData 클래스를 설정하여 app의 테마를 쉽게 변경할 수 있습니다.app에서 현재 기본 테마를 사용하지만 기본 색상을 흰색으로 변경합니다.

MyApp에 강조 표시된 코드를 추가하여 앱의 테마를 흰색으로 변경합니다:

<!-- skip -->
{% prettify dart %}
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new MaterialApp(
      title: 'Startup Name Generator',
      [[highlight]]theme: new ThemeData([[/highlight]]
        [[highlight]]primaryColor: Colors.white,[[/highlight]]
      [[highlight]]),[[/highlight]]
      home: new RandomWords(),
    );
  }
}
{% endprettify %}
</li>

<li markdown="1"> 앱을 hot reload 합니다. 전체 배경은 app bar 또한 흰색입니다.
</li>

<li markdown="1"> 독자를위한 연습으로 [ThemeData](https://docs.flutter.io/flutter/material/ThemeData-class.html)를 사용하여 UI의 다른 측면을 변경해 보세요. Material 라이브러리의 [Colors](https://docs.flutter.io/flutter/material/Colors-class.html) 클래스는 많은 색상 상수를 제공하며 hot reload는 UI를 빠르고 쉽게 테스트 해줍니다.
</li>
</ol>

<center><img src="images/step7-themes.png" alt="screenshot at completion of 7th step"></center>

<p class="h2-like">문제점?</p>
app이 제대로 실행되지 않는다면, 다음 링크의 코드를 사용해 최종 앱의 코드를 확인해 보세요:

* [**lib/main.dart**](https://gist.githubusercontent.com/Sfshaza/c07c91a4061fce4b5eacaaf4d82e4993/raw/4001a72c0133b97c8e16bdeb3195ca03525696bd/main.dart)

---

# 잘 하셨습니다!

iOS와 Android 모두에서 실행되는 대화식 Flutter 앱을 작성했습니다. 이 codelab에서는 다음을 수행했습니다:

* Flutter app을 만들었습니다.
* Dart 코드로 작성했습니다.
* third party library를 사용했습니다.
* 더 빠른 개발 cycle을 위해 hot reload를 사용했습니다.
* 상태 기반 위젯을 구현하여 app에 상호작용 기능을 추가했습니다.
* ListView 와 ListTiles와 함께 표시되는 지연로드 된(lazily loaded) 무한 스크롤 목록을 작성했습니다.
* 홈 경로와 새 경로 사이를 이동하기위한 경로를 만들고 로직을 추가했습니다.
* 테마를 사용하여 앱의 UI 모양 변경에 대해 배웠습니다.

<p class="h2-like">다음 단계</p>

[다음 단계: 더 배우기](/get-started/learn-more/)
