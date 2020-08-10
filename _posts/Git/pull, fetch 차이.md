**pull**

- 원격 저장소로부터 필요한 파일을 다운 + 병합
- local 브랜치와 원격 저장소 origin/master 가 같은 위치를 가리킨다.

**fetch**
- 원격 저장소로부터 필요한 파일을 다운 (병합은 따로 해야 함)
- 지역 브랜치는 원래 가지고 있던 지역 저장소의 최근 커밋 위치를 가리키고, 원격 저장소 origin/master는 가져온 최신 커밋을 가리킨다.

- 원래 내용과 바뀐 내용과의 차이를 알 수 있다 (git diff HEAD origin/master)
- commit이 얼마나 됐는지 알 수 있다 (git log --decorate --all --oneline)
- 이런 세부 내용 확인 후 git merge origin/master 하면 git pull 상태와 같아진다. (병합까지 완료)
