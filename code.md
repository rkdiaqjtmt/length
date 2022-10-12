```python
from tkinter import *#사용한 모듈
import tkinter.messagebox as msgbox
from math import lcm#최소공배수 함수
opt = ['mm', 'cm', 'm', 'in', 'ft', 'yd', 'km', 'mile(s)']
a = 'mm'

root = Tk()
click = StringVar()
root.geometry("330x420")
root.title('제목')
def dirqns(a, b):#약분
    x = lcm(a, b)
    if b == 0:#나눌 수 없다면
        return [1, 0]
    return [int(x/b), int(x/a)]
def get1():#길이단위
    if en1.get() == '':#입력이 없으면
        return msgbox.showinfo("메세지창", "값 없음")
    try:
        float(en1.get())
    except:#유리수가 아니면
        return msgbox.showinfo("메세지창", "유리수 아님")
    a = click.get()
    if a == 'mm':
        lbl1['text'] = '    ' + str(float(en1.get())*0.001) + '(m)'#밀리미터
    elif a == 'cm':
        lbl1['text'] = '    ' + str(float(en1.get())*0.01) + '(m)'#센티미터
    elif a == 'm':
        lbl1['text'] = '    ' + str(float(en1.get())) + '(m)'#미터
    elif a == 'in':
        lbl1['text'] = '    ' + str(round(float(en1.get())/39.3701, 5)) + '(m)'#인치
    elif a == 'ft':
        lbl1['text'] = '    ' + str(round(float(en1.get())/3.28084, 5)) + '(m)'#피트
    elif a == 'yd':
        lbl1['text'] = '    ' + str(round(float(en1.get())/1.09361, 5)) + '(m)'#야드
    elif a == 'km':
        lbl1['text'] = '    ' + str(round(float(en1.get())*1000, 5)) + '(m)'#킬로미터
    elif a == 'mile(s)':
        lbl1['text'] = '    ' + str(round(float(en1.get())/0.000621371, 5)) + '(m)'#마일
    
def get2():#대분수 => 가분수
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
    if int(en5.get()) == 0:
        return msgbox.showinfo("오류", "0으로 나눌 수 없음")
    b = int(en5.get())#분모는 그대로
    a = int(int(en5.get()) * int(en7.get()) + int(en4.get()))#분자는 자연수×분모 + 분자
    lbl4['text'] = dirqns(int(a), int(b))[1]#약분
    lbl3['text'] = dirqns(int(a), int(b))[0]#약분
def get3():#가분수 => 대분수
    if en2_1.get() == '':
        return msgbox.showinfo('오류', '분모 값 없음')
    if en2_2.get() == '':
        return msgbox.showinfo('오류', '분자 값 없음')
    try:
        int(en2_1.get())
        int(en2_2.get())
    except:
        return msgbox.showinfo('오류', '자연수 아님')
    if int(en2_2.get()) == 0:#분모가 0이면
        return msgbox.showinfo("오류", "0으로 나눌 수 없음")
    lbl2_3['text'] = int(en2_1.get())//int(en2_2.get())#자연수는 분자÷분모의 나머지
    a = int(en2_2.get())#분모는 그대로
    b = int(en2_1.get())%int(en2_2.get())#분자는 분자÷분모의 몫
    lbl2_4['text'] = dirqns(a, b)[1]#약분
    lbl2_5['text'] = dirqns(a, b)[0]#약분
def get4():#통분
    if en3_1.get() == '':
        return msgbox.showinfo('오류', '분모 값 없음')
    if en3_2.get() == '':
        return msgbox.showinfor('오류', '분자 값 없음')
    try:
        int(en3_1.get())
        int(en3_2.get())
        int(en3_3.get())
        int(en3_4.get())
    except:
        return msgbox.showinfo("오류", '자연수 아님')
    if int(en3_2.get()) == 0 or int(en3_4.get()) == 0:
        return msgbox.showinfo("오류", "0으로 나눌 수 없음")
    x = lcm(int(en3_2.get()), int(en3_4.get()))#최소공배수(분모가 되는 값)
    lbl3_4['text'] = x#분모
    lbl3_7['text'] = x#분모
    lbl3_3['text'] = int(x/int(en3_2.get()) * int(en3_1.get()))#분자는 최소공배수÷분모×분자
    lbl3_6['text'] = int(x/int(en3_4.get()) * int(en3_3.get()))#분자는 최소공배수÷분모×분자
def get5():
    if en4_1.get() == '':
        return msgbox.showinfo('오류', '분모 값없음')
    if en4_2.get() == '':
        return msgbox.showinfo('오류', '분자 값 없음')
    try:
        int(en4_2.get())
        int(en4_1.get())
    except:
        return msgbox.showinfo("오류", '자연수 아님')
    if int(en4_2.get()) == 0:
        return msgbox.showinfo("오류", "0으로 나눌 수 없음")
    lbl4_3['text'] = float(int(en4_1.get())/int(en4_2.get()))#분자÷분모
    
###########Label, Entry... 만들기
#길이단위
en1 = Entry(root, width = 7)
click.set(opt[0])
drop = OptionMenu(root, click, *opt)
lbl1 = Label(root, text = '   ' + '?'*7)
btn1 = Button(root, text = '====', command = get1)
##가분수 -> 대분수
lbl2 = Label(root, text =' 가분수➡대분수 ')
en4 = Entry(root, width = 7)
en6 = Label(root, text='---------')
en5 = Entry(root, width = 7)
en7 = Entry(root, width = 7)
btn2 = Button(root, text = '====', command = get2)
lbl3 = Label(root, text = '?')
lbl4 = Label(root, text = '?')
###대분수 -> 가분수
lbl2_1 = Label(root, text = ' 대분수➡가분수 ')
lbl2_2 = Label(root, text = '-' * 9)
lbl2_3 = Label(root, text = '?')
lbl2_4 = Label(root, text = '?')
lbl2_5 = Label(root, text = '?')
lbl2_6 = Label(root, text = '-' * 9)
en2_1 = Entry(root, width = 7)
en2_2 = Entry(root, width = 7)
btn2_1 = Button(root, text = '====', command = get3)
####통분
en3_1 = Entry(root, width = 7)
en3_2 = Entry(root, width = 7)
en3_3 = Entry(root, width = 7)
en3_4 = Entry(root, width = 7)
lbl3_1 = Label(root, text = '-' * 9)
lbl3_2 = Label(root, text = '-' * 9)
lbl3_3 = Label(root, text = '?')
lbl3_4 = Label(root, text = '?')
lbl3_5 = Label(root, text = '통분')
lbl3_6 = Label(root, text = '?')
lbl3_7 = Label(root, text = '?')
lbl3_8 = Label(root, text = '-' * 9)
lbl3_9 = Label(root, text = '-' * 9)
btn3 = Button(root, text = '====', command = get4)
#####분수 -> 소수
lbl4_1 = Label(root, text = ' 분수➡소수 ')
lbl4_2 = Label(root, text = '-' * 9)
lbl4_3 = Label(root, text = '?                           ')
btn4 = Button(root, text = '====', command = get5)
en4_1 = Entry(root, width = 7)
en4_2 = Entry(root, width = 7)

##########Label, Entry... 표시
#길이단위
Label(root, text= ' 단위 변환 ').grid(row = 0, column = 1, columnspan = 5)
en1.grid(row=1, column=1)
drop.grid(row=1, column=2)
btn1.grid(row=1, column=3)
lbl1.grid(row=1, column=4, columnspan = 2)
Label(root, text='  ').grid(row = 1, column = 0)
##가분수 -> 대분수
lbl2.grid(row=3, column=1, columnspan = 5)
en4.grid(row=4, column=2)
en5.grid(row=6, column=2)
en6.grid(row=5, column=2)
en7.grid(row=5, column=1)
btn2.grid(row = 5, column = 3)
lbl3.grid(row = 4, column = 4)
lbl4.grid(row = 6, column =4)
Label(root, text='---------').grid(row = 5, column = 4)
##대분수 -> 가분수
lbl2_1.grid(row = 7, column = 1, columnspan = 5)
lbl2_2.grid(row = 9, column = 1)
lbl2_3.grid(row = 9, column = 3)
lbl2_4.grid(row = 8, column = 4)
lbl2_5.grid(row = 10, column = 4)
lbl2_6.grid(row = 9, column = 4)
en2_1.grid(row = 8, column = 1)
en2_2.grid(row = 10, column = 1)
btn2_1.grid(row = 9, column = 2)
####통분
lbl3_5.grid(row = 11, column = 1, columnspan = 5)
lbl3_1.grid(row = 13, column = 1)
lbl3_2.grid(row = 13, column = 2)
lbl3_3.grid(row = 12, column = 4)
lbl3_4.grid(row = 14, column = 4)
lbl3_6.grid(row = 12, column = 5)
lbl3_7.grid(row = 14, column = 5)
lbl3_8.grid(row = 13, column = 4)
lbl3_9.grid(row = 13, column = 5)
btn3.grid(row = 13, column = 3)
en3_1.grid(row = 12, column = 1)
en3_2.grid(row = 14, column = 1)
en3_3.grid(row = 12, column = 2)
en3_4.grid(row = 14, column = 2)
#####분수 -> 소수
lbl4_1.grid(row = 15, column = 1, columnspan = 5)
lbl4_2.grid(row = 17, column = 1)
lbl4_3.grid(row = 17, column = 3, columnspan = 3)
btn4.grid(row = 17, column = 2)
en4_1.grid(row = 16, column = 1)
en4_2.grid(row = 18, column = 1)
###########
root.mainloop()
```
