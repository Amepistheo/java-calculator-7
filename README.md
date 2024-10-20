# java-calculator-precourse

## 1주차 미션 : 문자열 덧셈 계산기
<details>
	<summary>과제 내용</summary>

## 과제
- 입력한 문자열에서 숫자를 추출하여 더하는 계산기를 구현한다.
   - 쉼표(,) 또는 콜론(:)을 구분자로 가지는 문자열을 전달하는 경우 구분자를 기준으로 분리한 각 숫자의 합을 반환한다.
   - 예: "" => 0, "1,2" => 3, "1,2,3" => 6, "1,2:3" => 6
   - 앞의 기본 구분자(쉼표, 콜론) 외에 커스텀 구분자를 지정할 수 있다. 커스텀 구분자는 문자열 앞부분의 "//"와 "\n" 사이에 위치하는 문자를 커스텀 구분자로 사용한다.
   - 예를 들어 "//;\n1;2;3"과 같이 값을 입력할 경우 커스텀 구분자는 세미콜론(;)이며, 결과 값은 6이 반환되어야 한다.
   - 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException을 발생시킨 후 애플리케이션은 종료되어야 한다.
### 입출력
- 입력 : 구분자와 양수로 구성된 문자열
- 출력 : 덧셈 결과

ex)
```
덧셈할 문자열을 입력해 주세요.
1,2:3 
결과 : 6
```
</details>

## 구현 방식
```
1. 입력받는 View 객체 생성
2. 입력받은 값이 NULL일 경우 IllegalArgumentException 반환
3. 입력받은 값이 NULL이 아닐 경우 DTO 객체 생성 후 Controller 객체에 전달
4. Controller에서 Service 호출
5. Service의 비즈니스 로직 수행
	a. 빈 문자열을 입력할 경우 0 반환
	b. 쉼표 or 콜론을 구분자로 가지는 문자열을 전달하는 경우 구분자를 기준으로 분리한 각 숫자의 합을 반환
            * 추후 다른 연산자가 오는 가능성을 고려하여 연산 메서드는 따로 구현
	c. 커스텀 구분자
            * 쉼표, 콜론 외의 커스텀 구분자 지정 가능
            * 커스텀 구분자는 문자열 앞부분의 "//"와 "\n" 사이에 위치하는 문자를 커스텀 구분자로 사용 
	d. 잘못된 값을 입력할 경우 IllegalArgumentException을 발생시킴
            * 잘못된 값
               i) 입력값에 구분자와 숫자 외의 입력값 (공백이나 줄바꿈은 배제)
               ii) 자료형에 담을 수 없는 입력값
               iii) 연산이 불가능한 상황 (연산자가 연달아 나오는 경우)
6. 계산된 결과를 Controller로 반환
7. Controller에서 View로 결과값을 전달
8. View에서 결과값을 출력 및 프로그램 종료
```


## 구현할 기능 목록
- [X] 입력
   - 문자열을 입력
- [X] 전처리
   - 입력받은 문자열에서 커스텀 구분자 추출
   - 잘못된 입력값에 대한 예외를 처리
- [X] 연산
   - 숫자를 더함
- [X] 출력
   - 결과값을 출력
