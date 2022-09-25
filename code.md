```python
from tkinter import *
import tkinter.messagebox as msgbox
opt = ['mm', 'cm', 'm', 'in', 'ft', 'yd', 'km', 'mile(s)']
a = 'mm'

root = Tk()
click = StringVar()
root.geometry("330x420")
root.title('단위 통일')

def get1():
    if en1.get() == '':
        return msgbox.showinfo("메세지창", "값 없음")
    try:
        float(en1.get())
    except:
        return msgbox.showinfo("메세지창", "실수아님")
    a = click.get()
    if a == 'mm':
        lbl1['text'] = '    ' + str(float(en1.get())*0.001) + '(m)'
    elif a == 'cm':
        lbl1['text'] = '    ' + str(float(en1.get())*0.01) + '(m)'
    elif a == 'm':
        lbl1['text'] = '    ' + str(float(en1.get())) + '(m)'
    elif a == 'in':
        lbl1['text'] = '    ' + str(float(en1.get())/39.37) + '(m)'
    elif a == 'ft':
        lbl1['text'] = '    ' + str(float(en1.get())/3.2808) + '(m)'
    elif a == 'yd':
        lbl1['text'] = '    ' + str(float(en1.get())/1.936) + '(m)'
    elif a == 'km':
        lbl1['text'] = '    ' + str(float(en1.get())*1000) + '(m)'
    elif a == 'mile(s)':
        lbl1['text'] = '    ' + str(float(en1.get())/0.00062) + '(m)'
def get2():
    if en5.get() == '':
        return msgbox.showinfo("오류", "분모 값 없음")
    if en4.get() == '':
        return msgbox.showinfo("오류", "분자 값 없음")
    try:
        int(en7.get())
        int(en4.get())
        int(en5.get())
    except:
        return msgbox.showinfo("오류", "자연수 아님")
    lbl4['text'] = en5.get()
    lbl3['text'] = int(en5.get()) * int(en7.get()) + int(en4.get())
def get3():
    if en2_1.get() == '':
        return msgbox.showinfo('오류', '분모 값 없음')
    if en2_2.get() == '':
        return msgbox.showinfo('오류', '분자 값 없음')
    try:
        int(en2_1.get())
        int(en2_2.get())
    except:
        return msgbox.showinfo('오류', '자연수 아님')
    lbl2_3['text'] = int(en2_1.get())//int(en2_2.get())
    lbl2_5['text'] = int(en2_2.get())
    lbl2_4['text'] = int(en2_1.get())%int(en2_2.get())
#################################

en1 = Entry(root, width = 10)
click.set(opt[0])
drop = OptionMenu(root, click, *opt)
lbl1 = Label(root, text = '   ' + '?'*7)
btn1 = Button(root, text = '====', command = get1)
#
lbl2 = Label(root, text = '-' * 30)
en4 = Entry(root, width = 7)
en6 = Label(root, text='---------')
en5 = Entry(root, width = 7)
en7 = Entry(root, width = 7)
btn2 = Button(root, text = '====', command = get2)
lbl3 = Label(root, text = '?')
lbl4 = Label(root, text = '?')
##
lbl2_1 = Label(root, text = '-' * 30)
lbl2_2 = Label(root, text = '-' * 9)
lbl2_3 = Label(root, text = '?')
lbl2_4 = Label(root, text = '?')
lbl2_5 = Label(root, text = '?')
lbl2_6 = Label(root, text = '-' * 9)
en2_1 = Entry(root, width = 7)
en2_2 = Entry(root, width = 7)
btn2_1 = Button(root, text = '====', command = get3)
###############################
en1.grid(row=0, column=0)
drop.grid(row=0, column=1)
Label(root, text='    ').grid(row=0, column=2)
btn1.grid(row=0, column=3)
lbl1.grid(row=0, column=4)
#
lbl2.grid(row=2, column=0, columnspan = 5)
en4.grid(row=3, column=1)
en5.grid(row=5, column=1)
en6.grid(row=4, column=1)
en7.grid(row=4, column=0)
btn2.grid(row = 4, column = 3)
lbl3.grid(row = 3, column = 4)
lbl4.grid(row = 5, column =4)
Label(root, text='---------').grid(row = 4, column = 4)
##
lbl2_1.grid(row = 6, column = 0, columnspan = 5)
lbl2_2.grid(row = 8, column = 0)
lbl2_3.grid(row = 8, column = 2)
lbl2_4.grid(row = 7, column = 3)
lbl2_5.grid(row = 9, column = 3)
lbl2_6.grid(row = 8, column = 3)
en2_1.grid(row = 7, column = 0)
en2_2.grid(row = 9, column = 0)
btn2_1.grid(row = 8, column = 1)

```
