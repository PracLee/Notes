# React Native

* React <> React Native 이지만, React도 해야함..
* React 자체는 Vue.js || Angular 와 같은 언어...?



* 모바일 앱 개발기술
  * Native App 개발은 Android == SDK, iOS == XCode
  * Hybrid App 개발은 Cordova || Ionic
  * Web App 개발은 반응형 웹 사이트를 모바일로 접속
  * Cross Platform App은 React Native, Flutter, Xamarin 으로 안드로이드와 iOS 앱을 생성



* React Native 개요
  * 페이스북에서 개발한 오픈 소스 프레임 워크
  * Native 모바일 앱을 개발할때 사용
  * 하나의 소스코드로 안드로이드와 iOS 앱을 생성할 수 있는 Cross Platform 모바일 앱 개발기술
  * 2015년 3월에 발표 (2024.2월 기준 0.73 Version)
  * JS로 코딩하며, React를 사용
  * 페이스북에서 개발하여 레퍼런스가 잘 되어있고, 커뮤니티가 풍부함



* React Native 장점
  * 개발자가 JS에 익숙할 경우 코딩이 쉬움
  * Cross Platform 이기 때문에 생산성이 높음
  * Native App에 근접한 성능
  * 단방향 데이터 흐름이기에 App을 이용하기 용이
  * Native App의 컴파일 과정이 불필요
  * 코드 테스트시, Hot Reloading 되어 소스코드 변경이 빠르게 반영됨



* 개발자가 알아야 할 것들
  * JavaScript & TypeScript
  * ES6
  * React
  * React Native
  * Emulator
  * Editor || IDE



* React Native App
  * 프로젝트를 생성하여 개발
  * React Native 프로젝트를 생성하려면 React Native CLI || Expo CLI 사용
  * React Native CLI : 좀 더 Native에 가까워서 Android Emulator 에서 실행가능
  * Expo CLI : 가볍긴 하지만 Emulator 사용 불가능
  * React Native CLI 설치
    *   기존 CLI 제거

        npm uninstall -g react-native-cli @react-navive-communoty/cli
    *   react Native CLI 설치

        npm install -g react-native-cli
    *   프로젝트 실행

        npx react-native run-android



*   React

    * JSX : JavaScript XML을 의미
    * JavaScript언어의 확장 문법
    * 최상위 요소(View)가 반드시 있어야 함
    * {}로 자바 표현을 사용할 수 있음
    * 태그는 반드시 닫아야 함
    *

        ```javascript
        // 태그 안에 스타일은 아래와 같이 선언
        style={{backgroundColor:'blue'}}
        /* 주석은 이렇게 선언 */
        ```



    * React의 화면은 컴포넌트의 조합으로 구성됨 -> 화면 == 컴포넌트들의 조립
    * 컴포넌트는 함수형, 클래스 형으로 정의 가능
    * 정의된 컴포넌트를 Import 해서 사용가능
    * 생명주기
      * 마운팅 : 생성
      * 갱신 : 갱신
      * 언마운팅 : 제거
    * <mark style="color:red;">React Hook 알아봐야 함</mark>
    *   componentDidMount : 컴포넌트가 로딩된 후 실행

        \-> Ajax로 수신한 데이터를 처리하는 코드를 넣어두기 적절한 메소드

