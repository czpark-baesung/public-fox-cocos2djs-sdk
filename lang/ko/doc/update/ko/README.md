## 최신 버전으로 업데이트

구 버전의 F.O.X SDK가 설치된 앱을, 최신 버전의 F.O.X SDK를 설치하는 과정에 대해서 설명하겠습니다.

1. 이전 버전의 파일 전부를 삭제 합니다.
2. 최신 버전의 파일을 프로젝트에 추가합니다.
3. iOS의 경우에는 Xcode의 「Product」 → 「Clean」을 실시해 주십시오.

F.O.X iOS SDK v2.12 이후의 버전에서는, 라이브러리 파일은 libAppAdForce.a 만 존재합니다. v2.11 이전의 버전에서 여러 개로 나누어져 있던 라이브러리들을 libAppAdForce.a로 통합하였습니다. 업데이트 시 아래의 파일이 프로젝트에 포함 되어 있다면 전부 삭제해 주십시오.

* libLtv.a
* libAnalytics.a
* libNotify.a


Android의 광고 ID 경우 v2.14 버전부터 대응하고 있습니다.
광고 ID를 획득할 경우에는 「[광고 ID를 이용하기 위한 Google Play Services SDK의 설치](../../google_play_services/ko/README.md)」를 확인해 주십시오.


또한, v2.14 버전부터 재반응 유도(Re-engagement)측정 기능이 추가되었습니다.
재반응 유도(Re-engagement)를 측정하는 경우에는, iOS 앱의 경우 FoxReengagePlugin.m/h를 프로젝트에 추가해 주십시오. Android 앱의 경우 「재반응 유도(Re-engagement) 구현」을 확인하고, 구현해 주십시오.

SDK의 업데이트 후에는, 반드시 효과 측정 테스트를 실시하고, 측정 및 앱의 동작에 문제가 없는 것을 확인해 주십시오.
또한, 재반응 유도(Re-engagement)측정을 사용할 예정이 있을 경우에는, 재반응 유도(Re-engagement)의 테스트를 실시할 필요가 있습니다.


[TOP](/lang/ko/README.md)
