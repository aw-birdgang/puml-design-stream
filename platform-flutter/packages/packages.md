# mobx
````
1. component-diagram
Store는 MobX의 핵심 객체로, Observable 상태와 Action, Computed 값을 관리합니다.
Observable은 감시되는 상태입니다. 상태가 변경되면 자동으로 Observer에게 알리고, Observer는 UI를 업데이트합니다.
Action은 상태를 변경하는 함수입니다.
Computed는 여러 Observable을 기반으로 계산된 값을 제공합니다.
User는 앱 사용자로, 특정 Action을 트리거하여 상태를 변경할 수 있습니다.


2. sequence-diagram
사용자가 Action을 트리거하면, 이는 Observable 상태를 변경합니다.
Observable 상태가 변경되면, 그 상태를 기반으로 한 Computed 값이 재계산됩니다.
Observable은 Observer에게 상태 변경을 알리고, Observer는 이에 따라 UI를 업데이트합니다.


3. state-diagram
Idle 상태: 처음 앱이 시작될 때, 아무 액션이 없을 때의 기본 상태.
ActionTriggered: 사용자가 액션을 트리거하면 이 상태로 이동.
UpdateState: 액션이 트리거되면 Observable 상태가 업데이트되고, 이 상태에서 다시 계산된 값이 업데이트됨.
NotifyObserver: 상태가 변경되면 Observer에게 이를 알림.
UpdateUI: Observer가 상태 변화를 감지하고 UI를 업데이트함.
다시 Idle 상태: 모든 작업이 완료되면 다시 Idle 상태로 돌아감.

````



# get_it
````
1. component-diagram
GetIt 서비스 로케이터: GetIt 패키지는 Service Locator 역할을 하며, 의존성을 등록하고 관리하는 핵심 구성 요소야.
MyService & AnotherService: 비즈니스 로직을 처리하는 서비스 클래스들이고, GetIt을 통해 UI에 주입돼.
UI (HomeScreen): HomeScreen은 의존성을 요청하고, Service Locator를 통해 MyService와 AnotherService를 사용해 데이터를 처리.



2. sequence-diagram
사용자 상호작용: 사용자가 UI(HomeScreen)와 상호작용하면서 서비스가 필요할 때 GetIt을 통해 의존성을 요청해.
GetIt (Service Locator): 의존성 요청을 받은 GetIt은 MyService와 AnotherService 인스턴스를 반환해.
서비스 호출: 반환된 인스턴스를 사용해 UI는 필요한 메서드(예: fetchData(), processData())를 호출하고, 이 데이터가 UI에 반영돼.



3. state-diagram
초기 상태 (ServiceLocatorNotInitialized):

처음에 서비스 로케이터는 아직 초기화되지 않은 상태야. 이 단계에서 의존성 등록이 시작돼.
서비스 등록 (RegisterServices):

setupLocator() 함수에서 get_it을 사용해 서비스들을 등록하는 단계야. 모든 서비스가 등록되면 상태는 ServicesRegistered로 전환돼.
의존성 요청 대기 (WaitingForRequest):

서비스가 등록된 이후에는 사용자가 의존성을 요청할 때까지 대기하는 상태야.
의존성 요청 (DependencyRequested):

UI나 다른 서비스가 GetIt.I<MyService>()처럼 의존성을 요청하면 이 상태로 전환돼. 이때 서비스 제공(ProvidingService) 과정이 시작돼.
서비스 제공 (ProvidingService):

get_it은 요청된 서비스를 반환해. 서비스가 제공된 후, UsingService 상태로 전환돼 사용자가 서비스 메서드를 호출하거나 데이터를 가져오게 돼.
서비스 사용 (UsingService):

서비스가 사용된 후 다시 WaitingForRequest 상태로 돌아가, 또 다른 의존성 요청을 기다리게 돼.

````
