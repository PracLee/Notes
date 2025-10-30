# Git pull 시 인증 오류 (Mac)

## 🙀 Description 🙀

Mac 에서 remote repository에 저장된 소스를 local로 pull 할때 나타나는 인증 오류

URL은 **HTTP 방식**이지만 GitHub는 더 이상 Mac에서 비밀번호 기반 로그인(HTTP Basic Auth)을 허용하지 않음

SSH key를 재발급 받고, GitHub ID 에 새로운 key를 입력하여 해결

### ⚽ Goal ⚽

pull request 성공

### 🏃‍♀️ Try 🏃

### 😱 Now 😱

### 👻 Error 👻

```git
remote: Invalid username or token. Password authentication is not supported for Git operations.
```

***

## 🏁 Solution 🏁

1. terminal 에서 아래 명령어를 입력하여 SSH Key 재발급

```bash
ssh-keygen -t ed25519 -C "your@email.com"
```

2. 비밀번호 키는 기본값인 null로, 입력안함
3. terminal 에서 발급된 공개 키를 확인 후 GitHub ID에 입력

```bash
cat ~/.ssh/id_ed25519.pub
```

* 출력된 내용 전체 복사 후 GitHub에 등록

1. 웹 브라우저에서 GitHub 접속
2. 우측 상단 프로필 아이콘 클릭 → **Settings**
3. 좌측 메뉴에서 **SSH and GPG keys** 클릭
4. 우측 상단 `New SSH key` 클릭
5. 아래 항목 입력:
   * **Title**: 예) "MacBook"
   * **Key**: 아까 복사한 공개 키 붙여넣기
6. **Add SSH key** 클릭
7. SSH 연결 확인

```bash
ssh -T git@github.com
```

* 정상적으로 연동 되었을 시 아래와 같이 출력됨

```bash
Hi ${yourId}! You've successfully authenticated, but GitHub does not provide shell access.
```
