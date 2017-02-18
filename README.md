# Part I. IntroductionChapter 

## 1. What's TkinterTkinter 

모듈("Tk 인터페이스")은 Scriptics(Sun Labs)의   
Tk GUI 툴킷에 대한 표준 Python 인터페이스입니다.   

Tk와 Tkinter는 대부분의 Unix 플랫폼과 Windows 및 Macintosh      
시스템에서 사용할 수 있습니다.       
8.0 Release부터 Tk는 모든 플랫폼에서 기본적인 룩앤필을 제공합니다.   

Tkinter는 여러가지 모듈로 구성됩니다.   
Tk 인터페이스는 **tkinter**라는 2진 확장 모듈에 의해 제공됩니다.      
이 모듈은 Tk에 대한 저수준 인터페이스를 포함하고 있으므로 응용 프로그램 프로그래머가     
직접적으로 사용해서는 안됩니다.일반적으로 공유 라이브러리(.so, .DLL)형태로 존재하지만,    
경우에 따라서 Python 인터프리터와정적으로 링크될 수도 있습니다.    

공용 인터페이스는 여러개의 Python 모듈을 통해 제공됩니다.    
가장 중요한 인터페이스 모듈은 Tkinter 모듈 자체입니다.    

Tkinter를 사용하려면, Tkinter 모듈을 import 하면됩니다.    

```python
import tkinter
```

또는    

```python
from tkinter import *
```

Tkinter 모듈은 위젯 클래스와 관련된 상수만 노출하므로 대부분의 경우에서     
이방식의 import는 안전하게 사용할 수 있습니다.      
반드시 필요한것은 아니지만,다음과 같이 단축형식을 사용해도 됩니다.    

```python
import tkinter as tk
```
