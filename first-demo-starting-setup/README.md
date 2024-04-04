## 환경

- NodeJS 14버전
- Docker

## 도커 컨테이너 시작

```bash
docker build .
```

```bash
docker run -p 3000:3000 image아이디값
```

## 도커 컨테이너 중지하기

- 터미널 새로 열기

```bash
docker ps // 컨테이너 확인
```

```bash
docker stop 컨테이너 name(또는 id) // 실행중인 컨테이너 중지
```

## 노드 JS 설치

- 터미널 열기

```shell
docker run node
```

```shell
Unable to find image 'node:latest' locally
```

아래와 같이 찾을수 없다는 문구가 뜨면 docker hub 가 없기 때문 
없어도 알아서 image 찾아서 빌드 해줌

## node 터미널 직접 들어가기

```shell
docker run -it node
```

위와 같은 명령어는 node를 강제로 실행시키며 상호작용할 수 있는 환경을 만들어줌
단 해당 터미널을 종료하면 실행이 종료된다.
``ctrl + c``키를 누르면 종료 가능

node -v 을 해보면 해당 로컬과 버전이 다른 경우를 확인 할 수 있음
이는 컨테이너에서 실행되는 환경이 로컬과 상관없이 실행된다는 걸 확인 가능함
즉, 환경이 통일된다는게 이부분에서 증명됨.

