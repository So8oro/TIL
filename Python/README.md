https://lab.ssafy.com/s13/python

# BasicSyntax01

## Python 개요

### Python 특징

- 쉽고 간결한 문법
- 강력한 커뮤니티
- 광범위한 응용 분야
- AL, ML에 가장 일반적으로 사용되며, 기본 언어 채택률이 매우 높음
- 직관적인 문법과 강력한 표준 라이브러리, 빠른 프로토타이핑으로 알고리즘 구현에 유리

### Python interpreter 사용

1. shell 프로그램에서 한번에 한 명령어 씩 입력해서 실행
2. 확장자가 .py인 파일에 작성된 파이썬 프로그램을 실행
    1. `python sample.py` 
    2. Run 버튼을 누르는 것보다 명령어로 실행하는 방법에 우선 익숙해질 것

### 표현식과 값

- 표현식 Expression
    - 값으로 평가될 수 있는 코드 조각
- 값 Value
    - 표현식이 평가된 결과
- 평가 Evaluate
    - **표현식이 평가되어 값이 반환**
- 문장 Statement
    - 실행 가능한 동작을 기술하는 코드
    - 조건문, 반복문, 함수 정의
    - 보통 여러 개의 표현식을 포함

### 타입

- 타입은 **값(피연산자)**과 **값에 적용할 수 있는 연산(연산자)** 2가지 요소로 이루어짐
- 데이터 타입에 맞는 연산을 수행해야 함
- 연산자 우선순위
    - 지수 > 음수 부호 > 곱셈, 나눗셈, 정수 나눗셈, 나머지 > 덧셈, 뺄셈

### 변수와 메모

- 변수 Variable
    - 값을 저장(참조)하기 위한 이름
    - 변수 할당 - 표현식을 통해 변수에 값을 저장
        1. 할당 연산자 오른쪽에 있는 표현식을 평가해서 값(메모리 주소)을 생성
        2. 값의 메모리 주소를 변수에 저장
        3. 새 변수라면 생성, 기존 변수라면 변수에 들어 있는 메모리 주소를 변경
    - **변수는 그 변수가 참조하는 객체의 메모리 주소를 가짐**
- 객체 Object
    - **타입**을 갖는 **메모리 주소** 내 **값**
    - **값이 들어있는 상자**

## Data Types

- 값들을 구분하고 어떻게 다뤄야 하는지 알기 위해 필요
- 타입을 명시적으로 지정하면 변수의 의도를 더 쉽게 이해하고, 잘못된 타입으로 인한 오류를 예방

### Numeric Types

- int
    - 정수자료형
    - 진수 표현 가능
        - 0b10, 0o30, 0x10
- float
    - 실수자료형
    - e 또는 E를 사용한 지수 표현 ex. 314e-2
- **유한 정밀도**
    - 제한된 용량, 2진수의 한계로 float은 실수에 대한 **근삿값**
    - 이 과정에서 **Floating point roundng error (부동소수점 에러)**가 발생함
    
    ```python
    a = 3.2 - 3.1
    b = 1.2 - 1.1
    print(a) # 0.1000..009
    print(b) # 0.0999..987
    print(a==b) # False
    ```
    
    - **decimal 모듈**을 사용해 부동소수점 연산의 정확성을 보장할 수 있음
    
    ```python
    from decimal import Decimal
    a = Decimal('3.2')-Decimal('3.1')
    b = Decimal('1.2')-Decimal('1.1')
    print(a) # 0.1
    print(b) # 0.1
    print(a==b) # True
    ```
    

### Sequence Types

- 여러 개의 값들을 **순서대로 나열**하여 저장하는 자료형
    - 순서 - 값들이 순서대로 저장 (정렬X)
    - 인덱싱 - 각 값에 고유한 인덱스가 있어 특정 위치의 값을 선택, 수정 가능
    - 슬라이싱 - 인덱스 범위 조절해 부분 추출 가능
    - 길이 - `len()` 함수로 저장된 값의 개수(길이) 구함
    - 반복 - 반복문으로 저장된 값들을 반복 처리 가능

### **str** 문자열

- 문자들의 순서가 있는 변경 불가능한 시퀀스 자료
- 따옴표로 감싸서 표현
- 작은따옴표가 들어있는 경우는 큰따옴표로, 반대의 경우는 반대로 문자열 생성
- **Escape sequence**
    - 특수한 기능을 하는 문자 조합, 일반적인 문법 규칙을 잠시 탈출

    | 예약 문자 | 내용(의미) |
    | --- | --- |
    | \n | 줄 바꿈 |
    | \t | 탭 |
    | \\ | 백슬래시 |
    | \’ | 작은 따옴표 |
    | \” | 큰 따옴 |

    ```python
    print('철수야\'안녕\'') # 철수야 '안녕'
    
    '''
    이 다음은 엔터
    입니다.
    '''
    print('이 다음은 엔터\n입니다.')
    ```

- **String Interpolation**
    - 문자열 내 변수나 표현식 삽입
    - **f-string**
    
    ```python
    bugs = 'roaches'
    counts = 13
    area = 'living room'
    
    print(f'Debugging {bugs} {counts} {area}')
    ```
    
- 문자열의 시퀀스 특징
    
    ```python
    my_str = 'hello'
    print(my_str[1])
    print(my_str[2:4])
    print(my_str[:3])
    print(my_str[0:5:2])
    print(my_str[::-1])
    print(len(my_str))
    ```
    
    |  | h | e | l | l | o |
    | --- | --- | --- | --- | --- | --- |
    | index | 0 | 1 | 2 | 3 | 4 |
    | index | -5 | -4 | -3 | -2 | -1 |
- 문자열은 불변(변경 불가)

## 참고

### Style Guide

코드의 일관성과 가독성 향상을 휘안 규칙과 권장 사항들

- 변수명은 직관적으로
    - 영문 알파벳, 언더스토어, 숫자로 구성
    - 숫자로 시작할 수 없음
    - 대소문자 구분
    - 파이썬 내부 예약어 사용 불가
- 공백 4칸으로 코드 블록 들여쓰기
- 한 줄의 길이는 79자로 제한, 길어지면 줄 바꿈
- 문자와 밑줄로 함수, 변수, 속성 이름 작성
- 함수 정의, 클래스 정의 등의 블록 사이에는 빈 줄 추가
- https://peps.python.org/pep-0008/

### Python Tutor

파이썬 프로그램이 어떻게 실행되는지 도와주는 시각화 도우미

https://pythontutor.com/

# Basic Syntax 2

## Data Types - 이어서

### list 리스트

```python
# 리스트 표현
my_list_1 = []
my_list_2 = [1, 'a', 3.5]
my_list = [1, 'a', 3, 'b', 5]

# 인덱싱
print(my_list[1])  # a

# 슬라이싱
print(my_list[2:4])  # [3, 'b']
print(my_list[:3])  # [1, 'a', 3]
print(my_list[3:])  # ['b', 5]
print(my_list[0:5:2])  # [1, 3, 5]
print(my_list[::-1])  # [5, 'b', 3, 'a', 1]

# 길이
print(len(my_list))  # 5

# 중첩된 리스트 접근
my_list = [1, 2, 3, 'Python', ['hello', 'world', '!!!']]
print(len(my_list))  # 5
print(my_list[4][2])  # !!!
print(my_list[4][1][0])  # w

# 리스트는 가변
```

### tuple 튜플

- 여러 개의 값을 순서대로 저장하는 변경 불가능한 시퀀스 자료형
- **단일 요소 튜플을 만들 때는 반드시 Traliling comma (후행 쉼표)**

```python
# 튜플 표현
my_tuple_1 = ()
my_tuple_2 = (1,)
my_tuple_3 = (1, 'a', 3, 'b', 5)

my_tuple = (1, 'a', 3, 'b', 5)

# 인덱싱
print(my_tuple[1])  # a

# 슬라이싱
print(my_tuple[2:4])  # (3, 'b')
print(my_tuple[:3])  # (1, 'a', 3)
print(my_tuple[3:])  # ('b', 5)
print(my_tuple[0:5:2])  # (1, 3, 5)
print(my_tuple[::-1])  # (5, 'b', 3, 'a', 1)

# 길이
print(len(my_tuple))  # 5

# 튜플은 불변
# TypeError: 'tuple' object does not support item assignment
# my_tuple[1] = 'z'
```

- 개발 시 직접적으로 사용하는 경우는 흔치 않음
- 불변 특성을 사용하여 내부 동작과 안전한 데이터 전달에 사용

```python
# 다중 할당
x, y = 10, 20
print(x)  # 10
print(y)  # 20
# 실제 내부 동작
(x, y) = (10, 20)

# 값 교환
x, y = 1, 2
x, y = y, x
# 실제 내부 동작
temp = (y, x)  # 튜플 생성
x, y = temp  # 튜플 언패킹
print(x, y)  # 2 1

# 그룹화
student = ('Kim', 20, 'CS')
name, age, major = student  # 언패킹
print(name, age, major)  # Kim 20 CS
```

### range

- 연속된 **정수** 시퀀스를 생성하는 **변경 불가능**한 자료형

```python
# range
my_range_1 = range(5)
my_range_2 = range(1, 10)
my_range_3 = range(5, 0, -1)

print(my_range_1)  # range(0, 5)
print(my_range_2)  # range(1, 10)
print(my_range_3)  # range(5, 0, -1)

# 리스트로 형 변환 시 데이터 확인 가능
print(list(my_range_1))  # [0, 1, 2, 3, 4]
print(list(my_range_2))  # [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(list(my_range_3))  # [5, 4, 3, 2, 1]

# 값의 범위 규칙

# 음수 증가 시
# 시작 값이 끝 값보다 큰 경우 (정상)
print(list(range(5, 1, -1)))  # [5, 4, 3, 2]
# 시작 값이 끝 값보다 작은 경우
print(list(range(1, 5, -1)))  # []

# 양수 증가 시
# 시작 값이 끝 값보다 작은 경우 (정상)
print(list(range(1, 5)))  # [1, 2, 3, 4]
# 시작 값이 끝 값보다 큰 경우
print(list(range(5, 1)))  # []

# 주로 반복문과 함께 활용 예정
for i in range(1, 10):
    print(i)  # 1 2 3 4 5 6 7 8 9

for i in range(1, 10, 2):
    print(i)  # 1 3 5 7 9
```

### Non-sequence Types

### dict 딕셔너리

key-value 쌍으로 이루어진 순서와 중복이 없는 변경 가능한 자료형

- key는 변경 불가능한 자료형만 사용(str, int, float, tuple, range, …)
- value는 모든 자료형 사용 가능

```python
# 딕셔너리 표현
my_dict_1 = {}
my_dict_2 = {'key':"value"}
my_dict_3 = {'apple':12, 'list':[1,2,3]}
print(my_dict_1)  # 
print(my_dict_2)  # 
print(my_dict_3)  # 

# 딕셔너리는 키에 접근해 값을 얻어냄
my_dict = {'apple' : 12, 'list': [1, 2, 3]}
print(my_dict['apple']) # 12
print(my_dict['list']) # [1, 2, 3]
print(my_dict['list'][1]) # 2

# 추가
my_dict['banana'] = 50
print(my_dict) # {'apple': 12, 'list': [1, 2, 3], 'banana': 50}

# 변경
my_dict['apple'] = 100
print(my_dict) # {'apple': 100, 'list': [1, 2, 3], 'banana': 50}
```

### cf) int와 float는 불변 자료형

- 한 번 생성된 객체 자체는 변경되지 않음
- 값을 변경하는 것처럼 보일 때 사실은 새로운 객체가 생성되고 참조가 변경되는 것
- 불변 자료형인 이유
    - 효율성과 안전성:
    불변 자료형은 객체가 변경되지 않으므로 여러 곳에서 참조하더라도 문제가 없음
    - 해싱 가능성:
    불변 객체는 해시값이 변하지 않으므로, 딕셔너리의 키나 집합의 요소로 사용 가능

### cf) str 불변

- list와 달리, str은 문자열 전체가 하나의 객체로 지정됨
- list는 list 개별 인덱스가 각각 별개의 객체를 참조

### set 세트

- 순서와 중복이 없는 변경 가능한 자료
- 수학에서의 집합과 동일한 연산 처리

```python
# 세트 표현
my_set_1 = set() # dict과 구분분
my_set_2 = {1, 2, 3}
my_set_3 = {1, 1, 1}
print(my_set_1)  # set()
print(my_set_2)  # {1, 2, 3}
print(my_set_3)  # {1}

# 세트의 집합 연산산
my_set_1 = {1, 2, 3}
my_set_2 = {3, 6, 9}

# 합집합
print(my_set_1 | my_set_2)  # {1, 2, 3, 6, 9}

# 차집합
print(my_set_1 - my_set_2)  # {1, 2}

# 교집합
print(my_set_1 & my_set_2)  # {3}
```

### None

값이 없음

```python
# None
variable = None
print(variable)  # None
```

### Boolean

```python
# Boolean
bool_1 = True
bool_2 = False

print(bool_1)  # True
print(bool_2)  # False
print(3 > 1)  # True
print('3' != 3)  # True
```

### Collection

| 컬렉션 | 변경 가능 여부 | 순서 여부 |
| --- | --- | --- |
| str | X | O |
| list | O | O |
| tuple | X | O |
| dict | O | X |
| set | O | X |

순서 O - 시퀀스

## 형변환 Type Conversion

한 데이터 타입을 다른 데이터 타입으로 변환

### 암시적 형변환 Implicit Type conversion

파이썬이 자동으로 수행하는 형변환. Boolean, Numeric Type.

```python
# 암시적 형변환

print(3+5.0) # 8.0
print(True + 3) # 4
print(True + False) # 1
```

### 명시적 형변환 Explicit Type conversion

프로그래머가 직접 지정하는 형변환

```python
# 명시적 형변환

print(int('1')) # 1

# ValueError: invalid literal for int() with base 10: '3.5'
print(int('3.5'))

print(int(3.5)) # 3

print(float('3.5')) # 3.5

print(str(1) + '등') # 1등
```

## 연산자

### 산술 연산자

### 복합 연산자

- 연산과 할당이 함께 이루어짐

### 비교 연산자

- **==**
    - 값(데이터)이 같은지 비교
    - 동등성 equality
- **is**
    - 객체 자체가 같은지 비교
    - 식별성 identity
    - 두 변수가 동일한 메모리 주소(레퍼런스)를 가리키고 있어야 True
    - 코드 상에서 의도치 않게 False가 나오거나 파이썬 버전에 따른 내부 구현 차이 때문에 결과가 달라질 수 있음
    - None을 비교할 때, 싱글턴 객체를 비교할 때 사용
        - None은 파이썬에서 단일 객체로 구성되어 있어, is 연산자 사용이 권장됨
        - 싱글턴 객체는 애플리케이션 전역에서 단 하나의 객체만 존재하며, 모든 코드가 동일한 인스턴스를 공유

```python
# is 비교 연산자
# SyntaxWarning: "is" with a literal. Did you mean "=="?
print(1 is True)  # False
print(2 is 2.0)  # False

# 왜 is 대신 ==를 사용해야 하나?
print(1 is True)  # False
print(2 is 2.0)  # False
print(1 == True)  # True
print(2 == 2.0)  # True

# is 연산자는 언제 사용하는가?
x = None

# 권장
if x is None:
    print('x는 None입니다.')

# 비권장
if x == None:
    print('x는 None입니다.')

# 싱글턴 객체
x = True
y = True

# True, False, None은 실제로 같은 객체를 가리킨다.
print(x is y)  # True
print(True is True)  # True
print(False is False)  # True
print(None is None)  # True

# 추가 예시: 리스트나 객체 비교
a = [1, 2, 3]
b = [1, 2, 3]

print(a == b)  # True (두 리스트의 값은 동일)
print(a is b)  # False (서로 다른 리스트 객체)

# b가 a를 그대로 참조하도록 할 경우
b = a
print(a is b)  # True (같은 객체를 가리키므로 True)
```

### 논리 연산자

- and 논리곱
- or 논리합
- not 논리부정

### 단축평가

논리 연산에서 두번째 피연산자를 평가하지 않고 결과를 결정하는 동작

- and
    - 첫번째 피연산자가 False라면 두번째 피연산자를 무시하고 전체 표현식 False
- or
    - 첫번째 피연산자가 True라면 두번째 피연산자를 무시하고 전체 표현식 True

코드 실행 최적화, 불필요한 연산 단축

```python
# 단축 평가

vowels = 'aeiou'

print(('a' and 'b') in vowels)  # False
print(('b' and 'a') in vowels)  # True

print(3 and 5)  # 5
print(3 and 0)  # 0
print(0 and 3)  # 0
print(0 and 0)  # 0

print(5 or 3)  # 5
print(3 or 0)  # 3
print(0 or 3)  # 3
print(0 or 0)  # 0
```

### 멤버십 연산자

특정 값이 시퀀스나 다른 컬렉션에 속하는지 여부 확

- in
- not in

### 시퀀스형 연산자

- + 결합 연산자
- * 반복 연산자

## 참고

### Trailing Comma

- 컬렉션의 마지막 요소 뒤에 붙는 쉼표
- 선택사항
- 단, 하나의 요소로 구성된 튜플은 필수(int와 구분)
- 가독성 향상
- 유지보수 용이
  
```python
# Good

items = [
item1',
item2',
]

my_func(
value1',
'value2',
)

# Bad

items = ['item1', 'item2',]
my_func('value1','value2',)
```
