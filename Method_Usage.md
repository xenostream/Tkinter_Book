# Tkinter 8.6 Widget Most Usage   

## Common    
```python
from tkinter import *
from tkinter import ttk

root = Tk()

root.mainloop()
```

## Label
```python
label.pcak()
label = ttk.Label(root, text='Hello Tkinter')

label.config(text='Change Dynamic Text')
label.config(wraplength=150)
label.config(foreground='blue', background='yellow')
label.config(font=('Courier', 18, 'bold'))
logo = PhotoImage(file='img.gif')
label.config(image=logo)
label.config(compound='text')
label.config(compound='letf')
label.config(compound='center')
label.image = logo  # Because Garbage Collect
```


## Button
```python
button = ttk.Button(root, text='Click Me')

def callback():
    print('Clicked')

button.config(common=callback)
button.invoke()   # simulate button Click
button.state(['disabled'])
button.instate(['disabled'])
button.state(['!disabled'])
button.instate(['!disabled'])
logo = PhotoImage(file='img.gif')
button.config(image=logo, compound=LEFT)
small_logo =  logo.subsample(5, 5)
button.config(image=small_logo)
```


## Button Selections
```python
checkbutton = ttk.Checkbutton(root, text='SPAM?')

sapm = StringVar()
spam.set('SPAM!')
spam.get()
checkbutton.config(variable=spam, onvalue='SPAM pelase', offvalue='Boo SPAM')
breakfast = StringVar()
ttk.Radiobutton(root, text='SPAM',variable=breakfast, value='SPAM').pack()
ttk.Radiobutton(root, text='Eggs',variable=breakfast, value='Eggs').pack()
ttk.Radiobutton(root, text='Sausage',variable=breakfast, value='Sausage').pack()
ttk.Radiobutton(root, text='SPAM',variable=breakfast, value='SPAM').pack()
checkbutton.config(textvariable=breakfast)
```


## Entry
```python
entry = ttk.Entry(root, width=30)

entry.get()
entry.delete(0, 1)
entry.delete(0, END)
entry.insert(0, 'Enter your Password')
entry.config(show = '*')
entry.state(['disabled'])
entry.state(['!disabled'])
entry.state(['readonly'])
```

## Selection baxes
```python
month = StringVar()
combobox = ttk.Combobox(root, textvariable=month)

combobox.config(values=('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', \
                        'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'))
month.get()
month.set('Dec')
month.set('Not a month')
year = StringVar()
Spinbox(root, from_=1999, to=2017, textvariable=year).pack()
year.get()
```

## Progressbar
```python
progressbar = ttk.Progressbar(root, orient=HORIZONTAL, length=200)

progressbar.config(mode='indeterminate')
progressbar.start()
progressbar.stop()
progressbar.config(mode='determinate', maximum=11.0, value=4.2)
progressbar.config(value=8.0)
progressbar.step()
progressbar.step(5)
value = DoubleVar()
progressbar.config(variable=value)
scale = ttk.Scale(root, orient=HORIZONTAL, length=400, variable=value, \
                from_=0.0, to=11.0)
scale.set(4.2)
```

## Frame
```python
frame = ttk.Frame(root)
frame.pack()

frame.config(width=200, height=100)
# FLAT, RAISED, SUNKEN, SOLID, RIDGE, GROOVE
frame.config(relief=RIDGE)
ttk.Button(frame, text='Click Me').grid()
frame.config(padding=(30, 15))
ttk.LabelFrame(root, height=100, width=200, text='My Frame').pack()
```


## Toplevel Window
```python
from tkinter import *
root = Tk()

window = Toplevel(root)
window.title('New Window')
window.lower()
window.lift(root)
window.state('zoomed')
window.state('withdrawn')
window.state('iconic')
window.state('normal')
window.state()
window.iconify()
window.deiconify()
window.geometry('400x300+100+200')
window.resizable(width=False, height=False) # (False, Flase)
window.maxsize(640, 480)
window.minsize(320, 240)
window.resizable(True, True)
root.destroy() 
```


## Panedwindow
```python
panedwindow = ttk.Panedwindow(root, orient=HORIZONTAL)
panedwindow.pack(fill = BOTH, expand=Ture)

frame1 = ttk.Frame(panedwindow, width=100, height=300, relief=SUNKEN)
frame2 = ttk.Frame(panedwindow, width=400, height=400, relief=SUNKEN)
panedwindow.add(frame1, weight=1)
panedwindow.add(frame2, weight=4)
frame3 = ttk.Frame(panedwindow, width=50, height=400, relief=SUNKEN)
panedwindow.insert(1, frame3)
panedwindow.forget(1)   # not visible only
```

## Notebook
```python
notebook = ttk.Notebook(root)
notebook.pack()

frame1 = ttk.Frame(notebook)
frame2 = ttk.Frame(notebook)
notebook.add(frame1, text='One')
notebook.add(frame2, text='Two')
ttk.Button(frame1, text='Click Me').pack()
frame3 = ttk.Frame(notebook)
notebook.insert(1, frame3, text='Tree')
notebook.forget(1)
notebook.add(frame3, text='Three')
notebook.select()  # .45443434.4334344
notebook.index(notebook.select())
notebook.select(2)
notebook.tab(1, state='disabled')
notebook.tab(1, state='hidden')
notebook.tab(1, state='normal')
notebook.tab(1, 'text')  # Two
notebook.tab(1)
```


## Text
```python
text = Text(root, width=40, height=10)
text.pack()

text.config(wrap='word') # none, char
# line.char, end 
# +/-# chars and +/-# lines
# linestart, lineend, wordstart, wordend
text.get('1.0', 'end')
text.get('1.0', '1.end')
text.insert('1.0 + 2 lines', 'Inserted Message')
text.insert('1.0 + 2 lines lineend', 'and\nmore and\nmore...')
text.delete('1.0')
text.delete('1.0', '1.0 lineend')
text.delete('1.0', '3.0 lineend + 1 chars')
text.replace('1.0', '1.0 lineend', 'This is the first line.')
text.config(state='disabled')   # Read only
text.delete('1.0', 'end')
text.config(state='normal')
```

## Text Advanced
```python
text.tag_add('my_tag', '1.0', '1.0 wordend')
text.tag_configure('my_tag', background='yellow')
text.tag_remove('my_tag', '1.1', '1.3')
text.tag_ranges('my_tag')
text.tag_names()  # 'sel' , 'my_tag'
text.tag_names('1.0')  # 'my_tag'
text.replace('my_tag.first', 'my_tag.last', 'That')
text.tag_delete('my_tag')
text.mark_names() # insert : cursor current : mouse point
text.insert('insert', '_')
text.mark_set('my_mark', 'end')
text.mark_gravity('my_mark', 'right')
text.mark_unset('my_mark')
image = PhotoImage(file='img.gif')
text.image_create('insert', image=image)
button = Button(text, text='Click Me')
text.window_create('insert', window=button) 
```


## Treeview
```python
treeview = ttk.Treeview(root)
treeview.pack()

treeview.insert('', '0', 'item1', text='First Item')
treeview.insert('', '1', 'item2', text='Second Item')
treeview.insert('', 'end', 'item3', text='Third Item')
logo = PhotoImage(file='img.gif').subsample(10, 10)
treeview.insert('item2', 'end', 'python', text='Python', image=logo)
treeview.config(height=5) # total row
treeview.move('item2', 'item1', 'end')
treeview.item('item1', open=True) 
treeview.item('item1', 'open')  # 1 = True 
treeview.detach('item3')  # invisible
treeview.move('item3', 'item2', '0')
treeview.delete('item3')
```

## Treeview Advanced
```python
treeview.config(columns=('version'))
treeview.column('version', width=50, anchor='center')
treeview.column('#0', width=50)
treeview.heading('version', text='version')
treeview.set('python', 'version', '3.6.0') 
treeview.item('python', tags=('software'))
treeview.tag_configure('software', background='yellow')
def callback(event):
    print(treeview.selection())
treeview.bind('<<TreeviewSelect>>', callback)
treeview.config(selectmode='browse') # only one item select 
treeview.config(selectmode='none')
treeview.selection_add('python') 
treeview.selection_remove('python') # deselect 
treeview.selection_toggle('python')
```

## Menu
```python
root = Tk()
root.option_add('*tearoff', False)
menubar = Menu(root)
root.config(menu=menubar)

file = Menu(menubar)
edit = Menu(menubar)
help_ = Menu(menubar)  # help is Reserved word 
menubar.add_cascade(menu=file, label='File')
menubar.add_cascade(menu=edit, label='Edit')
menubar.add_cascade(menu=help_, label='Help')
file.add_command(label='New', command=lambda: print('New File'))
file.add_separator()
file.add_command(label='Open,...', command=lambda: print('Open File'))
file.add_command(label='Save', command=lambda: print('Save File'))
file.entryconfig('New', accelerator='Ctrl+N')
logo = PhotoImage(file='img.gif').subsample(10, 10)
file.entryconfig('Open...', image=logo, compound='left')
file.entryconfig('Open...', state='disabled') 
file.delete('Save')
save = Menu(file)
file.add_cascade(menu=save, label='Save')
save.add_command(label='Save As', command=lambda: print('Saving As...'))
save.add_command(label='Save All', command=lambda: print('Saving All...'))
choice = IntVar()
edit.add_radiobutton(label='One', variable=choice, value=1)
edit.add_radiobutton(label='Two', variable=choice, value=2)
edit.add_radiobutton(label='Three', variable=choice, value=3)
file.post(400, 300)
```

## Canvas
```python
canvas = Canvas(root)
canvas.pack()

canvas.config(width=640, height=480)
line = canvas_create_line(160, 360, 480, 120,fill='blue', width=5)
canvas.itemconfigure(line, fill='green')
canvas.coords(line)
canvas.coords(line, 0, 0, 320, 240, 640, 0)
canvas.itemconfigure(line, smooth=True)
canvas.itemconfigure(line, splinesteps=5)
canvas.itemconfigure(line, splinesteps=100)
canvas.delete(line)
```

## Canvas Advanced
```python
rect = canvas.create_rectangle(160, 120, 480, 360)
canvas.itemconfigure(rect, fill='yellow')
oval = canvas.create_oval(160, 120, 480, 360)
arc = canvas.create_arc(160, 1, 480, 240)
canvas.itemconfigure(arc, start=0, extent=180, fill='green')
poly = canvas_create_polygon(160, 360, 320, 480, 480, 360, fill='blue')
text = canvas.create_text(320, 240, text='Python', font=('Courier', 32, 'bold'))
logo = PhotoImage(file='img.gif')
image = canvas.create_image(320, 240, image=logo)
canvas.lift(text)
canvas.lower(image)
canvas.lower(image, text)
button = Button(canvas, text='Click Me')
canvas.create_window(320, 60, window=button)
canvas.itemconfigure(rect, tag=('shape'))
canvas.itemconfigure(oval, tag=('shape', 'round'))
canvas.itemconfigure('shape', fill='grey')
canvas.gettags(oval)
```

## Scrollbar
```python
text = Text(root, width=40, height=10, wrap='word')
text.grid(row=0, column=0)

scrollbar = ttk.Scrollbar(root, orient=VERTICAL, command=text.yview)
scrollbar.grid(row=0, column=1, sticky='ns')
text.config(yscrollcommand=scrollbar.set) # Link each other
# X : Text Canvas Treeview Entry Spinbox Combobox 
# Y : Text Canvas Treeview 
canvas = Canvas(root, scrollregion=(0, 0, 640, 480), bg='white')
xscroll = ttk.Scrollbar(root, orient=HORIZONTAL, command=canvas.xview)
yscroll = ttk.Scrollbar(root, orient=VERTICAL, command=canvas.yview)
canvas.config(xscrollcommand=xscroll.set, yscrollcommand=yscroll.set)
canvas.grid(row=1, column=0)
xscroll.grid(row=2,column=0, sticky='ew')
yscroll.grid(row=1, column=1, sticky='ns')
def canvas_click(event):
    x = canvas.canvasx(event.x) 
    y = canvas.canvasy(event.y) 
    canvas.create_oval((x-5, y-5, x+5, y+5), fill='green')
canvas.bind('<1>', canvas_click)
```

## Style
```python
# Widget State : active disabled focus pressed selected backgound readonly
#                alternate invalid hover
button1 = ttk.Button(root, text='Button1')
button2 = ttk.Button(root, text='Button2')
button1.pack()
button2.pack()

style = ttk.Style()
style.theme_names() # winnative, clam, alt, default, classic,vista, xpnative
style.theme_use()  # vista 
style.theme_use('classic')
style.theme_use('vista')
# Widget Style Name : T + widgetName => Treeview(no T), TPanedwindow, 
#                     Horizontal.TProgressbar Vertical.TProgressbar 
button.winfo_class() # TButton 
style.configure('TButton', foreground='blue')
style.configure('Alarm.TButton', foreground='orange', font=('Arial', 24, 'bold'))
button2.config(style='Alarm.TButton')
style.map('Alarm.TButton', foreground=[('pressed', 'pink'), ('disabled', 'grey')])
button2.state(['disabled'])
style.layout('TButton') # Return All setting  
style.element_options('Button.label') # Return option of widget
style.lookup('TButton', 'foreground') # blue 
```

## Dialog
```python
# Don't use Tk()
from tkinter import messagebox

messagebox.showinfo(title='A Friendly Message', message='Hello Tkinter')
# showinfo() showwarning() showerror()
messagebox.askyesno(title='Hungry?', message='Do you want SPAM?')
# askyesno() askokcancel() askretrycancel() askyesnocancel() askquestion() 

from tkinter import filedialog
filename = filedialog.askopenfile() 
filename.name # full path
# askdirectory() asksaveasfile(mode) asksaveasfilename()
# askopenfile(mode) askopenfiles(mode) askopenfilename() askopenfilenames()

from tkinter import colorchooser
colorchooser.askcolor(initialcolor='#FFFFFF')
```

## Pack 
```python
ttk.Label(root, text='Hello, Tkinter!', backgound='yellow').pack()
ttk.Label(root, text='Hello, Tkinter!', backgound='yellow').pack(fill=X) # Y BOTH 
ttk.Label(root, text='Hello, Tkinter!', backgound='yellow').pack(fill=BOTH, expand=True)
ttk.Label(root, text='Hello, Tkinter!', backgound='blue').pack(fill=BOTH)
ttk.Label(root, text='Hello, Tkinter!', backgound='green').pack(fill=BOTH, expand=True)

ttk.Label(root, text='Hello, Tkinter!', backgound='yellow').pack(side=LEFT) # RIGHT BOTTOM TOP 
ttk.Label(root, text='Hello, Tkinter!', backgound='yellow').pack()side=LEFT, anchor='nw')

ttk.Label(root, text='Hello, Tkinter!', backgound='yellow').pack(padx=10, pady=10)
ttk.Label(root, text='Hello, Tkinter!', backgound='yellow').pack(ipadx=10,ipady=10)

for widget in root.pack_slaves():
    widget.pack_configure(fill=BOTH, expand=True)
    print(widget.pack_info())

label.pack_forget()
```

## Grid 
```python
ttk.Label(root, text='Yellow', background='yellow').grid(row=1,column=1)
ttk.Label(root, text='Blue', background='blue').grid(row=1, column=0)
ttk.Label(root, text='Green', background='green').grid(row=0, column=0)
ttk.Label(root, text='Oragne', background='orange').grid(row=0, column=1)

ttk.Label(root, text='Yellow', background='yellow').grid(row=0,column=2, rowspan=2, stick='nsew')
ttk.Label(root, text='Blue', background='blue').grid(row=1, column=0, columnspan=2, sticky='e')
ttk.Label(root, text='Green', background='green').grid(row=0, column=0, stick='nsew')
ttk.Label(root, text='Oragne', background='orange').grid(row=0, column=1, stick='nsew')

root.rowconfigure(0, weight=1)   # Strech
root.rowconfigure(1, weight=3)
root.columnconfigure(2, weight=1)

ttk.Label(root, text='Yellow', background='yellow').grid(row=1,column=1, padx=10, pady=10) # ipadx, ipady
grid_slaves()
grid_configure()
grid_info()
grid_forget()
```

## Place 
```python
root.geometry('640x480+200+200')

ttk.Label(root, text='Yellow', background='yellow').place(x=100, y=50, width=100, height=50)
ttk.Label(root, text='Blue', background='blue').place(relx=0.5, rely=0.5, anchor='center', relwidth=0.5, relheight=0.5)
ttk.Label(root, text='Green', background='green').place(relx=0.5, x=100, rely=0.5, y=50)
ttk.Label(root, text='Orange', background='orange').place(relx=1.0, x=-5, y=5, anchor='ne')
```

## Callback Function
```python

def callback():
    print('In the Callback')
ttk.Button(root, text='Click Me', command=callback).pack()

def callback(nubmer):
    print(number)
ttk.Button(root, text='Click Me 1', command=lambda: callback(1)).pack()
ttk.Button(root, text='Click Me 2', command=lambda: callback(2)).pack()
ttk.Button(root, text='Click Me 3', command=lambda: callback(3)).pack()
# Commnad callback widget  : Button Checkbutton Radiobutton Spinbox Scale Scrollbar
```

## Keyboard Event
```python

def key_press(even):
    print('type: {}'.format(event.type))
    print('widget: {}'.format(event.widget))
    print('char: {}'.format(event.char))
    print('keysym: {}'.format(event.keysym))
    print('keycode: {}'.format(event.keycode))

root.bind('<KeyPress>', key_press)
# <Key> <KeyPress> <KeyPress-Delete> <KeyRelease-Right>...
# <Return> <Control-Alt-Next> <Shift_L> <Control-R> ...

def shortcut(action):
    print(action)

root.bind('<Control-c>', lambda e: shortcut('Copy'))
root.bind('<Control-v>', lambda e: shortcut('Paste'))
```


## Mouse Event
```python
canvas = Canvas(root, width=640, height=480, background='white')
canvas.pack()

# <Button> <ButtonPress> <Button-1> <ButtonPress-1> <Double-Button-1> <Triple-Button-1>
def mouse_press(evnet):
    global prev
    prev = event
    print('type: {}'.format(event.type))
    print('widget: {}'.format(event.widget))
    print('num: {}'.format(event.num))
    print('x: {}'.format(event.x))
    print('y: {}'.format(event.y))
    print('x_root: {}'.format(event.x_root))
    print('y_root: {}'.format(event.y_root))

def draw(event):
    global prev
    canvas.create_line(prev.x, prev.y, event.x, event.y, width=5)

canvas.bind('<ButtonPress>', mouse_press)
canvas.bind('<B1-Motion>', draw)
```

## Virtual Event 
```python
entry = ttk.Entry(root)
entry.pack() 

entry.bind('<<Copy>>', lambda e: print('Copy'))
entry.bind('<<Paste>>', lambda e: print('Paste'))
entry.event_add('<<OddNumber>>', '1', '3', '5', '7', '9')
entry.bind('<<OddNumber>>', lambda e: print('Odd Number'))
print(entry.event_info('<<OddNumber>>'))
entry.event_generate('<<OddNumber>>')
entry.event_generate('<<Paste>>')
entry.event_delete('<<OddNumber>>')
```

## Multiple Event 
```python
label1 = ttk.Label(root, text='Label 1')
label2 = ttk.Label(root, text='Label 2')
label1.pack()
label2.pack()

label1.bind('<ButtonPress>', lambda e: print('<ButtonPress> Label'))
label1.bind('<1>', lambda e: print('<1> Label'))
root.bind('<1>', lambda e: print('<1> Root'))
label1.unbind('<1>')
label1.unbind('<ButtonPress>')
root.bind_all('<Escape>', lambda e: print('Escape'))
```






































