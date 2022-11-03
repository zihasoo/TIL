openssl pkcs12 -export -out javava.p12 -in runjava.mcv.kr-crt.pem -inkey runjava.mcv.kr-key.pem -passout pass: 030512 -alias javava

https://blog.itcode.dev/posts/2021/08/19/lets-encrypt

	//letsencrypt 인증서 발급 라우터
//	@GetMapping("/.well-known/acme-challenge/{fileName}")
//	public String auth(@PathVariable String fileName) throws IOException {
//		var file = new File("D:\\Codes\\Java\\Java Execute Server\\.well-known\\acme-challenge\\"+fileName);
//		return new Scanner(file).nextLine();
//	}