### 경로를 변경하기

[Flutter SDK 구하기](./#get-sdk)와 같이 명령 줄에서만 현재 세션의 PATH 변수를 업데이트 할 수 있습니다. 이 변수를 영구적으로 업데이트하여 모든 터미널 세션에서 `flutter` 명령을 실행할 수 있습니다.

모든 터미널 세션에 대해 이 변수를 영구적으로 수정하는 단계는 시스템마다 다릅니다. 일반적으로 새 창을 열 때마다 실행되는 파일에 행을 추가합니다. 예를 들면:

1. Flutter SDK를 배치 할 디렉토리를 결정하십시오. Step 3에서 이 항목이 필요합니다.
2. `$HOME/.bash_profile` 파일을 열거나, 새로 생성하세요. 파일 경로와 파일 이름은 시스템에 따라 다를 수 있습니다.
3. 다음 줄을 추가하고 `[PATH_TO_FLUTTER_GIT_DIRECTORY]`를 Flutter의 git repo를 복제 한 경로로 변경하세요.

{% commandline %}
export PATH=[PATH_TO_FLUTTER_GIT_DIRECTORY]/flutter/bin:$PATH
{% endcommandline %}

4. `source $HOME/.bash_profile`을 실행하고 현재 윈도우를 refresh 합니다.

5. 다음을 실행하여 `flutter/bin` 디렉토리가 PATH에 있는지 확인하세요.

{% commandline %}
echo $PATH
{% endcommandline %}

자세한 사항은 [this StackExchange question](https://unix.stackexchange.com/questions/26047/how-to-correctly-add-a-path-to-path)을 확인해 보세요.
