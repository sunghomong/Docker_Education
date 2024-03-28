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

