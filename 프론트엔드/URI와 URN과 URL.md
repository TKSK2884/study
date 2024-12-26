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
