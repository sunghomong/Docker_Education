
## 환경 구성

```shell
node install
```

```shell
node server.js
```

## COPY

```dockerfile
COPY . .
```

- 첫번째 '.'은 Host file system 을 의미
- 두번째 '.'은 image/ container file system을 의미 / 이미지 내부의 경로

```dockerfile
COPY . /app
```

- 도커 파일과 동일한 위치에 있는 모든 파일을 /app 위치에 복사 해준다.
- /app이 없을 경우 이미지와 컨테이너를 생성해줌
- ./은 현재 작업 디렉토리를 의미할수 있다.

## WORKDIR

```dockerfile
FROM node

WORKDIR /app

COPY . /app

RUN npm install
```

- npm install을 /app 내부에서 실행시켜주겠다.
- workdir은 상대 경로를 설정해줌 copy든 RUN이든 workdir을 기준으로 실행된다.

## CMD

```dockerfile
CMD ["node","server.js"]
```

- 컨테이너가 실행될때 server.js파일을 실행하도록 지시

## EXPOSE

```dockerfile
EXPOSE 80
```

- 우리의 로컬 시스템에 특정 포트를 노출하고 싶다는것을 도커에 알리는 명령어 추가
- 단 생략 가능 선택 사항(사용하는것이 모범적인 사용법)

## DOCKER RUN

```shell
docker build .
```

- '.'은 해당 위치를 의미

```shell
docker run #{id}
```

- run 실행시 계속 실행되고 있는것을 확인 가능 이유 : cmd 명령어가 끝나지 않았기 때문

## 도커 컨테이너 실행 후 종료


```shell
# 새 터미널 연다음
docker ps #컨테이너 확인
docker stop #{name} #docker container stop
docker ps #실행중인 컨테이너가 없는것을 확인
docker ps -a #모든 컨테이너 확인
```

## 포트 지정해주기

```shell
docker run -p 3000:80 #{container id}
```

- -p는 publish를 의미 도커에 해당한 80포트를 localhost:3000번 포트에 열어주겠다 명시

## 이미지에 대한 이해

- 코드를 변경하고 컨테이너를 다시 실행 시켜도 반영되지 않는다.
- 기존 코드에서는 기본적으로 복사한 시점에서 소스 코드의 스냅샷을 만든다.
- 업데이트된 소스 코드를 반영하려면 dockerfile을 다시 빌드해야된다.
- 이미지는 모두 읽기 전용이며 한번 읽어지면 끝이다. 

## build에 대한 이해

- 이미 읽어낸 이미지를 한번더 빌드해서 읽어내면 Using cache하면서 빠르게 빌드가 끝나는것을 확인

## COPY package.json /app (캐시의 이해)

- 해당 코드를 npm install 위에 놓고 server.js만 수정을 하고 빌드하면 속도가 빨라진걸 확인 가능
- 이유는 해당 json은 변경이 없었기에 기존 캐시를 유지하고 다음 명령어를 실행

## 멈춘 컨테이너 다시 실행

```shell
docker start #컨테이너 이름/아이디
```

## Attached & Detached 컨테이너 이해하기

```shell
docker run 8000:80 -d #이미지id
docker attach #컨테이너id 
```

- attach를 하면 해당 컨테이너로 들어갈 수 있다.
- 기존의 run을 보면 이해하기 쉽다 server.js를 보면 console로 결과물을 출력하는 걸 확인 가능하다.
- run을 시키면 터미널 자체는 해당 컨테이너를 run 시키고 console 결과를 확인 가능하다.
- 하지만 Detached는 디폴트로 run을 시키고 다른 작업을 가능하게 한다.
- docker start의 디폴트 값은 Detached이다.
- 콘솔의 입력된 과거의 값들을 가져오는 방법은 아래와 같다.

```shell
docker logs #컨테이너id
```

- 컨테이너를 실행 시키고 다시 프로세스를 갖는 방법은 아래의 명령어다.

```shell
docker logs -f #컨테이너id
docker start -a #컨테이너id -> attache 모드로 다시 컨테이너 실행
```


