## Git branch

1. branch는 단순한 포인터이다.
2. HEAD는 단순한 포인터이다. (포인터의 포인터인 경우가 많음)
3. HEAD는 현재 내가 작업중인 커밋을 의미한다.
4. HEAD가 master에 있다. -> 현재 master에서 작업 중이다.



```bash
$ git branch b1<브랜치명>
$ git switch b1 (head가 b1을 가리킴)

$ git switch -c b3 (b3 브랜치 생성하면서 스위치해줘)

$ git log --oneline (깃로그 상태확인)
$ git log --oneline --graph (깃로그 그래프로 상태확인)
 
merge하는 법 (master에서 머지해야 마스터가 앞으로 나아감 )
$ git switch master
$ git merge b1 

$ git branch -d b1 (머지 후 브랜치 삭제)


```



#### Merge

1. FF (그냥 마스터에서 새로운 브랜치가 연장선상일때 길따라서 마스터가 새로운브랜치로 확장함)
2. Auto Merge  (마스터와 브랜치가 길이 갈라져서 새로 합쳐야되는데 아무런 충돌이 일어나지않아 자연스럽게 합쳐짐)
3. Manual Merge(confilict) (2와같은 경우인데 충돌이 생겨 (공통작업파일이 있는 경우) 충돌된 부분을 수정한 후 다시 커밋하여 합치기)



#### 공동작업하기

1. 메인 브랜치 생성 (커밋루트 필수)
2. 각각 메인테이너와 디벨로퍼들은 메인 브랜치를 클론
3. 클론 후 자신의 브랜치 생성 후 이동
4. 자신의 파생 브랜치에서 깃 에드 커밋 진행
5. git push origin master(x) git push origin add2(파생브랜치네임)
6. 깃랩에서 메인 브랜치로의 머지리퀘스트 진행 
7. 충돌이 없다면 (리뷰 및 충돌 정리) 머지 진행 (소스브랜치-파생브랜치 삭제 옵션 설정)
8. 머지완료 후 자신의 작업으로 돌아와 메인브랜치로 스위치 후 풀 진행 
9. git branch -d add2로 파생 브랜치 삭제