# About_Android
안드로이드를 공부하면서 알게 된 것을 기록하는 저장소입니다.

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
