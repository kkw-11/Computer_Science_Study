# HTTP역사와 HTTPs

- Hypertext
  - 현재는 Hypermedia에 가깝다.
  - hyper links 나 resource(문서나 이미지 파일 json, mp3, mp4) 등
- Transfer Protocol : request - response으로 이루어진 protocol

## HTTP

- 암호화처리 되어있지 않아 보안에 취약

## HTTPS

- Hypertext Transfer Protocol Secure
- TLS/SSL와 같은 암호화된 방식으로 데이터 처리
- 보안관계가 형성된 Server와 Client간 데이터 처리

## 역사

- HTTP (1989)
- HTTPS (1994)
- HTTP v1 (1997)

  - 전세계 30%
  - HTTP, HTTPS 둘 다 지원
  - text-based로 데이터 통신
  - uncompressed headers
  - one file at a time
  - inefficient

- HTTP v2 (2015)

  - 전세계 50%, 거의 HTTPS
  - v1에 비해 efficient와 secure 개선
  - binary based protocol
  - header compression
  - multiplexing : 여러개파일 동시에 주고받음.
  - stream prioritization
  - **현재는 v2 기준으로 정리**

- HTTP v3 (2019~)
  - HTTPS만 지원
  - 기존 TCP -> UDP 프로토콜 베이스 바뀜

# Status Code

- HTTP Status Codes 정리
- 1xx
- 2xx
- 3xx
- 4xx
- 5xx
- Status Code안에 숨겨진 의미 & 활용방법

# Request

- Request URL
- URL(Uniform Resource Locator)은 무엇인지 어떻게 구성이 되어지는 지,
- Request Methods
- GET : get
- POST : create
- PUT : replace
- DELETE : delete
- PATCH : replace partially
- HEAD : get without body
- OPTIONS : all supported methods for URL
- TRACE : echoes the received request

# HTTP Headers
