## 프레임워크의 설정 위한 자세한 설명

빌드 대상의 타켓 클릭하고 「Build Phases」 → 「Link Binary With Libraries」를 선택합니다. 「+」 버튼을 눌러 각 프레임워크를 선택하십시오.

![프레임워크 설정01](./img01.png)

다음 프레임워크를 프로젝트에 링크해 주십시오.

<table>
<tr><th>프레임워크 명</th><th>Status</th></tr>
<tr><td>AdSupport.framework</td><td>Optional</td></tr>
<tr><td>iAd.framework </td><td>Required</td></tr>
<tr><td>Security.framework </td><td>Required </td></tr>
<tr><td>StoreKit.framework </td><td>Required </td></tr>
<tr><td>SystemConfiguration.framework </td><td>Required </td></tr>
</table>

> AdSupport.framework은 iOS 6 이후에 추가된 프레임워크이기 때문에, 앱을 iOS 5 이전 버전에서도 동작시킬(iOS Deployment Target을 5.1 이하로 설정하는) 경우에는 weak link로 설정하기 위해 "Optional"로 설정하십시오.

![프레임워크 설정02](./img02.png)

[TOP](/lang/ko/README.md)
