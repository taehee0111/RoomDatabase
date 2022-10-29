#### CodeLab 뷰를 사용한 Android Room -Kotlin (https://developer.android.com/codelabs/android-room-with-a-view-kotlin#0)

#### 공부정리10: [ViewModel 만들기](https://developer.android.com/codelabs/android-room-with-a-view-kotlin#9)
ViewModel UI 에 필요한 모든 데이터를 보유하고 처리 가능
LiveData 수명주기 인식 -> UI를 표시하는 변경 가능한 데이터에 적절한 구성요소

viewModelScope
코루틴: CoroutineScope에서 실행됨 범위 취소시 해당 범위내 코루틴은 모두 취소 됨

코루틴 CodeLab URL: https://developer.android.com/codelabs/kotlin-coroutines?index=..%2F..index&hl=ko#0

LiveData를 사용하고 allWords가 반환하는 것을 캐싱하면 다음과 같은 몇 가지 이점이 있습니다.
- 우리는 (변경 사항을 폴링하는 대신) 데이터에 관찰자를 배치하고 오직 업데이트만 할 수 있다.
  데이터가 실제로 변경될 때 UI를 선택합니다.
- Repository는 View Model을 통해 UI와 완전히 분리됩니다.

polling : 일정한 주기를 가지고 서버에 요청을보내 데이터를 갱신하는 기능

ViewModel :프로세스가 중단될 경우 ViewModel 데이터도 사라질 수 있다
ViewModel의 수명주기보다 짧은 Context를 참조하지 않기 -> MemoryLeak 방지
=>ViewModel의 저장된 상태 모듈을 사용하여 복원 (참고: https://developer.android.com/topic/libraries/architecture/viewmodel-savedstate)

#### 공부 정리: [12 RecyclerView 추가](https://developer.android.com/codelabs/android-room-with-a-view-kotlin#11)
ListAdapter에는 DiffUtil이 있기 때문에 RecyclerView.Adapter 보다 성능이 더 빠르다. RecyclerView.Adapter에 DiffUtil을 추가하면 성능이 같아진다
DiffUtils에는 비동기 처리가 존재한다

#### 공부정리: [13 저장소 및 데이터베이스 인스턴스화](https://developer.android.com/codelabs/android-room-with-a-view-kotlin#12)
다른 종속 항목 삽입 패턴: Android의 종속 항목 삽입 (https://developer.android.com/training/dependency-injection)
Application : database repository 생성 (by lazy 사용할때 초기화되면 초기화 값이 정해져 있을 때 사용)

공부정리: 14 데이터 베이스 채우기 (https://developer.android.com/codelabs/android-room-with-a-view-kotlin#13)
데이터베이스를 채우는작업은 UI와 관련없기 떄문에 viewModelScope 과 같은 CoroutineScope 을 사용하면 안된다.
SupervisorJob : 자식 코루틴에서 에러가 발생할경우 부모 코루틴이 중단되게 되면서 부모 코루틴 내부의 모든 코루틴이 종료되게 된다. 이를 방지하기 위해 SupervisorJob 를 사용한다.

#### 공부정리: [15 NewWordActivity 추가](https://developer.android.com/codelabs/android-room-with-a-view-kotlin#14)

#### 공부정리: [16 데이터와 연결](https://developer.android.com/codelabs/android-room-with-a-view-kotlin#15)
by viewModels => ViewModelProvider을 사용하지 않고 ViewModel을 생성할 수 있다.

#### 공부정리: [17 요약](https://developer.android.com/codelabs/android-room-with-a-view-kotlin#16)
