# Jupyter notebook 사용하기



## 1.1 Jupyter notebook 이란?

>Jupyter notebook은 웹 브라우저 기반의 소스편집 도구이다.





## 1.2  Jupyter notebook 설치 및 실행 방법



### 1.2.1 설치 방법

>1. Anaconda와 함꼐 설치하는 방법
>
>   >Anaconda를 설치할 떄  Jupyter notebook도 같이 설치된다.
>
>2. pip를 사용하여  Jupyter notebook을 설치한다.
>
>   ```python
>   pip install jupyter		
>   ```



### 1.2.2 실행

> 1. Anaconda Prompt(Anaconda3)를 실행시킨다.
>
>    ![image-20210715131723857](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210715131723857.png)
>
> 2. cmd 창에 jupyter notebook을 입력후 엔터를 누른다.
>
>    ![image-20210715131851518](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210715131851518.png)
>
> 3. 웹브라우저가 실행되면서 Jupyter notebook을 사용할수 있다.
>
>    ![image-20210715131956645](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210715131956645.png)



### 1.3 Jupyer notebook의 기본 사용방법

> ### 1.3.1 새 파일 생성
>
> ​		 ![image-20210715132413283](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210715132413283.png)
>
> 클릭 순서대로 실행을하면 Python3 코드를 입력할 수 있는 창이 열린다.
>
> ![image-20210715132531747](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210715132531747.png)
>
> 생성을 하게 되면 기본적으로 Untitled 라는 제목으로 생성이된다.  
>
> Jupyter notebook을 설치한 곳에 파일이 저정된다. 
>
> <img src="C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210715132840844.png" alt="image-20210715132840844" style="zoom:50%;" />
>
> 필자는 이미 하나 생성되어있어  Untitled1로 생성된 파일을 볼수있다.
>
> 
>
> ### 1.3.2 편집/명령 모드
>
> 편집 모드에서는 셀의 내용을 편집할 수 있고(셀의 테두리가 초록색), 명령 모드는 편집 중인 상태가 아니라 셀 자체에 조작을 할 수 있는 상태(셀의 테두리가 파란색)이다.
>
> 
>
> ### 1.3.3 셀의 타입
>
> 1. Code 타입 
>
>    Code타입은 일반 코드를 실행할 수 있는 셀이다. 기본적으로 셀을 생성하면 Code 타입으로생선된다.
>
> 2. Markdown타입
>
>    Markdown타입은 Markdown으로 셀의 내용을 작성할 수 있다. 코드로 실행되지는 않으면 수식을 작성할 수있다. 주석같은 용도로 사용할 수 있다.
>
>    ![image-20210715133528724](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210715133528724.png)
>
>    Code 타입 이였을때는 코드창 옆에 In []이라는 것을 볼수있지만 Markdown타입 이였을때는 In[]이 없는 것을 볼 수 있다.
>
> ### 1.3.4 셀 실행
>
> 실행하고 싶은 셀의 아무곳에서나 커서를 위치시킨후 `Shift`+`enter`를 입력하면 셀이 실행이 될 수 있다. 실행하면 셀 아래쪽에 실행 결과가 표시되고, 셀 옆의 `In[]` 과 `out[]`에 몇 번째로 실행시켰고 출력되었는지를 나타내는 숫자가 나타난다.
>
> ![image-20210715134022817](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210715134022817.png)
>
> 



##  1.4 Jupyter notebook 의 단축키

>  Jupyter notebook 사용 시 평소 자주 소용하는 단축키 모음은 `[Help]`-`[keyboard Shortcus]`또는 명령 모드에서 `H`를 놀러서 표시할 수 있다.
>
> | 공용 단축키 | 설명                                            |
> | ----------- | ----------------------------------------------- |
> | Shift+Enter | 엑티브 셀을 실행하고 아래 셀을 선택한다.        |
> | Ctrl+Enter  | 엑티브 셀을 실행한다.                           |
> | Alt+Enter   | 엑티브 셀을 실행하고 아래에 셀을 하나 생성한다. |
> | Shift+Tab   | 툴팁 또는 변수의 상태를 표시한다.               |
>
> | 명령 모드 단축키 | 설명                                        |
> | ---------------- | ------------------------------------------- |
> | A                | 엑티브 코드 셀의 위에 셀을 하나 생성한다.   |
> | B                | 엑티브 코드 셀의 아래에 셀을 하나 생성한다. |
> | DD               | 엑티브 코드 셀을 삭제한다.                  |
> | Z                | 이전에 삭제한 코드 셀을 하나 복원한다.      |
> | Y                | 엑티브 코드 셀을 Code타입으로 변환한다.     |
> | M                | 엑티브 코드 셀을 Markdown타입으로 변환한다. |
> | OO               | 커널을 재시작한다.                          |
> | H                | 단축키 목록을 표시한다.                     |
>
> 

