#----------------------------------------------------------------------------------------------------------------------------------------------------
#this is sample project in progess
from tkinter import *
from PIL import Image,ImageTk
from tkinter import messagebox,ttk
from tkcalendar import Calendar
from datetime import date
import mysql.connector
mydb=mysql.connector.connect(host='localhost',user='harish',password='1234',database='rtr')
mycursor=mydb.cursor()
def window6():
    window6 = tkinter.Toplevel()
    window6.title("RAILWAY TICKET RESERVATION")
    sw = window6.winfo_screenwidth()
    sh = window6.winfo_screenheight()
    width = sw
    hieght = sh
    x = (sw / 2) - (width / 2)
    y = (sh / 2) - (hieght / 2)
    window6.geometry("%dx%d+%d+%d" % (width, hieght, x, y))
    load = Image.open("tt1.jpg")
    photo = ImageTk.PhotoImage(load)
    label = Label(window6, image=photo)
    label.image = photo
    label.place(x=0, y=0)
    sample = Label(window6,text="Ticket details", bg='#0a3d62', fg='white', font=('times', 30, 'bold'),
               pady=40, padx=60)
    sample.pack(fill="x")
    temp=0
    for i in rformage:
        if int(i) <= 10:
            temp += 1
    if rclass=="1 CLASS":
        rs= 500 * (int(rnum)-len(rformantifight))
        rs=rs-(temp*250)
    if rclass == "2 CLASS":
        rs = 300 * (int(rnum)-len(rformantifight))
        rs = rs - (temp * 150)
    if rclass == "3 CLASS":
        rs = 100 * (int(rnum)-len(rformantifight))
        rs = rs - (temp * 50)
    sql = "INSERT INTO rtr (rmail,rfrom,rto,rclass,rdate,rtime,rnum,rbookedtic,rform) VALUES (%s,%s, %s,%s, %s,%s, %s,%s, %s)"
    val2 = (rmail,rfrom,rto,rclass,rdate,rtime,rnum,rticprintstr,str(rs))
    mycursor.execute(sql, val2)
    mydb.commit()
    mycursor.execute("SELECT * FROM rtr")
    myresult = mycursor.fetchall()
    for i in range(len(myresult)):
        print(" " + str(i + 1), myresult[i])
    label1 = Label(window6, text="FROM:", font=("times", 15, "bold"))
    label2 = Label(window6, text=rfrom.upper(), font=("times", 15, "bold"))
    label3 = Label(window6, text="TO:", font=("times", 15, "bold"))
    label4 = Label(window6, text=rto.upper(), font=("times", 15, "bold"))
    label5 = Label(window6, text="DATE:", font=("times", 15, "bold"))
    label6 = Label(window6, text=rdate, font=("times", 15, "bold"))
    label7 = Label(window6, text="NOON:", font=("times", 15, "bold"))
    label8 = Label(window6, text=rnoon.upper(), font=("times", 15, "bold"))
    label9 = Label(window6, text="CLASS:", font=("times", 15, "bold"))
    label10 = Label(window6, text=rclass, font=("times", 15, "bold"))
    label11 = Label(window6, text="TIME:", font=("times", 15, "bold"))
    label12 = Label(window6, text=rtime, font=("times", 15, "bold"))
    label13 = Label(window6, text="NUMBER OF PASSENGER:", font=("times", 15, "bold"))
    label14 = Label(window6, text=rnum, font=("times", 15, "bold"))
    label15 = Label(window6, text="BOOKED TICKETS:", font=("times", 15, "bold"))
    label16 = Label(window6, text=rticprintstr, font=("times", 15, "bold"))
    label17 = Label(window6, text="PASSENGERS DETAILS:", font=("times", 15, "bold"))
    label18 = Label(window6, text="TOTAL AMOUNT:", font=("times", 15, "bold"))
    label19 = Label(window6, text=str(rs), font=("times", 15, "bold"))
    l1 = Listbox(window6, width=30, height=5)
    l1.place(x=1200,y=500)
    label1.place(x=150,y=200)
    label2.place(x=300, y=200)
    label3.place(x=150, y=300)
    label4.place(x=300, y=300)
    label5.place(x=150, y=400)
    label6.place(x=300, y=400)
    label7.place(x=150, y=500)
    label8.place(x=300, y=500)
    label9.place(x=150, y=600)
    label10.place(x=300, y=600)

    label11.place(x=850, y=200)
    label12.place(x=1200, y=200)
    label13.place(x=850, y=300)
    label14.place(x=1200, y=300)
    label15.place(x=850, y=400)
    label16.place(x=1200, y=400)
    label17.place(x=850, y=500)
    label18.place(x=850, y=600)
    label19.place(x=1200, y=600)
    for i in range(int(rnum)):
        ss="Person "+str(i+1)+"--> "+"Name:"+rformname[i]+","+"Age:"+rformage[i]+","+"Gender:"+rformgender[i]+"."
        l1.insert(END,ss)
    def printt():
        messagebox.showwarning("WARNING","Printing Device is not found",parent=window6)
    btnext = Button(window6, text='PRINT', bg='#0a3d62', fg='white', font=('times', 10, 'bold'), pady=10, padx=10,command=printt)
    btnext.place(x=1400, y=200)
    window6.mainloop()
def window5():
    window5 = tkinter.Toplevel()
    window5.title("RAILWAY TICKET RESERVATION")
    sw = window5.winfo_screenwidth()
    sh = window5.winfo_screenheight()
    width = sw
    hieght = sh
    x = (sw / 2) - (width / 2)
    y = (sh / 2) - (hieght / 2)
    window5.geometry("%dx%d+%d+%d" % (width, hieght, x, y))
    load = Image.open("t6.jpg")
    photo = ImageTk.PhotoImage(load)
    label = Label(window5, image=photo)
    label.image = photo
    label.place(x=0, y=0)
    sample = Label(window5,text="Fill the details", bg='#0a3d62', fg='white', font=('times', 30, 'bold'),
               pady=40, padx=60)
    sample.pack(fill="x")
    label1 = Label(window5, text="NAME", font=("times", 15, "bold"))
    label2 = Label(window5, text="AGE", font=("times", 15, "bold"))
    label3 = Label(window5, text="GENDER", font=("times", 15, "bold"))
    label4 = Label(window5, text="SPECIAL", font=("times", 15, "bold"))
    label1.place(x=50, y=150)
    label2.place(x=50, y=300)
    label3.place(x=50, y=450)
    label4.place(x=1000, y=150)
    tname = Entry(window5, width=30, bg='#55efc4', fg='white', font=("times", 20), selectbackground="black",
               selectforeground="yellow")
    tname.place(x=180, y=145)
    tage = Entry(window5, width=8, bg='#55efc4', fg='white', font=("times", 20), selectbackground="black",
                  selectforeground="yellow")
    tage.place(x=180, y=295)

    def submit():
        indiname = tname.get()
        indiage = tage.get()
        rformname.append(indiname)
        rformage.append(indiage)
        tname.delete(0,END)
        tage.delete(0,END)
        if rb.get() == 1:
            # val=rb.get()
            indigen = rb1.cget('text')
            rformgender.append(indigen)
        if rb.get() == 2:
            # val=rb.get()
            indigen = rb2.cget('text')
            rformgender.append(indigen)
        if rb.get() == 3:
            # val=rb.get()
            indigen = rb3.cget('text')
            rformgender.append(indigen)
        if c1.get() == 1:
            # val=c1.get()
            indifig = cb1.cget('text')
            rformantifight.append(indifig)
            cb1.deselect()
        if len(rformname)==int(rnum):
            bd1.pack_forget()
    c1 = IntVar()
    cb1 = Checkbutton(window5, text='FreedomFighter', variable=c1, onvalue=1, offvalue=0, font=('times,20'))
    cb1.place(x=1000, y=250)
    rb = IntVar()
    rb1 = Radiobutton(window5, text='Male', variable=rb, value=1)
    rb2 = Radiobutton(window5, text='FeMale', variable=rb, value=2)
    rb3 = Radiobutton(window5, text='other', variable=rb, value=3)
    rb1.place(x=180, y=450)
    rb2.place(x=180, y=550)
    rb3.place(x=180, y=650)
    global rformname,rformage,rformantifight,rformgender
    rformname=[]
    rformage=[]
    rformgender=[]
    rformantifight=[]
    bd1 = Button(window5, text='submit', bg='#0a3d62', fg='white', font=('times', 10, 'bold'), pady=40, padx=60,
                command=submit)
    bd1.pack(side="bottom")
    btnext = Button(window5, text='Next', bg='#0a3d62', fg='white', font=('times', 20, 'bold'), pady=40, padx=60,
                    command=lambda: window6())
    btnext.place(x=1300, y=650)
    window5.mainloop()
def window4():
    window4=tkinter.Toplevel()
    sw = window4.winfo_screenwidth()
    sh = window4.winfo_screenheight()
    width = sw
    hieght = sh
    x = (sw / 2) - (width / 2)
    y = (sh / 2) - (hieght / 2)
    window4.geometry("%dx%d+%d+%d" % (width, hieght, x, y))
    load = Image.open("t1.jpg")
    photo = ImageTk.PhotoImage(load)
    label = Label(window4, image=photo)
    label.image = photo
    label.place(x=0, y=0)

    window4.title("RAILWAY TICKET RESERVATION")
    l1 = Label(window4, text="Select the tickets", bg='#0a3d62', fg='white', font=('times', 30, 'bold'), pady=30, padx=50)
    l1.pack(fill="x")
    def submit():
        global rticprintstr
        rticprintstr = ""
        for item in reversed(l1.curselection()):
            rticketdel.append(item)
            l1.delete(item)
        print('rticketdel',rticketdel)
        for i in rticketdel:
            if rfrom == 'Chennai' and rto == 'Bangalore':
                sql = "INSERT INTO cb (ticket) VALUES (%s)"
            if rfrom == 'Chennai' and rto == 'Mumbai':
                sql = "INSERT INTO cm (ticket) VALUES (%s)"
            if rfrom == 'Chennai' and rto == 'Delhi':
                sql = "INSERT INTO cd (ticket) VALUES (%s)"
            if rfrom == 'Bangalore' and rto == 'Delhi':
                sql = "INSERT INTO bd (ticket) VALUES (%s)"
            if rfrom == 'Bangalore' and rto == 'Chennai':
                sql = "INSERT INTO bc (ticket) VALUES (%s)"
            if rfrom == 'Bangalore' and rto == 'Mumbai':
                sql = "INSERT INTO bm (ticket) VALUES (%s)"
            if rfrom == 'Mumbai' and rto == 'Bangalore':
                sql = "INSERT INTO mb (ticket) VALUES (%s)"
            if rfrom == 'Mumbai' and rto == 'Chennai':
                sql = "INSERT INTO mc (ticket) VALUES (%s)"
            if rfrom == 'Mumbai' and rto == 'Delhi':
                sql = "INSERT INTO md (ticket) VALUES (%s)"
            if rfrom == 'Delhi' and rto == 'Chennai':
                sql = "INSERT INTO dc (ticket) VALUES (%s)"
            if rfrom == 'Delhi' and rto == 'Bangalore':
                sql = "INSERT INTO db (ticket) VALUES (%s)"
            if rfrom == 'Delhi' and rto == 'Mumbai':
                sql = "INSERT INTO dm (ticket) VALUES (%s)"
            gg=bb1[i]
            rticprint.append(gg)
            print(gg,"OOOO",rticprint)
            value = (str(gg),)
            mycursor.execute(sql, value)
            mydb.commit()
        global rnum
        rnum = t1.get()
        l2.delete(0,END)
        for i in rticketdel:
           ii=a1[i]
           l2.insert(END, ii)
        for i in range (len(rticprint)):
            if i==len(rticprint)-1:
                rticprintstr+=rticprint[i]+"."
            else:
                rticprintstr+=rticprint[i]+","
        print(rticprintstr)
    global rticketdel,rticprint
    rticprint=[]
    rticketdel = []
    label1 = Label(window4, text="Number of Seats:", font=("times", 15, "bold"))
    label2 = Label(window4, text="Select the Tickets:", font=("times", 15, "bold"))
    label3 = Label(window4, text="Your Booked Tickets", font=("times", 15, "bold"))
    label1.place(x=100, y=250)
    label2.place(x=680, y=150)
    label3.place(x=1180, y=150)
    t1 = Entry(window4, width=8, bg='#55efc4', fg='black', font=("times", 20), selectbackground="black",
               selectforeground="yellow")
    t1.place(x=260, y=245)
    l1 = Listbox(window4, width=30, height=20, selectmode=MULTIPLE)
    l1.place(x=680, y=250)
    if rfrom=='Chennai' and rto=='Bangalore':
        mycursor.execute("SELECT * FROM cb")
    if rfrom == 'Chennai' and rto == 'Mumbai':
        mycursor.execute("SELECT * FROM cm")
    if rfrom=='Chennai' and rto=='Delhi':
        mycursor.execute("SELECT * FROM cd")
    if rfrom=='Bangalore' and rto=='Delhi':
        mycursor.execute("SELECT * FROM bd")
    if rfrom=='Bangalore' and rto=='Chennai':
        mycursor.execute("SELECT * FROM bc")
    if rfrom=='Bangalore' and rto=='Mumbai':
        mycursor.execute("SELECT * FROM bm")
    if rfrom=='Mumbai' and rto=='Bangalore':
        mycursor.execute("SELECT * FROM mb")
    if rfrom=='Mumbai' and rto=='Chennai':
        mycursor.execute("SELECT * FROM mc")
    if rfrom=='Mumbai' and rto=='Delhi':
        mycursor.execute("SELECT * FROM md")
    if rfrom=='Delhi' and rto=='Chennai':
        mycursor.execute("SELECT * FROM dc")
    if rfrom=='Delhi' and rto=='Bangalore':
        mycursor.execute("SELECT * FROM db")
    if rfrom == 'Delhi' and rto == 'Mumbai':
        mycursor.execute("SELECT * FROM dm")
    myresult = mycursor.fetchall()
    print(myresult,"myr")
    aa = []
    for i in myresult:
        aa.append(i[0])
    print(aa,"aa")
    bb1=[]
    a1=['T1', 'T2', 'T3', 'T4', 'T5', 'T6', 'T7', 'T8', 'T9', 'T10', 'T11', 'T12', 'T13', 'T14', 'T15', 'T16', 'T17', 'T18', 'T19', 'T20', 'T21', 'T22', 'T23', 'T24', 'T25', 'T26', 'T27', 'T28', 'T29', 'T30']
    for i in a1:
        if i in aa:
            continue
        else:
            bb1.append(i)
            l1.insert(END,i)
    l2 = Listbox(window4, width=30, height=20, selectmode=MULTIPLE)
    l2.place(x=1180, y=250)
    b1 = Button(window4, text='submit', bg='#0a3d62', fg='white', font=('times', 10, 'bold'), pady=40, padx=60,
                command=submit)
    b1.place(x=700, y=650)
    btnext = Button(window4, text='Next', bg='#0a3d62', fg='white', font=('times', 20, 'bold'), pady=40, padx=60,
                    command=lambda: window5())
    btnext.place(x=1300, y=650)
    window4.mainloop()
def window3():
    window3 = tkinter.Toplevel(window1)
    window3.title("RAILWAY TICKET RESERVATION")
    sw = window3.winfo_screenwidth()
    sh = window3.winfo_screenheight()
    width = sw
    hieght = sh
    x = (sw / 2) - (width / 2)
    y = (sh / 2) - (hieght / 2)
    window3.geometry("%dx%d+%d+%d" % (width, hieght, x, y))
    load = Image.open("t6.jpg")
    photo = ImageTk.PhotoImage(load)
    label = Label(window3, image=photo)
    label.image = photo
    label.place(x=0, y=0)

    sample = Label(window3, text="Select the date,time and class", bg='#0a3d62', fg='white', font=('times', 30, 'bold'),
               pady=40, padx=60)
    sample.pack(fill='x')
    label1=Label(window3,text="Select the date:",font=("times",15,"bold"))
    label2 = Label(window3, text="Select the time:", font=("times", 15, "bold"))
    label3 = Label(window3, text="Select the class:", font=("times", 15, "bold"))
    label1.place(x=200,y=150)
    label2.place(x=680,y=150)
    label3.place(x=1180,y=150)
    toda = date.today()
    today = str(toda)
    syear=today[0:4]
    smonth=today[5:7]
    sday=today[8:]
    cal = Calendar(window3, selectmode='day',
                   year=int(syear), month=int(smonth),
                   day=int(sday))
    cal.place(x=150,y=250)
    def submit():
        global rtime,rclass,rnoon,rdate
        if rb.get() == 1:
            rtime= rb1.cget('text')
        if rb.get() == 2:
            rtime= rb2.cget('text')
        if rtime=="10:00AM":
            rnoon="forenoon"
        else:
            rnoon="afternoon"
        rdate = cal.get_date()
        if rc.get() == 1:
            # val=rb.get()
            rclass = rc1.cget('text')
        if rc.get() == 2:
            # val=rb.get()
            rclass = rc2.cget('text')
        if rc.get() == 3:
            # val=rb.get()
            rclass = rc3.cget('text')
    rb = IntVar()
    rb1 = Radiobutton(window3, text='10:00AM', variable=rb, value=1)
    rb2 = Radiobutton(window3, text='05:00PM', variable=rb, value=2)
    rb1.place(x=700,y=250)
    rb2.place(x=700,y=350)
    rc = IntVar()
    rc1 = Radiobutton(window3, text='1 CLASS', variable=rc, value=1)
    rc2 = Radiobutton(window3, text='2 CLASS', variable=rc, value=2)
    rc3 = Radiobutton(window3, text='3 CLASS', variable=rc, value=3)
    rc1.place(x=1200,y=250)
    rc2.place(x=1200,y=300)
    rc3.place(x=1200,y=350)
    b1 = Button(window3, text='submit', bg='#0a3d62', fg='white', font=('times', 10, 'bold'), pady=40, padx=60,
                command=submit)
    b1.place(x=700,y=650)
    btnext = Button(window3, text='Next', bg='#0a3d62', fg='white', font=('times', 20, 'bold'), pady=40, padx=60,
                    command=lambda: window4())
    btnext.place(x=1300, y=650)
    window3.mainloop()
def window2():
    window2=tkinter.Toplevel()
    sw = window2.winfo_screenwidth()
    sh = window2.winfo_screenheight()
    width = sw
    hieght = sh
    x = (sw / 2) - (width / 2)
    y = (sh / 2) - (hieght / 2)
    window2.geometry("%dx%d+%d+%d" % (width, hieght, x, y))
    load = Image.open("t2.jpg")
    photo = ImageTk.PhotoImage(load)
    label = Label(window2, image=photo)
    label.image = photo
    label.place(x=0, y=0)

    window2.title("RAILWAY TICKET RESERVATION")
    l1 = Label(window2, text="Select a city", bg='#0a3d62', fg='white', font=('times', 30, 'bold'), pady=30, padx=50)
    l1.pack(fill='x')
    def comto(event):
        global rfrom
        rfrom = com1.get()

        if rfrom == "Delhi":
            def comfo(event):
                global rto
                rto = com2.get()
            com2 = ttk.Combobox(window2, width=30, state="readonly",font=("times",15,"bold"))
            com2['values'] = ("Mumbai", "Bangalore", "Chennai")
            com2.current(0)
            com2.bind("<<ComboboxSelected>>", comfo)
            com2.place(x=800,y=350)
        if rfrom == "Mumbai":
            def comfo(event):
                global rto
                rto = com2.get()
            com2 = ttk.Combobox(window2, width=30, state="readonly",font=("times",15,"bold"))
            com2['values'] = ("Delhi", "Bangalore", "Chennai")
            com2.current(0)
            com2.bind("<<ComboboxSelected>>", comfo)
            com2.place(x=800,y=350)
        if rfrom == "Bangalore":
            def comfo(event):
                global rto
                rto = com2.get()
            com2 = ttk.Combobox(window2, width=30, state="readonly",font=("times",15,"bold"))
            com2['values'] = ("Delhi","Mumbai","Chennai")
            com2.current(0)
            com2.bind("<<ComboboxSelected>>", comfo)
            com2.place(x=800,y=350)
        if rfrom == "Chennai":
            def comfo(event):
                global rto
                rto = com2.get()
            com2 = ttk.Combobox(window2, width=30, state="readonly",font=("times",15,"bold"))
            com2['values'] = ("Delhi","Mumbai","Bangalore")
            com2.current(0)
            com2.bind("<<ComboboxSelected>>", comfo)
            com2.place(x=800,y=350)
    com1 = ttk.Combobox(window2, width=30, state="readonly",font=("times",15,"bold"))
    com1['values'] = ("Delhi","Mumbai","Bangalore","Chennai")
    com1.current(0)
    com1.bind("<<ComboboxSelected>>",comto)
    com1.place(x=800,y=250)
    com2 = ttk.Combobox(window2, width=30, state="readonly",font=("times",15,"bold"))
    com2['values'] = ("Delhi", "Mumbai", "Bangalore")
    com2.current(0)
    com2.place(x=800, y=350)
    btnext = Button(window2, text='Next2', bg='#0a3d62', fg='white', font=('times', 20, 'bold'), pady=40, padx=60,
                command=lambda: window3())
    btnext.place(x=1300,y=650)
    window2.mainloop()
window1=Tk()
window1.title("RAILWAY TICKET RESERVATION")
sw=window1.winfo_screenwidth()
sh=window1.winfo_screenheight()
width=sw
hieght=sh
x=(sw/2)-(width/2)
y=(sh/2)-(hieght/2)
window1.geometry("%dx%d+%d+%d" %(width,hieght,x,y))
#glopal variable rfrom,rto,rdate,rtime,rnum,rticketdel,rclass,rformname,rformage,rformantifight,rformgender,rnoon,rticprint,rticprintstr,rmail
load=Image.open("t4.jpg")
photo=ImageTk.PhotoImage(load)
label=Label(window1, image=photo)
label.image=photo
label.place(x=0,y=0)
rl1=Label(window1,text="RAILWAY TICKET RESERVATION",bg='#0a3d62',fg='white',font=('times',30,'bold'),pady=40,padx=60)
rl1.place(x=400,y=10)
frame1=Frame(window1,highlightbackground="black",highlightthickness=2,width=100,padx=20,pady=20)
frame1.place(x=200,y=200)#ffffffffffffffffffffffffffffffffffffff
lt=Label(frame1,text="REGISTRATION",font=("times",25,"bold"),fg="green",pady=20,padx=50)
lt.grid(columnspan=2)
ln=Label(frame1,text="NAME",font=("times",15,"bold"),pady=20,padx=50)
ln.grid(row=1,column=0)
tn=Entry(frame1,font=("times",15,"bold"))
tn.grid(row=1,column=1)
lm=Label(frame1,text="MAIL",font=("times",15,"bold"),pady=20,padx=50)
lm.grid(row=2,column=0)
tm=Entry(frame1,font=("times",15,"bold"))
tm.grid(row=2,column=1)
lp=Label(frame1,text="PASSWORD",font=("times",15,"bold"),pady=20,padx=50)
lp.grid(row=3,column=0)
tp=Entry(frame1,font=("times",15,"bold"),show="*")
tp.grid(row=3,column=1)
def bsubmit():
    rregm=tm.get()
    rregp=tp.get()
    sql = "INSERT INTO reg (mail,pass) VALUES (%s, %s)"
    val1 = (rregm,rregp)
    mycursor.execute(sql, val1)
    mydb.commit()
    messagebox.showinfo("MAIL","Sucesess fully registred")
    tn.delete(0, END)
    tm.delete(0, END)
    tp.delete(0, END)
def sclear():
    tn.delete(0, END)
    tm.delete(0, END)
    tp.delete(0, END)
bs=Button(frame1,text="SUBMIT",bg="green",width=5,pady=5,padx=10,font=("times",10,"bold"),command=bsubmit)
bs.grid(row=4,column=1)
bc=Button(frame1,text="ClEAR",bg="red",width=5,pady=5,padx=10,font=("times",10,"bold"),command=sclear)
bc.grid(row=4,column=1,sticky=W)
frame2=Frame(window1,highlightbackground="black",highlightthickness=2,width=100,padx=20,pady=20)
frame2.place(x=800,y=250)
flt=Label(frame2,text="LOGIN",font=("times",25,"bold"),fg="green",pady=20,padx=50)
flt.grid(columnspan=2)
flm=Label(frame2,text="MAIL",font=("times",15,"bold"),pady=20,padx=50)
flm.grid(row=1,column=0)
ftm=Entry(frame2,font=("times",15,"bold"))
ftm.grid(row=1,column=1)
flp=Label(frame2,text="PASSWORD",font=("times",15,"bold"),pady=20,padx=50)
flp.grid(row=2,column=0)
ftp=Entry(frame2,font=("times",15,"bold"),show="*")
ftp.grid(row=2,column=1)
def submit():
    rlogm=ftm.get()
    rlogp=ftp.get()
    mycursor.execute("SELECT * FROM reg")
    myresult = mycursor.fetchall()
    print(myresult)
    q=0
    for i in range(len(myresult)):
        if myresult[i][0] == rlogm and myresult[i][1] == rlogp:
            rb2 = Button(window1, text='Next1', bg='#0a3d62', fg='white', font=('times', 20, 'bold'), pady=40, padx=60,
                         command=lambda: window2())
            rb2.place(x=1300, y=650)
            q=1
            messagebox.showinfo("MAIL","Welcome to RTR")
            global rmail
            rmail=rlogm
    if q==0:
        messagebox.showerror("MAIL","email address or password is incorrect")
def clear():
    ftm.delete(0, END)
    ftp.delete(0, END)
fbs=Button(frame2,text="SUBMIT",bg="green",width=5,pady=5,padx=10,font=("times",10,"bold"),command=submit)
fbs.grid(row=3,column=1)
fbc=Button(frame2,text="ClEAR",bg="red",width=5,pady=5,padx=10,font=("times",10,"bold"),command=clear)
fbc.grid(row=3,column=1,sticky=W)

window1.mainloop()
