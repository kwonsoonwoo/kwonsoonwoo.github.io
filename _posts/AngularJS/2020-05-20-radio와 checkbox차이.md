---
layout: post
title: radio와 checkbox 차이
category: TIL(Today I Learned)
tags:
  - angularJS
  - radio와 checkbox의 차이
  - ng-repeat
---



### 문제상황

---

`ng-repeat`을 통해 나오는 값을 다중선택 혹은 해제할수 있어야 함.

---

### 문제 해결

---

- `checkbox` 속성 사용

```javascript
// 수정하려는 기존 데이터의 프로토콜 값이 HTTP
<tr ng-repeat="(key, portMember) in pop.portMembers"><!-- 선택 된 row -->
				<td>
					<div class="checkbox">
						<input type="checkbox" id={{portMember.id}} ng-model="portMember.checked" value="true">
						<label for={{portMember.id}}></label>
					</div>
				</td>
</tr>
```

![ngchecked](/assets/angularjs/ngchecked.PNG)



- 기존에는 `input` 의 속성이 `radio` 로 되어있다 보니 다중선택이 안됐었다.
  - 되도록 구현해봤으나 해제가 안됨......(~~삽질을 몇시간 한거지 대체..~~)



---

### Reference

---

