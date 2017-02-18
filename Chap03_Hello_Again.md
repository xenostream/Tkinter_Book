##Chapter 3. Hello, Again!

큰 프로그램을 작성할 때 일반적으로 하나 이상의 클래스에서 코드를 나눠서 저장하는 것이 좋습니다.     
다음의 예는 Matt Conway의 Tkinter Life Preserver의 "hello world"프로그램에서 발췌 한 것입니다.
 
### 두 번째 Tkinter 프로그램

```python 
from tkinter import *

class App:

    def __init__(self, master):
        
        frame = Frame(master)
        frame.pack()

        self.button = Button(
            frame, text="QUIT", fg="red", command=frame.quit)
        self.button.pack(side=LEFT)

        self.hi_there = Button(frame, text="Hello", command=self.say_hi)
        self.hi_there.pack(side=LEFT)

    def say_hi(self):
        print "hi there, everyone!"

root = Tk()
app = App(root)
root.mainloop()
root.destroy() # optional
```

### 프로그램 실행 (Windows Tk 8.6 사용)
 

오른쪽 버튼(**Hello**)을 클릭하면 `"hi there, everyone!"`이라는 텍스트가 콘솔에 표시됩니다.       
왼쪽 버튼(**Quit**)을 클릭하면 프로그램이 종료됩니다.


>참고 : 일부 Python 환경에서는 상기의  Tkinter 예제를 실행하는 데 문제가 있습니다.    
 일반적인 환경에서는 Tkinter 자체를 사용하며 주 이벤트루프  함수 호출과 종료 함수 호출은       
 환경의 일반적인 작동과  상호 작용합니다.     
 상기예제에서와 같이 명시적으로 `Destory()`함수호출을 정상적으로 작동합니다.      
 하지만, 만약 종료작업이 정상적으로 되지 않는다면 상기와 같이 사용하시기 바랍니다. 



### 세부사항

> 이 응용 프로그램은 *클래스*로 작성됩니다.       

생성자(**__init__**)는 부모 위젯 (master)과 함께 호출되며, 여기에 여러개의 자식 위젯이 추가됩니다.     
생성자는 프레임 위젯을 생성하며 시작합니다.    
`프레임`은 단순히 컨테이너이며,이 경우 다른 두 위젯을 묶어두는 역할로 사용됩니다.    
```python
class App:
    def __init__(self, master):
        frame = Frame(master)
        frame.pack()
```

프레임 인스턴스는 frame이라는 `로컬 변수`에 저장됩니다.     
위젯을 생성 한 후에는 곧바로 `pack 메소드`를 호출하여 프레임을 화면에 표시합니다.     
그런 다음 두 개의 Button 위젯을 프레임의 하위 위젯으로 만듭니다.

```python
self.button = Button(frame, text="QUIT", fg="red", command=frame.quit)
self.button.pack(side=LEFT)

self.hi_there = Button(frame, text="Hello", command=self.say_hi)
self.hi_there.pack(side=LEFT)
```

이번에는 생성자(**__init__**)에 여러 가지 옵션을 키워드 인수로 전달합니다. 
첫 번째 버튼에는 "Quit"라는 레이블이 지정되고 빨간색으로 표시됩니다 (fg는 foreground).      
두 번째 항목은 "Hello"로 표시됩니다. 두 버튼 모두 명령옵션(`command`)을 사용합니다.      
이 옵션은 함수명을  지정하거나(이 경우), 버튼을 클릭 할 때 호출되는 *바인드드 메서드*를 지정합니다.    

버튼 인스턴스는 인스턴스 속성에 저장됩니다. 그들은 모두 화면에 포장(pack)되지만,      
이번에는  `side=LEFT`옵션을 사용했습니다.  즉, 프레임에서 가능한 한 왼쪽으로 배치됩니다.      
첫 번째 단추는 프레임의 왼쪽 가장자리에 배치되고 두 번째 단추는 첫 번째 단추의 바로 오른쪽에      
배치됩니다 (즉, 프레임의 나머지 공간의 왼쪽 가장자리에 위치).      
기본적으로 위젯은 부모 (프레임 위젯의 마스터이고 버튼의 프레임 자체)를 기준으로 포장됩니다. 
`side 옵션`이 지정되지 않으면, 기본값은 **TOP**입니다.

"hello"버튼을 누르면실행하는  콜백함수는 다음과 같이 구현됩니다.    
버튼을 누를 때마다 단순히 콘솔에 메시지를 출력합니다.
```python
def say_hi(self):
    print "hi there, everyone!"
```

마지막으로 Tk 루트 위젯을 생성하는 코드와 루트 위젯을 부모로 사용하는 App 클래스 인스턴스를 
제공합니다.      
```python
root = Tk()

app = App(root)

root.mainloop ()
root.destroy ()
```

mainloop 호출은 종료 메소드가 호출 될 때까지 응용 프로그램이 유지하는 `Tk 이벤트 루프`를      
시작합니다 (QUIT). 이 루틴을 실행하지 않는다면, 윈도우가 곧바로 닫힙니다.

destory() 호출은 특정한  환경에서 실행하는 경우에만 필요합니다.    
이벤트 루프가 종료 될 때 메인윈도우를 명시적인 명령으로 종료합니다. 일부 환경에서는    
이 메소드를 실행하지 않으면,  프로그램이 종료되지 않는 현상이 발생합니다. 

### 위젯에 대한 추가 정보

두 번째 예제에서 프레임 위젯은 frame이라는 로컬 변수에 저장되는 반면 버튼 위젯은 두 개의      
인스턴스 변수에 저장됩니다. 여기에 다음과 같은 심각한 문제가 발생할 수 있습니다.     
 
 > **__init__** 생성자메소드가 반환되고  frame변수가 범위를 벗어날 때 어떤 일이 발생합니까?

**걱정하지 마시기바랍니다.**    
실제로는 위젯 인스턴스에 대한 참조를 별도로 유지할 필요가 없습니다.     
Tkinter는 (각 위젯 인스턴스의 마스터 및 하위 속성) 위젯 트리를 자동으로 관리하므로      
애플리케이션의 마지막 참조값이  사라져도 위젯이 사라지지 않습니다.    
실제로 파기할려면 명시적으로 파기해야합니다 (destroy 메소드 사용). 
그러나 위젯을 만든 후에 위젯을 사용하여 어떠한 작업하려면 위젯 인스턴스에 대한 참조값     
변수를 만들어서 보관하는 것이 좋습니다.

만약, 위젯에 대한 참조변수를 유지할 필요가 없다면, 
다음과 같이 한 줄에 만들고 포장하는 것도 가능합니다.      
```python
Button(frame, text="Hello",  command=self.hello).pack (side=LEFT)
```

> 이 명령의 리턴값을 저장하지 마십시오.     

 만약, 상기에 사용한 코드에서 리턴값을 사용하려고하면 실망하게 될 것입니다.   
 
 > **pack() 메소드는 None을 반환합니다.** 
 
그래서 안전한 코드를 작성하려면 항상 인스턴스생성과 포장을 분리하는 것이 좋습니다.      
```python
w = Button(frame, text="Hello", command=self.hello)
w.pack(side=LEFT)
```


### 위젯 이름에 대한 추가 정보

만약 `Tcl`을 사용해서 Tk를 프로그래밍한 경험이있는 사람들의 혼란은     
Tkinter의 위젯이름 개념입니다. Tcl에서는 명시적으로 각 위젯의 이름을 지정해야만 합니다.       
예를 들어, 다음 Tcl 명령은 "ok"라는 버튼을 "dialog"라는 위젯 (루트 윈도우: ".")의 하위 노드로 만듭니다.  
```tcl
button .dialog.ok
```

동일한 Tkinter방식의  호출은 다음과 같습니다.
```python
ok = Button(dialog)
```

그러나 Tkinter의 경우 ok와 dialog는 실제 위젯 이름이 아닌 위젯 인스턴스에 대한 참조입니다.      
Tk가 이름을 필요로하기 때문에,  Tkinter는 새로운 위젯마다 고유 한 이름을 자동으로 할당합니다.    
위의 경우 대화 상자 이름은 아마도 ".1428748"과 같으며 버튼의 이름은 ".1428748.1432920"입니다.     Tkinter 위젯의 전체 이름을 얻으려면 위젯 인스턴스에서 str() 함수를 사용하기만 하면됩니다.   
```
>>> print str(ok)
.1428748.1432920
```

뭔가를 출력하게되면, 파이썬은 자동으로 str() 함수를 사용해서 무엇을 인쇄 할지를 결정합니다. 
그러나 분명히 "name = ok"와 같은 연산은 이방식으로 작동하지 않으므로 이름이 필요할 경우      
항상 str()을 명시적으로 사용해야합니다.

위젯의 이름을 지정해야하는 경우, 위젯을 만들 때 name 옵션을 사용할 수 있습니다. 
이방식이 필요한 이유 중 하나는 Tcl로 작성된 코드와 인터페이스해야하는 경우입니다.

다음 예제에서,  결과 위젯 이름은 ".dialog.ok"입니다 .     
(만약 dialog의 이름을 잊어 버린 경우라면 ".1428748.ok"와 같은 것으로 표시됩니다).
```python
ok = Button(dialog, name="ok")
```

> Tkinter의 명명 체계와의 충돌을 피하려면 숫자만 포함 된 이름을 사용하지 마십시오. 
> 또한 이름은 "생성 전용" 옵션입니다.  위젯을 한번 만들면 이름을 변경할 수 없습니다.