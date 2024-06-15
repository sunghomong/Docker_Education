# python dockerfile 활용

## --interactive

- attached 모드가 아니여도 컨테이너에서 무언가를 입력할 수 있다.

## --tty

- 터미널을 생성함.

## python 컨테이너 실행

- docker run -it (image id)
> 0 (min_number = int(input('Please enter the min number: ')))
> 10 (max_number = int(input('Please enter the max number: ')))
> 8

input 값 받고 결과 값 반환

## python 컨테이너 재실행

- docker start -a -i (컨테이너 이름)

## 컨테이너 삭제

```shell
docker ps # 컨테이너 확인
docker rm container_name #해당 컨테이너 삭제(실행중인 컨테이너 삭제 불가)
```

## 이미지 삭제

```shell
docker images #생성된 이미지 조회
docker rmi image_id # 해당 이미지 삭제 (사용되고 있는 이미지는 삭제 불가 -> 컨테이너 먼저 삭제)
docker image prune # 사용되지 않는 모든 이미지 제거
```

## 컨테이너 자동 삭제

```shell
docker rum -p 3000:80 -d --rm image_id #--rm 추가로 컨테이너에 종료되면 자동 삭제되라고 명령
```