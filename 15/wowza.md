# wowza

[wowza install guide](Wowza설치및사용법.pdf)

[blog dasom7978](blog.naver.com/dasom7978)
[limdasom blog](https://xpk718.blog.me/221453769542)

## wowza 시작하기
> 1 필수 환경 - 서버

|    |    |
|:---|:---|
|    |와우자설치경로/bin에들어가서startup을실행합니다.    |
|    |위에있는shutdow이서비스를종료하는프로그램입니다.    |
|    | program files(x86) > wowozamediasystem > wowza streaming engine  |

cmd 파일은 숨겨 놓고 종료는 하지 말것. 서버쪽 터널링 연결이 지속되어야 gui가 사용가능함
` http://localhost:1935/  에서 접속 확인 가능 함`

> 2 GUI 환경 - 브라우저
- http://localhost:8088/enginemanager/
- |    |    |
|:---|:---|
|    |login    |
| playbacvk   | ./contents/*   |
|    | play button   |
|    | 내용입력후 앱생성   |
| application 생성   |  add application   |
| VOD   | VOD 선택 생성후 저장 버턴   |
|    | /contents 재생하고 앱은 생성한 app을 선택   |
|    | 재생상태에서 manager 진입하여 상태확인    |
|  Stream test  |[참고1]( ##ref1)   |
|  파일 구분  | [참고2]( ##ref2)   |
| Live Stream   |    |
|    | addapplication>Live 선택후 저장   |
|    | GoCode 또는 libstreaming 앱에서 핸드폰등으로 송출   |
|    |  github link example3  |
| playback test   | pdf p56 57 58 58 참고   |
### links
[livestreaming example git](https://github.com/fyhertz/libstreaming-examples)\
[livestreaming wiki](https://github.com/fyhertz/libstreaming/wiki)

## ref1
> 재생할때URL 경로에Application 이름이들어갑니다. \
rtmp://192.169.0.23:1935/vodtest/test.mp4
그래서content 폴더에
아까생성한VOD Application과같은이름의폴더가생기고
그경로에있는비디오를재생한다고생각할수있지만
그렇지않습니다.\
Application을생성했다고해서
content 폴더에같은이름으로폴더가생성되지않아요!\
모든VOD Application이content폴더를공유하고있습니다.
<u>그래서이content 폴더안에있는파일들</u>은
모든VOD Application을통해서재생이가능합니다.\
(LIVE Application은안되요!)

## ref2
> 만약데이터를구분하고싶다면 \
content 폴더안에폴더를만들어사용할수있습니다.
재생은파일이름앞에폴더이름을붙여사용합니다.\
예를들어content/vod1/test.mp4를스트림하고싶으면\
프로토콜이름://호스트주소:포트/어플리케이션이름/vod1/test.mp4
가스트림주소가됩니다.