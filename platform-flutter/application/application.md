#
````
이 프로젝트는 MVVM (Model-View-ViewModel) 패턴을 기반 입니다.

View (UI Layer):
flutter, cupertino_icons 등 UI 관련 패키지들이 이를 지원.
flutter_localizations, google_fonts 등을 통해 다국어 지원과 다양한 폰트 스타일을 적용하는 것도 이 레이어에 포함 됩니다.



Model (Data Layer):
데이터는 주로 shared_preferences, sembast, sembast_web 등을 사용해서 로컬 저장소에 저장 됩니다. 
이들은 SQLite 대체로 가볍게 로컬 데이터를 다루는 데 사용됩니다.
API 통신을 위해 dio, http 패키지를 사용하고, 데이터 직렬화는 json_serializable로 관리. 이를 통해 외부 API와 데이터를 주고받아 로컬에 저장할 수 있습니다.


ViewModel (State Management):
mobx, flutter_mobx 로 상태 관리를 수행하고 있습니다. 상태 변경이 있을 때마다 View가 업데이트되도록 합니다.
event_bus 를 통해 이벤트 기반으로 ViewModel 간의 통신을 쉽게 처리할 수 있습니다.


Service Layer (Dependency Injection 및 기타 서비스):
get_it 을 사용해 의존성 주입을 관리 합니다. get_it은 서비스 객체들이 필요할 때마다 인스턴스를 생성해주는 역할을 함.
logger는 로그 관리를 통해 디버깅을 도와줄 거고, another_flushbar는 UI에서 알림 같은 메시지를 보여주는 데 사용될 수 있습니다.


Dev Tools (Development/Testing):
build_runner 와 mobx_codegen 은 코드 생성을 지원. 모델과 상태 관리를 자동화해주는 코드 생성기 입니다.
flutter_test 는 테스트를 작성할 때 사용되고, analyzer는 코드 분석을 통해 오류를 미리 잡아 줍니다.

````
