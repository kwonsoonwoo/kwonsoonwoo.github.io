---
layout: post
title: jekyll blog에서 css가 적용이 안될때 해결법
category: ETC
tags:
  - ETC
  - jekyll
---





마음에 드는 jekyll theme의 github에서 fork를 떠오거나 

파일들을 다운로드 받아 커스터 마이징을 할때 로컬에서는 잘 적용이 되는데

아래 그림처럼 서버에서는 적용이 안된 모습을 간혹가다 볼수 있다.

수많은 구글링(<del>삽질</del>)끝에 찾은 해결법에 대해 기록하고자 한다.

![jekyll blog css not rendering](/assets/jekyll/jekyll blog css not rendering.png)

**(내가 뭘 잘못한거니...?)**

---

**해결법**

**```_config.yml```** 파일의 **```baseurl```**부분을 내 github과 연결된 repo주소 혹은 블로그 주소로 변환.



해결법은 의외로 간단했다.

구글링을 통해 찾은 이유는 다음처럼 요약된다.(~~정확한 해석이 아님을 주의...~~)

- 보통 fork를 떠오는 경우 ```baseurl```이 원본 github repo주소로 되어있다.
  - ex) **user.github.io/테마원본저장소**

- 문제는 css, js, img 파일같은 resource들은 baseurl에 있는걸 렌더링하는데
- fork를 뜨면 baseurl이 테마원본저장소가 아닌 내 github주소로 바뀌기 때문에
- 없는 파일로 인식하고 계속 오류가 나게 되는것. 



잘 이해가 되지 않는다면 위에 있는 출처를 통해 오류원인을 보다 정확히 알수 있다.

---

### Reference

[Stylesheets not working for Jekyll theme Freelancer bootstrap](https://stackoverflow.com/questions/25466166/stylesheets-not-working-for-jekyll-theme-freelancer-bootstrap)