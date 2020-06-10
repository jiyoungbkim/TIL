## 로컬에 생성한 파일을 cmd를 이용하여 깃허브로 커밋하기 
### 1. 깃 저장소로 이용할 디렉토리 생성 후

해당 디렉토리에서 Shift+우클릭:여기서 명령창 열기

### 2. 깃허브 닉네임과 이메일 등록
```bash
git config --global user.name {nickname}
git config --global user.name {email address}
```
### 3. 새로운 로컬 깃 저장소 생성
```bash
git init
```
### 4. 변경된 파일을 스토리지에 추가
```bash
git add * : 새로 생성한 모든 파일
git add {file name} : 특정 파일
```
### 5. 커밋하기
```bash
git commit
git commit -m "blah blah" : 메시지를 포함하여 커밋
```
### 6. 원격 저장소의 주소
```bash
git remote add origin {remote repository url} : 처음 커밋 할 때만 사용
```
### 7. 푸쉬
```bash
git push -u origin master : 처음 커밋할 때만 사용하고 이후에는 git push만 사용
git push : local repository를 remote repository에 업로드
```
푸쉬까지 하고 나면 깃에 파일이 올라와 있는 것을 확인할 수 있다.
> 처음에 깃허브에 있던 README.md 파일을 지우고 local에 만든 README.md커밋을 하려고 하니<br> 
> ![refected] master -> master(fetch first)오류가 나서 아예 저장소를 새로 만들고 다시 테스트했봤다.
