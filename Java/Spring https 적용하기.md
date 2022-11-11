Spring https 적용하기
=

윈도우에서 letsencrypt로 인증서를 발급받고 이를 spring에 적용해보자. 


우선 가장 먼저 도메인이 있어야 한다. 필자는 https://mcv.kr/ 에서 발급받았다. 딱히 더 좋아서 그런 건 아니고, 무료 도메인을 발급받을 수 있는 사이트를 아는 곳이 몇 곳 없었다.   
freenom은 발급을 받아도 해당 도메인으로 접속이 안돼서 포기했고, (한국에서 잘 안된다는 말이 있다) 내도메인.한국 은 그냥 뭔가 쓰기 불편해서 mcv에서 발급받았다. 발급 딜레이도 없고 괜찮은 것 같기도 하다.


이제 [SSL 인증서 발급받기](https://blog.itcode.dev/posts/2021/08/19/lets-encrypt) 글을 따라서 win-acme를 설치하고 발급을 받으면 된다. 해당 글에 큰 도움을 받았다. 하지만 프로그램을 실행하기 전에, 서버에 한 가지 코드를 추가해야 한다.

```java
//letsencrypt 인증서 발급 라우터
@GetMapping("/.well-known/acme-challenge/{fileName}")
public String auth(@PathVariable String fileName) throws IOException {
    var file = new File("D:\\Codes\\Java\\Java Execute Server\\.well-known\\acme-challenge\\"+fileName);
    var sc = new Scanner(file);
    var ret = sc.nextLine();
    sc.close();
    return ret;
}
```

인증 방법이 여러가지가 있는데 위 글에서 진행하는 방식은 다음과 같다. 

1. 먼저 인증 프로그램에게 서버의 루트 경로(프로젝트 폴더)와 도메인 이름등을 제공한다.
2. 이후에 인증을 시작하면 프로그램이 <프로젝트 폴더>\\.well-known\\acme-challenge\\ 경로에 랜덤한 파일을 만든다. 
3. 프로그램이 리퀘스트를 하나 날린다. 이때 <도메인 이름>/.well-known/acme-challenge/<폴더에 생성된 파일 이름> 으로 날아오기 때문에, PathVariable(라우터 이름을 받아오는 것)로 파일 이름을 받아서 위의 경로에 생성된 파일의 내용을 읽고 응답으로 보내면 된다.

위 코드를 추가하고 글을 잘 따라했다면 설정한 경로에 pem파일 4개가 생겼을 것이다. 이 중 chain이 들어간 파일 2개는 그냥 삭제해도 된다. 이제 spring에 인증서를 적용하기 위해서는 pem파일을 pkcs12로 변환하면 된다.    
pem파일을 그냥 적용해도 될 것 같은데 되는지 확인을 안해봐서 그냥 변환해서 하는 방법만 해보겠다.    

변환을 위해서는 openssl을 이용해야 한다. 윈도우에 설치할 수 있는거 아무거나 찾아서 설치하고, cmd를 실행해서 openssl.exe가 있는 폴더로 이동한다. 이후 아래 커맨드를 실행하면 된다.

> openssl pkcs12 -export -out <원하는 파일명>.p12 -in <어쩌구-crt.pem> -inkey <어쩌구-key.pem> -passout pass: <원하는 비밀번호>

<어쩌구-crt.pem> 파일과 <어쩌구-key.pem> 파일은 아까 인증 프로그램으로부터 받은 파일 4개 중 chain을 제외한 2개에서 각각 crt로 끝나는 것과 key로 끝나는 파일 이름을 넣으면 된다.    
비밀번호는 spring에 적용할 때 필요하니 아무거나 쓰면 안된다.    

그렇게 해서 .p12파일을 얻었다면 모든게 준비됐다.

> server.ssl.key-store=<.p12 파일의 절대경로>   
> server.ssl.key-store-type=PKCS12   
> server.ssl.key-store-password=<아까 입력한 비번>

<프로젝트>/src/main/resources 폴더에 있는 application.properties 파일에 위 3가지 값을 넣어주면 된다. key 파일을 resources 폴더에 넣고 그냥 키 이름을 넣어도 된다는데 나는 안돼서 그냥 절대경로를 넣었다. 그리고 다른 글을 보면 alias도 넣던데 나는 alias를 설정한 기억이 없어서 그냥 빼고 위의 3개만 넣었는데 잘 됐다.   

끝이다! 이제 https를 즐기자
