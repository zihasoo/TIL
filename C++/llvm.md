LLVM
=

LLVM은 재사용 가능하고 모듈화된 Compiler Infrastructure이다. 크리스 래트너가 2003년에 발표한 석사논문에서 출발했다.   
일리노이 대학교/NCSA 오픈 소스 라이선스를 적용받아 [소스 코드](https://github.com/llvm/llvm-project)가 Github에 공개되어 있다. 여기서 수많은 서브 프로젝트와 문서, 예제들을 확인할 수 있다.

참고로 크리스 래트너는 2005년에 애플에 들어가 Clang, Swift등을 만들기도 했다. Clang역시 같은 라이선스를 적용받아 완전히 오픈소스이며, LLVM의 메인 프런트엔드로 사용되고 있다. Swift도 LLVM을 백엔드로 하여 빌드되고, IOS의 메인 개발 언어로 사용된다.

원래 LLVM은 Low-Level Virtual Machine의 약자로 저레벨 가상 머신이라는 의미를 가졌지만, 점차 프로젝트가 커지면서 약자가 아니라 그냥 프로젝트의 이름으로 사용하고 있다.

전체적인 구조는 아래와 같다.

![LLVM 구조](images/LLVM%20%EA%B5%AC%EC%A1%B0.webp)

