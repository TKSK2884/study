# URI와 URL의 차이

## URI(Uniform Resource Identifier)

-   자원을 고유하게 식별하는 문자열
-   웹에서 특정 자원(파일, 페이지, 서비스 등)을 가리키는데 사용됨

### 구성요소

-   스키마(프로토콜): http, https, ftp등
-   경로: /path/to/resource
-   선택적으로 쿼리문자열, 포트, 호스트 등이 포함될수 있음

### 예시

-   https://example.com/index.html
-   mailto:user@example.com(이메일 주소 식별)
-   urn:isbn:04568358(ISBN 책 번호 식별)

### 특징

-   URI는 자원의 위치(URL)과 자원의 이름(URN)을 모두 포함하는 개념
-   모든 URL은 URI이지만, 모든 URI가 URL은 아님

## URN(Uniform Resource Name)

-   자원의 이름을 식별
-   URN은 자원이 어디에 있는지는 나타내지 않으며, 단지 자원의 고유한 이름을 제공하여 식별함
-   위치 독립적: 자원이 현재 어디에 있든 상관없이, 동일한 이름으로 식별
-   유일성 보장: 같은 이름을 가진 자원이 두 개 이상 존재할 수 없음

### URN 예시

1. ISBN(국제 표준 도서 번호):
   urn:isbn:0780131103627
    - 이 URN은 특정 책을 식별하며, 책의 위치나 접근 방법은 제공하지 않음
2. RFC 문서(IETF 표준 문서):
   urn:ietf:rfc:2141

    - 이 URN은 RFC 2141이라는 문서를 식별

3. UUID(범용 고유 식별자):
   urn:uuid:123e4567-e89b-12d3-a456-426614174000

    - 이 URN은 특정 객체를 고유하게 식별함

    URN의 활용

    - 도서관 시스템: ISBN, ISSN 등을 사용하여 책, 논문, 잡지를 고유하게 식별
    - 디지털 자산 관리: UUID 또는 기타 네임스페이스를 사용하여 디지털 객체 식별
    - 표준 문서 식별: IETF 문서, ISO 표준 등

### URL(Uniform Resource Locator)

-   URL은 자원의 위치와 접근 방법을 나타냄
-   URL은 자원이 어디에 위치하는지와 어떻게 접근할 수 있는지를 모두 포함함
-   위치 종속적: 자원이 이동하면 URL도 변경됨
-   접근 정보 포함: 프로토콜(http, ftp) 및 경로(/path/to/resource)를 포함하여 자원을 가져오는 방법을 제공함

### URL 예시

1. 웹페이지:
   https://example.com/index.html

-   스키마: https (프로토콜)
-   호스트: example.com
-   경로: /index.html

2. API 요청:
   https://api.example.com/v1/users?id=123

-   스키마: https (프로토콜)
-   호스트: api.example.com
-   경로: /v1/users
-   쿼리 문자열: id=123

3. 파일 다운로드:
   ftp://ftp.example.com/file.zip

-   스키마: ftp (파일 전송 프로토콜)
-   호스트: ftp.example.com
-   파일 경로: /file.zip

### URL의 활용

-   웹 페이지 및 리소스 접근: 브라우저에서 링크를 클릭하거나 자원에 직접 접근
-   REST API 설계: 자원의 위치와 접근 방법을 제공
-   파일 다운로드 및 업로드: FTP 또는 HTTP를 통해 자원 관리
