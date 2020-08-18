## Git 파일, 폴더명 변경하기
Git으로 관리하는 저장소안의 파일, 폴더명을 변경하려면 git mv 명령을 사용해야 한다.
```bash
$ git mv [원본 이름] [변경할 이름]
```
git mv 명령은 위와 같이 사용한다.
```bash
$ git mv myFile yourFile
$ git status
On branch master
Changes to be committed:
        renamed:    myFile -> yourFile
```
이후 git status로 확인하면 수정내역이 renamed로 기록된 것을 볼 수 있다.
```bash
$ mv myFile yourFile
$ git rm myFile
$ git add yourFile
```
git mv 명령은 위 세가지를 한번에 하는 것과 같은 역할을 한다.

# 참고자료 
- [git mv 명령으로 파일 이름 변경하기](https://dololak.tistory.com/311)

# 작성일
2020.08.18