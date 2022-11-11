Unity에서 Newtonsoft Json 사용하기
=

유니티 자체에도 JsonUtility를 지원하기 때문에 단순한 직렬화 - 역직렬화는 가능하지만, 이상하게 C# 딕셔너리를 직렬화하려고 하면 빈 값으로 저장이 돼버린다. 

Json을 쓰는 곳이 워낙 많기때문에 가끔 전혀 연관없는 다른 패키지에도 내장으로 Json컨버터가 있는 경우가 간혹 있지만, 일반적으론 속도가 매우 느리다. 필자의 경우엔 Reflect 패키지에 내장되어있는 JsonConverter를 써보았는데, 딕셔너리도 직렬화가 잘 되긴 하지만 속도가 무진장 느려서 멀티스레드를 무조건 사용해야했다. (당시에는 데이터가 너무 커서 원래 이런 줄 알았다.)
Newtonsoft의 JsonConvert를 사용하니 속도가 10배 이상 빨라졌다. 비동기도 필요가 없어질 정도였다...

각설하고, 설치하는 방법을 알아보자. 먼저, NuGet같은걸로 dll을 그냥 박아서 사용하면, 빌드 세팅에서 scripting backend가 mono일 땐 괜찮지만 IL2CPP일 경우엔 
> NotSupportedException: System.Reflection.Emit.DynamicMethod::.ctor

오류가 뜨며 전혀 실행이 되지 않는다. 요즘엔 거의 IL2CPP를 사용하기 때문에 다행히 이를 지원하는 Newtonsoft.Json-for-Unity가 있어 이를 사용하면 된다.

사용 방법은, 유니티 프로젝트에서 <프로젝트 경로>/Packages/manifest.json 로 가서 dependencies에 "com.unity.nuget.newtonsoft-json": "3.0.2" 를 추가하면 된다. 그러면 유니티 패키지 메니저에 뜨게 되고, 업데이트도 가능하다.

다만 Rider에서 이를 인식하지 못하는 경우가 간혹 있는데, 그럴땐 오른쪽 상단 실행 버튼 옆에 있는 Refresh Unity Assets 버튼을 눌러주면 된다.

Json으로 한줄로 저장된걸 VSC를 이용해 정렬을 해주면 6만줄 정도가 나오는 데이터인데, 저장/로드가 0.1 ~ 0.3초정도면 완료된다. 정말 끝내주는 성능이다.