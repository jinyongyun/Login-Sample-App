# Login-Sample-App
Firebase를 이용한 로그인 샘플 앱
Backend-Frontend 데이터 흐름![image](https://user-images.githubusercontent.com/102133961/181448268-cfb07a4a-db5a-4a38-ab63-1adfd3f29159.png)
<img width="296" alt="image" src="https://user-images.githubusercontent.com/102133961/181448303-f3251da1-92a3-40fd-a338-91c8cfc02b4e.png">
client-server model
어떤 서비스를 사용하는 사용자가 client<br>
인터넷 프로그래밍 시간에 배운거<br>
사용자가 보는 화면에 표시되는 데이터를 처리하는 시스템이 서버<br>
이 둘은 서로 상호작용하며 서비스를 구성<br>
Frontend(처음) Backend(마지막)<br>
이와 같이 어떤 프로세스의 처음과 마지막을 나타내는 것이 프론트엔드와 백엔드이다<br>
Client영역이 Frontend이고 Server가 Backend영역이다.<br>
사용자를 기준으로 생각하면 <br>
사용자가 어떤 프로그램을 바라보고 있다면, 그 사용자가 프로그램으로 하는 다양한 형태의 행위. 입력, 삭제, 저장, 클릭, 스와이프 등의 입력을 받아서 처리하는 것을 프론트엔드라고 통칭한다. 백엔드는 프론트엔드와 약속한 비중에 따라 이런 여러 입력들을 전달하거나 처리한다.<br>
<br>
웹서비스가 나타나고선 이 프론트엔드과 백엔드가 인터넷으로 연결되어 데이터를 주고받게 된다.<br>
<br>
지금 현재 다루고 있는 것은 모바일 프론트엔드고 그 중에서도 ios 앱개발이다.<br>
![image](https://user-images.githubusercontent.com/102133961/181448335-3559740c-1c82-4f54-8f6e-d0eb826bd292.png)
<img width="452" alt="image" src="https://user-images.githubusercontent.com/102133961/181448372-57187e46-56b0-4da4-a9eb-65f29079963f.png"><br>
어떤 ios 앱에서 로그인의 흐름<br>
먼저 사용자가 아이폰을 통해 사용자의 아이디와 비밀번호 또는 소셜 로그인 계정을 입력한다<br>
그럼 이것을 전달하여 입력한 값이 올바른 값인지 판단할 서버가 필요하다<br>
다시 말해 로그인이라는 기능을 개발하려면 사용자가 입력할 화면 즉 프론트엔드 뿐만 아니라, 프론트엔드가 전달할 값을 적절히 처리해서 다시 인증값을 되돌려줄 백엔드 개발도 필요한 것이다!<br>
<br>
하지만 우리는 지금 ios 화면 개발밖에 못하므로 firebase를 이용하여 이 어려움을 해결해 보고자 한다.<br>
<br>
Firebase는 프론트엔드 개발에 필요한 여러 플랫폼을 제공하는 서비스이다.<br>
즉 백엔드의 여러 기능들을 별도의 백엔드 개발 없이 서버리스로 대체할 수 있는 플랫폼을 제공하는 서비스이다.<br>
<br>
서버를 직접 개발한다고 생각해보라, 도메인도 구매해야하고, API도 개발해야 하고, 서버도 따로 개발하고 비용도 지불해야 한다. 이 모든 과정을 대체할 수 있는 서비스가 바로 firebase이다.<br>
<br>
특히 포트폴리오용 앱개발을 하는 데 특화 되어 있는 것 같다.<br>
![image](https://user-images.githubusercontent.com/102133961/181448400-bd50710c-4528-4fc1-a017-90400b2a48b8.png)
<img width="452" alt="image" src="https://user-images.githubusercontent.com/102133961/181448425-a286e4d3-3eeb-44af-a5bb-4850e294b335.png">
위의 사진처럼 다양한 항목을 바탕으로 서비스를 누릴 수 있다.![image](https://user-images.githubusercontent.com/102133961/181448446-dd2961c3-733f-42f6-8c04-740784d73e53.png)
<img width="452" alt="image" src="https://user-images.githubusercontent.com/102133961/181448468-6810813e-6e8c-4192-adac-5683d058c1d0.png"><br>
intermediate 파트에서 다루게 될 다양한 Firebase의 기능들이다.<br>
<br><br>
먼저 로그인에 대해 다루어 볼 건데<br>
우리에게 익숙한 소셜 로그인을 이용한 로그인이라면 OAuth란 개념을 이해하고 있어야 한다.<br>
<br>
![image](https://user-images.githubusercontent.com/102133961/181448489-0567318a-c7db-4da0-9f37-0eb26a57c2c1.png)
OAuth란?![image](https://user-images.githubusercontent.com/102133961/181448500-2847beaf-2eab-4f27-a2d8-ddfd43ab9e56.png)
-사용자 인증 방식에 대한 업계 표준<br>
-아이디와 패스워드를 노출하지 않고 OAuth를 사용하는 업체의 API접근 권한을 위임 받음<br>
1. USER: Service Provider에 계정을 갖고 있는 사용자<br>
2. Consumer: Service Provider의 API를 사용하려는 서비스<br>
3.Service Provider: OAuth를 사용하여 API를 제공하려는 서비스<br>
4.Access Token: 인증 완료 후 Service Provider의 제공 기능을 이용할 수 있는 권한을 위임 받은 인증 키<br>
![image](https://user-images.githubusercontent.com/102133961/181448516-c3dcd482-48fb-401e-bb1d-e116569bb636.png)
<img width="451" alt="image" src="https://user-images.githubusercontent.com/102133961/181448530-1cb37163-69ec-4470-a670-21ef9e8d5b50.png">
<br>
위 사진에서 권한 위임 확인 요청을 이번에는 firebase가 대체하게 되는 것이다.<br>
(왜 그 앱 들어가면 구글에서 뭐 승인할거냐고 뜨는 하얀색 화면 그거 말하는 거다)<br>
<br>
Firebase인증 제공업체로는 google/apple/google play game/facebook/github/twitter 등이 있다<br>


![image](https://user-images.githubusercontent.com/102133961/181449399-6f5af107-208c-48cd-9ad4-41bc119236a6.png)

1.Firebase 프로젝트를 추가하기 위해, 맨 오른쪽 상단에 있는 [콘솔로 이동] 버튼 클릭!

<img width="322" alt="image" src="https://user-images.githubusercontent.com/102133961/181449504-463b081a-74ea-4149-9483-b00cba147dec.png">

xcode 프로젝트와 firebase 연결하기

![image](https://user-images.githubusercontent.com/102133961/181448573-640679b3-b639-4a71-bb44-619ad9de3a35.png)


<img width="322" alt="image" src="https://user-images.githubusercontent.com/102133961/181448630-4bc07057-c716-4a78-a52f-9ad87a75b019.png">

<br>
2.콘솔로 이동한 후, 프로젝트 추가(십자버튼) 클릭<br>
<br>
3.프로젝트 이름 입력->계속, 애널리시스(데이터 분석)과정은 아직 필요 없다->설정 끄고 만들기<br>
<br>
4.새 프로젝트가 준비 되었다는 알람이 뜨면 계속->프로젝트 추가 완료<br>
<br>
5.해당 프로젝트에서 '앱에 Firebase를 추가하여 시작하기' 문구 밑에 있는 ios 원형 버튼을 클릭<br>
![image](https://user-images.githubusercontent.com/102133961/181448652-f9539a6a-042a-4d15-996b-b85f17ce2ee3.png)<br>
<img width="259" alt="image" src="https://user-images.githubusercontent.com/102133961/181448668-b6775fb2-4494-4e6f-be61-7431977b40ae.png">
<img width="262" alt="image" src="https://user-images.githubusercontent.com/102133961/181448691-557652fd-3c81-42f9-a1f6-5a15df1cbb65.png"><br>
그럼 이런 화면이 나오는데, ios 번들 ID는 우리의 프로젝트에서 <br>
설정으로 들어가면 identity - Bundle Identifier에 있다<br>
복사 후 붙여넣기 <br>
<br>
기타 항목을 채우고, 앱 등록하기 버튼을 누르면 <br>
plist 다운로드 화면이 나온다.<br>
<br>
이 plist를 다운로드 한 후에, 우리의 xcode 프로젝트에 info.plist 아래에 추가한다.<br>
<br>
그 다음에는 Firebase sdk를 설치한다<br>
<br>
우리의 프로젝트 폴더에서 새로운 터미널을 연다<br>
<br>
pod init<br>
<br>
입력
<br>
그러면 우리의 프로젝트 폴더 내에 podfile이 탄생하는데<br>
podfile 내부의 <br>
# Pods for ~App<br>
밑에<br>
pod 'Firebase/Auth'<br>
<br>
를 추가<br>
<br>
저장한 후, 터미널로 돌아가 pod install 추가 입력<br>
<br>
그럼 sdk에 소속된 것들이 Install된다<br>
<br>
다시 폴더로 돌아가면 workspace 파일이 새로 생겨있는데<br>
<br>
앞으로는 이곳에서 작업 해야한다.<br>
<br>
AppDelegate.swift 파일로 가서 <br>
import Firebase<br>
그리고<br>
didFinishLaunchingWithOptions 메소드 내부에<br>
<br>
FirebaseApp.conFigure()<br>
를 추가해주면 초기화가 완료된다<br>
<br>
그럼 연결 끝!!<br>

