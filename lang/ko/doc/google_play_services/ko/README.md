#광고 ID를 이용하기 위한 Google Play Services SDK의 설치


## Google Play 개발자 프로그램 정책 준거

Force Operation X Android SDKはGoogle Play 개발자 프로그램 정책에 준거하고 있습니다. 본 SDK는 정책에 준거하기 위해서, 영속적인 디바이스 ID(IMEI, MAC 어드레스, AndroidID)를 획득하고 있는 경우에는 광고 ID를 획득할 수 없습니다. 2014년 8월 1일 부터, Google Play 스토어에 업로드되는 모든 업데이트나 신규 앱을 광고 목적으로 사용할 경우에는 광고 ID를 이용할 필요가 있습니다.


## Google Play Services SDK


광고 ID를 이용하기 위해는, Google Play Services SDK가 설치되어 있어야 합니다.
앱에 Google Play Services SDK가 설치되어 있지 않은 경우에는, 아래의 사이트를 참고하여 설치하여 주십시오.

[Setting Up Google Play Services | Android Developers](https://developer.android.com/google/play-services/setup.html)



## Google Play Services SDK 설치

아래에, 2014년 12월 시점의 Google Play Services SDK의 설치 방법을 설명하겠습니다.

Google Play Services SDK를 설치하지 않은 경우에는, Android SDK Manager를 이용하여 패키지를 설치하여 주십시오.

* Android SDK Manager를 기동합니다.
* Extras 디렉토리 아래의 Google Play services에 체크하고, 패키지를 인스톨합니다.

![googlePlayServices01](./img01.png)

## Google Play Services 설치

Google Play Services의 라이브러리 프로젝트를 프로젝트 프로퍼티에서 외부 라이브러리 프로젝트로 참조하도록 ${ANDROID_SDK_PATH}/extras/google/google_play_services/libproject/google-play-services_lib를 지정해 주십시오.


## Google Play Services를 이용하기 위한 설정

#### AndroidManifest.xml의 편집

Google Play Services을 이용하기 위해서 아래의 설정을 AndroidManifest.xml의 <application> 태그 안에 추가하여 주십시오.

```xml
<meta-data android:name="com.google.android.gms.version"
        android:value="@integer/google_play_services_version" />
```

#### Proguard의 설정

Proguard를 이용하여 난독화하고 있는 경우에는, 아래의 설정을 추가해 주십시오.

```
-keep class * extends java.util.ListResourceBundle {
    protected Object[][] getContents();
}

-keep public class com.google.android.gms.common.internal.safeparcel.SafeParcelable {
    public static final *** NULL;
}

-keepnames @com.google.android.gms.common.annotation.KeepName class *
-keepclassmembernames class * {
    @com.google.android.gms.common.annotation.KeepName *;
}

-keepnames class * implements android.os.Parcelable {
    public static final ** CREATOR;
}
```
