# About_Android
안드로이드를 공부하면서 알게 된 것을 기록하는 저장소입니다.

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
