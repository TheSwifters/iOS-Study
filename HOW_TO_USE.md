# 최초세팅

1. github에서 Fork
> 기존 Fork를 뜬 경우에는 해당 X

2. 터미널에서 git clone Fork URL

3. `cd iOS-Study`

4. git remote add upstream `Facam-10th/iOS-Study`의 git 주소를 넣는다.

5. `git checkout -b 생성할 브랜치`
> 브랜치를 생성하면서 이동하는 명렁어 

# 작업시

1. `git fetch upstream`

2. `git merge upstream/master`

3. 발표자료 or 작업을 진행한다.

4. 해당 내용을 `add`, `commit`, `fetch`, `merge`, `push`순으로 진행을 해준다.

> git add 파일명

> git commit -m "커밋내용"

> git fetch upstream

> git merge upstream/master

> git push origin 자신의 브랜치

5. github에서 pull request를 작성한다.

> write영역에 내용을 상세하게 적어준다.

6. merge되기를 기다린다.

7. 1~6 사이클이 반복된다.

# git 명령어

- `git status` --> **git 상태확인**
- `git log` --> **커밋 이력 확인**
- `git remote add <폴더/파일명>` --> **원격저장소 등록 origin을 관용적으로 사용**
- `git commit -m "커밋 메시지"` --> **커밋 메시지 작성**
- `git push <원격저장소> <원격브랜치>` --> **원격저장소에 커밋 업로드**
- `git pull <원격저장소> <원격브랜치>` --> **원격저장소의 해당브랜치 내용을 로컬저장소에 가져온다**
- `git fetch <원격저장소>` --> **원격저장소의 해당브랜치 내용을 로컬저장소에 가져온다 (fetch상태 적용안됨)**
- `git merge <원격저장소/원격브랜치>` --> **fetch한 내용을 현재 브랜치에 합친다.**

# Terminal 명령어

- `cd <이동할 경로>` --> **경로이동**
- `ls` --> **디렉토리 목록**
- `mkdir <폴더명>` --> **폴더생성**
- `touch <파일.확장자>` --> **파일생성**
- `vi <파일명>` --> **vim으로 파일 수정**
- `rm <파일명>` --> **파일삭제**
-  `rm -rf <폴더 또는 파일명>` --> **force명령어가 있으므로 주의해서 사용할것!!! 복구안됨**
-  `clear` --> **화면청소**
-  `history` --> **최근 입력한 명령어 리스트**

**초기작성일 2020/02/14**
**내용 추가 혹은 수정은 아무나 해주세요.**
