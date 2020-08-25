## CSS Flex 사용법 정리 - 1
Flex는 Flexible Box, FlexBox라고도 불리우며, float, inline-block등의 기존 레이아웃 방식을 대체하기 위해 고안되었다.

## 사용법
```html
<div class="container">
	<div class="item">helloflex</div>
	<div class="item">abc</div>
	<div class="item">helloflex</div>
</div>
```
위에서 부모 요소인 container를 **Flex Container**라고 부르고, 자식 요소인 item들을 **Flex Item**이라고 부른다.
![flex_container_and_items](https://studiomeal.com/wp-content/uploads/2020/01/02.jpg)
Container안에 Item들은 기본적으로 위 그림 처럼 배열된다.

## Flex Container에 적용하는 속성
### display: flex;
```CSS
.container {
	display: flex;
}
```
Flex 레이아웃을 사용하기 위해선, 먼저 Container의 display 속성에 Flex를 적용해 주어야 한다.
### 배치 방향 설정
```CSS
.container {
	flex-direction: row;
	/* flex-direction: column; */
	/* flex-direction: row-reverse; */
	/* flex-direction: column-reverse; */
}
```
각각 아래와 같은 결과가 나타난다.
![flex_direction](https://studiomeal.com/wp-content/uploads/2020/01/05-1.jpg)
## 줄넘김 처리 설정
컨테이너가 더 이상 아이템들을 한줄에 담을 수 없을때 어떻게 처리할지에 대한 옵션으로 flex-wrap이 있다.
```CSS
.container {
	flex-wrap: nowrap;
	/* flex-wrap: wrap; */
	/* flex-wrap: wrap-reverse; */
}
```
각각 아래와 같은 결과가 나타난다.
![flex_wrap](https://studiomeal.com/wp-content/uploads/2020/01/06-1.jpg)

# 사진 및 참고 자료 출처
[1분코딩](https://studiomeal.com/archives/197)

# 작성일
2020.08.25