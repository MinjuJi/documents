# CSS Position
+ 포지션 속성은 엘리먼트의 위치를 결정하는 CSS 속성이다.

## position속성의 종류
+ static
	+ position 속성을 정의하지 않았을 때 기본값으로 설정되어 있는 값
	+ 왼쪽에서 오른쪽으로, 위에서 아래로 엘리먼트가 배치되는 것
+ relative
	+ static이었을 때의 위치를 기준으로 top, right, bottom, left 방향으로 지정된 픽셀만큼 엘리먼트의 위치를 이동시킬 수 있다.
+ absolute
	+ 부모엘리먼트의 position 설정이 relative,fixed, absoute로 설정되어 있을 때 (부모엘리먼트가 static 속성이 아닌 경우) 부모를 기준으로 엘리먼트의 위치를 이동시킨다.
+ fixed
	+ 엘리먼트의 위치를 고정시킨다.
	+ 내비게이션, 좌측 메뉴, 우측의 퀵메뉴, 배너광고 고정시킬 때 사용

## CSS Layout 
+ float 속성
  + 부모엘리먼트 내의 특정 엘리먼트를 왼쪽 혹은 오른쪽으로 떠 있게 하는 것이다.
	+ 엘리먼트가 floating되면 다른 엘리먼트는 floating된 엘리먼트 아래로 들어오게 된다.
	+ floating된 엘리먼트 아래로 들어온 엘리먼트의 켄텐츠는 floating된 엘리먼트를 피해서 화면에 표시된다.
+ overflow 속성
  + floating된 엘리먼트의 높이가, 원래 그 엘리먼트 포함하고 있던 부모 엘리먼트의 높이보다 크면, 부모엘리먼트 밖으로 벗어나게 된다.
  + 부모 엘리먼트에 overflow:auto속성을 추가하면, 부모엘리먼트 밖으로 벗어나는 문제를 해결할 수 있다.
+ clear 속성
  + 특정 엘리먼트의 옆쪽에 floating된 엘리먼트가 위치하지 못하게 하는 것이다.
		