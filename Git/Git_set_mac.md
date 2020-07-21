## 맥북에 Git 설치하기
원래 터미널에 git --version을 입력하면 깃이 설치되는데 중간에 자꾸 네트워크 오류로 실패


```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
brew install -s git
```

터미널에 위에 두줄을 입력해서 Homebrew를 설치하면 된다고 해서 해봤는데 역시 실패

https://sourceforge.net/projects/git-osx-installer/

링크에서 직접 다운 받아서 설치하는 것으로 드디어 성공했다.

1. 다운 받은 파일을 열어서 pkg파일을 실행하려고 하면

2. 확인되지 않은 개발자 ~메시지가 뜬다

3. 보안 및 개인 정보 보호 - 일반을 보면 

4. 확인된 개발자가 등록한 응용 프로그램이 아니기 때문에 차단했다는 내용 옆에 확인 없이 열기

5. 설치하면 끝!
