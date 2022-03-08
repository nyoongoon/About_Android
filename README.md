# About_Android
안드로이드를 공부하면서 알게 된 것을 기록하는 저장소입니다.



# Context 
- 안드로이드에서 컨텍스트란 애플리케이션(객체)의 현재 상태의 맥락을 의미함. 
- 컨텍스트는 새로 생성된 객체가 지금 어떤 일이 일어나고 있는지 알 수 있도록 함. -> 액티비티와 애플리케이션에 대한 정보를 얻기 위해서는 컨텍스트를 사용하면 됨. 
- 컨텍스트는 시스템의 핸들과 같음. 리소스, DB, preferences 등에 대한 접근을 제공. 
- 액티비티 객체는 컨텍스트를 상속받기 때문에 액티비티는 애플리케이션이 현재 실행중인 환경에 대한 핸들과도 같음
- 액티비티는 애플리케이션의 특정 리소스, 클래스, 환경에 대한 정보에 접근할 수 있게 해줌.

## Application Context
- 애플리케이션 컨텍스트는 싱글턴 인스턴스이며 액티비티에서 getApplicationContext()를 통해 접근할 수 있음. 이 컨텍스트는 애플리케이션의 라이프사이클과 연결되어 있음. 이 컨텍스트는 현재의 컨텍스트와 분리된 라이플 사이클을 가진 컨텍스트가 필요할 때나 액티비티의 범위를 넘어서 컨텍스트를 전달할 때 사용.
- 메모리 누수 발생 조심.

## Activity Context
- 액티비티 컨텍스트는 액티비티에서 사용 가능하며 이는 액티비티의 라이플사이클과 연결되어 있음. 액티비티 범위 내에서 컨텍스트를 전달하거나 라이프사이클이 현재의 컨텍스트에 붙은 컨텍스트가 필요할 때, 액티비티 컨텍스트를 사용. 
- ContentProvider.getContext();
<br/><br/>

# 컴포넌트 
- 어플리케이션은 컴포넌트로 이뤄짐
### activity
- 사용자 UI, UX 
### service
- 백그라운드 실행 프로그램
### broadcast reciver
- Intent가 이곳에
### content provider

## Activity
- UI 페이지 하나.
- Event-Driven 프로그래밍 
- 액티비티들이 모여서 애플리케이션이 됨. 

## Service
- 백그라운드에서 실행되는 컴포넌트로서 오랫동안 실행되는 작업이나 원격 프로세스를 위한 작업
- ex) 배경음악을 연주하는 작업. 
- 액티비티는 활성화시에만 작동하는데 반면, 서비스는 백그라운드에서 작동 가능. (독립 스레드)

## Broadcast Reciver
- 방송을 받고 반응하는 컴포넌트
  
## Content Provider
-  데이터를 관리하고 다른 애플리케이션에게 제공하는 컴포넌트 
- (전화번호부에 번호 저장하면 카카오톡에서도 보이는 개념)

### PC 애플리케이션과 차이점
- 다른 애플리케이션의 코드 사용 X
- ex) 카톡의 데이터를 스카이프가 가져올 수 없다.
- 안드로이드는 다른 애플리케이션의 컴포넌트 사용가능.


## Intent
- 애플리케이션의 의도를 적어서 안드로이드에 전달하면 안드로이드가 가장 적절한 컴포넌트를 찾아서 활성화하고 실행

## Menifest File
- 적재목록(적하목록)
- 구조화된 정보처리에 적합한 XML 파일 이용. 

## XML (extensable markup language)
- xml은 안드로이드에서 많이 사용
- sgml의 부분 집합으로 웹 상에서 구조화된 텍스트 형식의 문서를 전송하고 수신하며 처리가 가능하도록 만든 마크업 언어
  


# Class MainActicity 
```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle 
    	savedInstanceState) { // create이벤트 발생시 실행
        super.onCreate(savedInstanceState);
        //R은 리소스(res디렉토리)의 약자(레이아웃이라는 리소스)
        setContentView(R.layout.activity_main);
    }
}
```
<br/><br/>

# 딥링크와 URL 스킴(스키마)
- 앱 내부 콘텐츠로 연결하는 링크가 딥 링크
- 딥 링크 중 하나의 기술이 URI 스킴, 앱 스키마 커스텀 설정 후 사용.
- URI 스킴에는 앱이 설치 안되어 있는 경우 에러가 뜨고, 다른 스킴과 겹쳐 충돌이 일어날 수 있음.
- 그래서 iOS와 android에서는 요즘 유니버셜 링크와 앱 링크를 주로 활용.

### 딥링크
- 사용자가 앱 내부 콘텐츠에 직접 도달하도록 해주는 모든 링크
- 유니버설 링크, URI스킴 및 앱 링크는 모바일 딥링크가 작동하도록 하는 기술들. 
<br/><br/>


# 안드로이드 앱의 기본 구조
### 일반적인 앱 작성 절차
- 사용자 인터페이스 작성
- 자바 코드 작성
- 매니페스트 파일 작

### 패키지 폴더
- java, Gradle, res, manifest
- res -> drawable에는 해상도 별로 아이콘 파일이 저장, layout에는 화면의 구성을 정의. values에는 문자열과 같은 리소스 가 저장. menu에는 메뉴 리소스들이 저장됨. 

### onCreate()
- 일조으이 main 함수의 역할
- onCreate() 메소드는 액티비티가 생성되는 순간에 딱 한 번 호출
- 모든 초기화와 사용자 인터페이스 설정이 여기에 들어간다. 


### setContentView(R.layout.activity_main)
- setContentView()함수는 액티비티의 화면을 설정
- R.layout.activity_main은 activity_main.xml 파일을 나타낸다.


# 소스코드와 XML과 리소스
### 안드로이드 앱 실행이 시작되는 곳
- 안드로이드에는 main()이 없음
- 액티비티 별로 실행됨
- 액티비티 중에서 onCreate() 메소드가 가장 먼저 실행 됨.  
### <Text View>의 XML 속성 설명
- xmls:android : xml name space의 선언으로 안드로이드 도구에 안드로이드 name space에 정의된 속성들을 참고하려고 한다는 것을 함시. xml 파일에서 항상 최외곽 태그는 이 속성을 정의. 
- android:id TextView 요소에 유일한 아이디를 할당. 이 아이디를 이용해서 소스 코드에서 이 텍스트 뷰를 참조. 
- android:layout_width 화면에서 얼마나 폭을 차지할 것인지를 정의. "match_parent"는 전체 화면의 폭을 다 차지하는 것을 의미.
- android:layout_heigt 화면에서 길이를 얼마나 차지할 것인지를 정의. "wrap_content"는 콘텐츠를 표시할 정도만 차지하는 것을 의미.
- android:text 화면에 표시하는 텍스트를 설정. 이 속성은 예제와 같이 하드코딩될 수도 있고 아니면 문자열 리소스의 개념을 사용할 수도 있음. 

### cf) 자바 oop
- Object 객체에는 두가지 관게
- "is a" 관계 : A is a B -> 상속(inheritance)
- "has a" 관계 : A has a B -> 포함(composite)

### 리소스 
- 안드로이드에서 레이아웃, 이미지, 문자열들을 리소스로 취급.
- drawable -> 이미지
- layout -> 뷰의 배치
- mipmap -> 특이한 형태의 이미지들(아이콘 등)
- values -> 색, 문자열, 스타일

### 코드와 리소스 분리 이유
- 안드로이드가 탑재된 장치들이 다양해지면서 언어나 화면 크기에 따라서, 리소스를 다크게 하는 것이 필요 !
- 문자열도 xml로 기술하는 것이 바람직 (언어별 버전 등)

### 메니페스트 파일
- app의 전체 컴포넌트를 기술

### 에뮬레이터 로그캣
- 디버깅용 메세지 출력 


<br/><br/>
# Gradle 
- 빌드 자동화 시스템 
### 목적
- 1. 빠른 기간 동안 계속해서 늘어나는 라이브러리의 추가
- 2. 프로젝트를 진행하며 라이브러리 버전 쉽게 동기화

### 특징
- Groovy기반 DSL
- Build-by-convention 
- Multi 프로젝트 빌드 지원하기 위해 설계됨
- 설정 주입 방식. 

### buildscript{} (메소드)
- 빌드 스크립트 자체를 빌드하는 과정에서 필요한 외부 라이브러리를 클래스 패스에 추가하는 기능을 함. 
- 중괄호 묶은 내용을 ScriptHandler로 전달.
- ScriptHandler는 클로저를 인자로 받는 두 개의 메소드를 갖음. 
- 빌드 스크립트에서 클래스패스를 추가할 경우 구성(configuration) 이름으로 classpath 문자열이 필요.

### repository 메소드
- 저장소 설정을 담당. 
- 클로저 내용은 RepositoryHandler를 통해 실행 됨.
- RepositoryHandler는 메이븐 중앙 저장소 추가를 위한 mavenCentral 메소드와 Bintray의 jCenter 저장소 추가를 위한 jcenter 메소드를 제공. 

### ext 메소드
- ext 메소드는 그 인자를 buildScript에서 전역변수로 사용하기 위해 사용되는 메소드. 

### dependencies 메소드
- Gradle은 Maven과 Ivy를 지원.
- 이행적 의존성이 아닌 일반 파일로 저자된 외부 라이브러리도 지원.
- 빌드 스크립트에서 직접 의존성을 지정.

### apply plugin 
- Gradle 플러그인을 사용하기 위한 것. 

### sourceCompatibility
- 자바 소스를 컴파일 시키는 역할. 

## 기본 구조
- Project: 모든 Gradle script는 하나 이상의 project로 구성, 모든 프로젝트는 하나 이상의 task로 구성됨.
- Task: 작업의 최소 단위. Task간 의존관계 설정과 함께 흐름에 따른 구성이 가능, 동적인 태스크의 생성도 가능. 
### 구조
- /.gradle, /gradle : 버전별 엔진 및 설정 파일
- /.idea 에디터 관련 파일들
- /gradlew, /gradlew.bat : gradle 명령 파일
- /settings.gradle : 빌드할 프로젝트 정보 설정(트리 형태로 멀티프로젝트 구성)
- /build.gradle : 프로젝트 빌드에 대한 모든 기능 정의
- /src 자바 소스 파일

## Build Lifecyle
### 1. 초기화
- 빌드 대상 프로젝트를 결정하고 각각에 대한 Project객체를 생성. settings.gradle 파일에서 프로젝트 구성
### 2. 구성
- 빌드 대상이 되는 모든 프로젝트의 빌드 스크립트를 실행(프로젝트 객체 구성). configured Task 실행
### 3. 실행
- 구성 단계에서 생성하고 설정된 프로젝트의 태스크 중에 실행 대상 결정.
- gradle 명령행에서 태스크 이름 인자와 현재 디렉토리를 기반으로 태스크를 결정하여 선택된 Task들을 실행. 

### Build 설정 파일
- setting.gradle: 프로젝트 구성 설정(싱글 프로젝트의 경우 생략 가능)
- build.gradle : 빌드에 대한 모든 기능 정의

## 사용법
- build.gradle 파일에 빌드 정보를 정의하여 프로젝트에서 사용하는 환경 설정, 빌드 방법, 라이브러리 정보 등을 기술함으로서 빌드 및 프로젝트의 관리환경을 구성한다. 
### plugin 설정
- plugin은 미리 구성해 놓은 task들의 그룹이며, 특정 빌드과정에 필요한 기본정보를 포함하고, 필요에 따라 정보를 수정하여 목적에 맞게 사용. 

### 저장소 설정
- Gradle은 Maven repository, JCenter repository, Ivy directory등 다양한 저장소를 지원함.

### 의존관계 설정
- Gradle은 java 의존성 관리를 위해 다양한 구성을 제공.
- implementation: 프로젝트 컴파일 과정에서 필요한 라이브러리
- providedCompile: complie시에는 필요하지만, 배포시에는 제외될 dependency를 설정.(war plugin이 설정된 경우에만 사용 가능)
- providedRuntime: runtime시에만 필요하고, 실행환경에서 제공하는 dependency를 설정.(war plugin이 설정된 경우에만 사용 가능)
- testImplementation : teest시 필요한 dependency 관리. 

### 테스팅
- Gradle을 통해 테스팅 또한 간편하게 할 수 있음.

  
# UI 기초
## 뷰와 뷰그룹
- UI 컴포넌트 -> Activity  
### 뷰
- 컨트롤 또는 위젯이라고도 불린다. ui를 구성하는 기초적인 빌딩블록. 버튼, 텍스트필드, 체크박스 등이 여기에 속함. 뷰들은 View 클래스를 상속받아서 작성됨.
### 뷰그룹
- 다른 뷰들을 담는 컨테이너 기능. ViewGroup 클래스에서 상속받아서 작성됨. 흔히 layout이라고 불리며 선형 레이아웃, 테이블 레이아웃, 상대적 레이아웃 등이 여기에 속함. 각 레이아웃은 정해진 정책에 따라 뷰들을 배치. 
### 절차
- 1. 뷰그룹을 생성.
- 2. 필요한 뷰를 추가.
- 3. 액티비티 화면으로 설정.

## 뷰
- View 클래스는 모든 뷰들의 부모 클래스
- View 클래스가 가지고 있는 필드나 메소드는 모든 뷰에서 공통적으로 사용할 수 있다.  
### 뷰의 필드와 메소드
- id : 뷰의 식별자
- 뷰의 위치와 크기 : match_parent, wrap_content, 숫자
- 단위 : px, dp, sp, pt, mm, in 
- 화면 보이기 : visible, invisible, gone 

### 마진과 패딩
- 패딩이란 뷰의 경계와 뷰의 내용물 사이의 간격
- 마진이랑 자식 뷰 주위의 여백  
  ![image](https://user-images.githubusercontent.com/68639744/156681655-28c43663-9683-484e-a63a-e30b37f20b14.png)
  
## 레이아웃
- 뷰들을 화면에 배치하는 방법
- 레이아웃 클래스는 뷰들의 위치와 크기를 결정.
  
### 위젯과 레이아웃
- 뷰 중에서 일반적인 컨트롤의 역할을 하는 것을 위젯
- 뷰 그룹중에서 내부에 뷰들을 포함하고 있으면서 그것들을 배치하는 역할을 하는 것을 레이아웃.(레이아웃도 뷰를 상속)

# Constraint Layout
- 제약 레이아웃의 가장 큰 특징은 뷰의 크기와 위치를 결정할 때 제약 조건을 사용. 
### 제약조건
- 레아이웃 안의 다른 요소와 어떻게 연결되는지 알려주는 것으로, 뷰의 연결점과 대상을 연결.
- 연결선을 만들 때는 뷰의 연결점과 타깃이 필요.
### 가이드라인
- 여러 개의 뷰를 일정한 기준 선에 정렬할 때 사용.
  
# 대표적 레이아웃
### 제약 레이아웃
- 제약 조건 기반 모델
- 제약 조건을 사용해 화면을 구성
- 안드로이드 스튜디오 디폴트 레이아웃
### 리니어 레이아웃
- 박스 모델
- 한 쪽 방향으로 차례대로 뷰를 추가하며 화면을 구성.
- 뷰가 차지할 수 있는 사각형 영역을 할당.
### 상대 레이아웃
- 규칙 기반 모델
- 부모 컨테이너나 다른 뷰와 상대적 위치로 화면을 구성.
- 제약 레이아웃을 사용하게 되면서 상대 레이아웃은 권장하지 않음
### 프레임 레이아웃
- 싱글 모델
- 가장 상위에 있는 하나의 뷰 또는 뷰그룹만 보여주는 방법
- 여러 개의 뷰가 들어가면 중첩하여 쌓게 됨. 가장 단순하지만 여러 개의 뷰를 중첩한 후 각 뷰를 전환하여 보여주는 방식으로 자주 사용.
### 테이블 레이아웃
- 격자 모델
- 격자 모양의 배열을 사용하여 화면을 구성.
- HTML에서 많이 사용하는 정렬방식과 유사하지만 많이 사용하지 않음.
### 스크롤 뷰
- 하나의 뷰나 뷰그룹을 넣을 수 있고 어떤 뷰의 내용물이 넘치면 스크롤을 만들 수 있게 도와줌. -> 뷰그룹의 역할

  
## 뷰의 영역
- 뷰가 레이아웃에 추가될 때, 보이지 않는 뷰의 Border가 있음. 이것을 뷰의 영역(Box)라고 하는데 뷰는 Border를 기준으로 바깥쪽과 안쪽 공간을 띄움.
- Border의 바깥쪽을 Margin, Border의 안쪽을 Padding이라고 부름.  
 <br/><br/>  
  
  
# MotionEvent 객체
- 이 객체에는 액션 정보나 터치한 곳의 좌표 등이 들어 있음. 
- getAction()으로 액션정보 확인 가능 -> 손가락이 눌렸는지 눌린 상태로 움직이는지, 손가락이 떼졌는지 알 수 있음.
``` java 
MotionEvent.ACTION_DOWN // 손가락이 눌렸을 때
MotionEvent.ACTION_MOVE // 손가락이 눌린 상태로 움직일 때
MotionEvent.ACTION_UP // 손가락이 떼졌을 때
```  
 <br/><br/>  
  
# shouldOverrideUrlLoading(WebView view, WebResourceRequest request)
- WebView에 URL이로드 되려고 할 때 호스트 응용 프로그램이 제어할 수 있는 기회를 제공한다. shouldOverrideUrlLoading 영역에서 내부적으로 url에 맞는 행동을(내부 화면 호출 후 종료) 하는 경우, 내부처리를 진행하고 true를 반환하여 URL 로드를 중단거나, false을 반환하여 WebView가 평소와 같이 URL로드를 진행하도록 처리한다.  
<br/><br/>  
  
# Webview 
- WebView 프레임워크를 사용하면 모든 주요 웹브라우저의 어떤 화면 구성에도 웹페이지가 적절한 크기와 배율로 표시되도록 표시 영역과 스타일 속성을 지정할 수 있음. Android와 웹 페이지 간의 인터페이스를 정의할 수도 있음. 이 인터페이스를 사용하면 웹페이지의 자바스크립트가 앱의 API를 호출하여 웹 기반 애플리케이션에 Android API를 제공할 수 있음. 
- WebView 클래스는 View 클래스의 확장으로, 웹페이지를 액티비티 레이아웃의 일부로 표시할 수 있게 해줌. 

### WebView에서 Javascript 사용
- 자바스크립트 코드와 Android 코드 간의 새 인터페이스를 결합하려면 addJavascriptInterface()를 호출한 다음, 자바스크립트에 결합할 클래스 인스턴스와 자바스크립트가 클래스를 위해 호출할 수 있는 인터페이스 이름에 전달.
```java
WebView webview = (WebView) findViewById(R.id.webview);
webView.addJavascriptInterface(new WebAppInterface(this), "Android");
```
  
<br/><br/>  
  
# XML 속성
- xmls:android -> 안드로이드 기본 SDK에 포함되어 있는 속성
- xmlns:app -> 프로젝트에서 사용하는 외부 라이브러리에 포함되어 있는 속성을 사용. app이라는 단어는 다른 것으로 바꿀 수 있음.
- xmlns:tools -> 안드로이드 스튜디오의 디자이너 도구 등에서 화면을 보여줄 때 사용. 이 속성은 앱이 실행될 때 적용되지 않고 안드로이드 스튜디오에서만 적용. 

### android:id -> id 속성은 뷰를 구분하는 구분자. 
- "@+id/아이디 값"
- xml 레이아웃 파일 안에서 뷰를 구분할 때 사용
- xml 레이아웃 파일에서 정의한 뷰를 자바 소스 파일에서 찾을 때 사용.
- xml 레이아웃 파일안에 려어 개의 뷰를 추가할 수도 있고, 추가한 각각의 뷰는 다른 뷰의 왼쪽이나 오른쪽 등에 연결할 수 있음. 이때 다른 뷰가 어떤 것인지 지정할 필요가 있는데 그 때 id속성 값이 사용됨.
- 제약 레이아웃에서 하나의 뷰를 다른 뷰와 연결할 때 사용하는 XML 속성의 이름은 다음과 같은 규칙을 갖음
```xml
layout_constraint[소스뷰의 연결점]_[타깃뷰의 연결점]="[타깃뷰의 id]"  
```  
  
  
  
