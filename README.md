import tkinter
import tkinter.ttk
from PIL import ImageTk, Image
import string
import os, sys
import time


class Plocha():
    canvas = None
    def __init__(self):
        self.pole_pismen = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H']
        self.pole_cisel = ['8', '7', '6', '5', '4', '3', '2', '1']
        self.postavicky = {'pesiak_biely_1': 'A2', 'pesiak_biely_2': 'B2', 'pesiak_biely_3': 'C2',
              'pesiak_biely_4': 'D2', 'pesiak_biely_5': 'E2', 'pesiak_biely_6': 'F2',
              'pesiak_biely_7': 'G2', 'pesiak_biely_8': 'H2', 'veza_biely_1': 'A1',
              'veza_biely_2': 'H1', 'kon_biely_1': 'B1', 'kon_biely_2': 'G1',
              'strelec_biely_1': 'C1','strelec_biely_2': 'F1', 'kralovna_biely_1': 'D1',
              'kral_biely_1': 'E1', 'pesiak_cierny_1': 'A7', 'pesiak_cierny_2': 'B7',
              'pesiak_cierny_3': 'C7','pesiak_cierny_4': 'D7', 'pesiak_cierny_5': 'E7',
              'pesiak_cierny_6': 'F7','pesiak_cierny_7': 'G7', 'pesiak_cierny_8': 'H7',
              'veza_cierny_1': 'A8','veza_cierny_2': 'H8', 'kon_cierny_1': 'B8',
              'kon_cierny_2': 'G8','strelec_cierny_1': 'C8','strelec_cierny_2': 'F8',
              'kralovna_cierny_1': 'D8', 'kral_cierny_1': 'E8'}
        self.miesta={}
        self.id = self.canvas.create_rectangle(100, 50, 700, 650)
        farby = ['black', 'white']
        for i in range(8):
            farby[0], farby[1] = farby[1], farby[0]
            for y in range(8):
                self.canvas.create_rectangle(i*75+100, y*75+50, i*75+75+100,y*75+75+50,
                                             fill=farby[0])
                farby[0], farby[1] = farby[1], farby[0]
                self.miesta.update({f'{self.pole_pismen[y]}{self.pole_cisel[i]}':
                                    (i*75+100, y*75+50)})
        Plocha.postavicky(self)

    def postavicky(self):
        ###pesiak biely
        for i in range(1, 9):
            path = os.path.join(os.path.dirname(__file__))
            pesiakb = Image.open(path + '/pesiak_biely.png')
            test = ImageTk.PhotoImage(pesiakb)
            label=tkinter.Label(image=test)
            label.image = test
            slovo = 'pesiak_biely_'+str(i)
            x1 = self.postavicky[slovo]
            postavenie = self.miesta[x1]
            label.place(x = postavenie[1]+65, y = postavenie[0]-40)
        ###pesiak ciernyy
        for i in range(1, 9):
            path = os.path.join(os.path.dirname(__file__))
            pesiakc = Image.open(path + '/pesiak_cierny.png')
            test = ImageTk.PhotoImage(pesiakc)
            label=tkinter.Label(image=test)
            label.image = test
            slovo = 'pesiak_cierny_'+str(i)
            x1 = self.postavicky[slovo]
            postavenie = self.miesta[x1]
            label.place(x = postavenie[1]+65, y = postavenie[0]-40)

        ###veza biely
        for i in range(1, 3):
            path = os.path.join(os.path.dirname(__file__))
            vezab = Image.open(path + '/veza_biely.png')
            test = ImageTk.PhotoImage(vezab)
            label=tkinter.Label(image=test)
            label.image = test
            slovo = 'veza_biely_'+str(i)
            x1 = self.postavicky[slovo]
            postavenie = self.miesta[x1]
            label.place(x = postavenie[1]+65, y = postavenie[0]-40)
        ###veza cierny
        for i in range(1, 3):
            path = os.path.join(os.path.dirname(__file__))
            vezac = Image.open(path + '/veza_cierny.png')
            test = ImageTk.PhotoImage(vezac)
            label=tkinter.Label(image=test)
            label.image = test
            slovo = 'veza_cierny_'+str(i)
            x1 = self.postavicky[slovo]
            postavenie = self.miesta[x1]
            label.place(x = postavenie[1]+65, y = postavenie[0]-40)
        ###kon biely
        for i in range(1, 3):
            path = os.path.join(os.path.dirname(__file__))
            konb = Image.open(path + '/kon_biely.png')
            test = ImageTk.PhotoImage(konb)
            label=tkinter.Label(image=test)
            label.image = test
            slovo = 'kon_biely_'+str(i)
            x1 = self.postavicky[slovo]
            postavenie = self.miesta[x1]
            label.place(x = postavenie[1]+65, y = postavenie[0]-40)
        ###kon cierny
        for i in range(1, 3):
            path = os.path.join(os.path.dirname(__file__))
            konc = Image.open(path + '/kon_cierny.png')
            test = ImageTk.PhotoImage(konc)
            label=tkinter.Label(image=test)
            label.image = test
            slovo = 'kon_cierny_'+str(i)
            x1 = self.postavicky[slovo]
            postavenie = self.miesta[x1]
            label.place(x = postavenie[1]+65, y = postavenie[0]-40)
        ###strelec biely
        for i in range(1, 3):
            path = os.path.join(os.path.dirname(__file__))
            strelecb = Image.open(path + '/strelec_biely.png')
            test = ImageTk.PhotoImage(strelecb)
            label=tkinter.Label(image=test)
            label.image = test
            slovo = 'strelec_biely_'+str(i)
            x1 = self.postavicky[slovo]
            postavenie = self.miesta[x1]
            label.place(x = postavenie[1]+60, y = postavenie[0]-40)
        ###strelec cierny
        for i in range(1, 3):
            path = os.path.join(os.path.dirname(__file__))
            strelecc = Image.open(path + '/strelec_cierny.png')
            test = ImageTk.PhotoImage(strelecc)
            label=tkinter.Label(image=test)
            label.image = test
            slovo = 'strelec_cierny_'+str(i)
            x1 = self.postavicky[slovo]
            postavenie = self.miesta[x1]
            label.place(x = postavenie[1]+60, y = postavenie[0]-40)
        ###kralovna biely
        path = os.path.join(os.path.dirname(__file__))
        kralovnab = Image.open(path + '/kralovna_biely.png')
        test = ImageTk.PhotoImage(kralovnab)
        label=tkinter.Label(image=test)
        label.image = test
        slovo = 'kralovna_biely_1'
        x1 = self.postavicky[slovo]
        postavenie = self.miesta[x1]
        label.place(x = postavenie[1]+60, y = postavenie[0]-40)
        ###kralovna cierny
        path = os.path.join(os.path.dirname(__file__))
        kralovnac = Image.open(path + '/kralovna_cierny.png')
        test = ImageTk.PhotoImage(kralovnac)
        label=tkinter.Label(image=test)
        label.image = test
        slovo = 'kralovna_cierny_1'
        x1 = self.postavicky[slovo]
        postavenie = self.miesta[x1]
        label.place(x = postavenie[1]+60, y = postavenie[0]-40)
        ###kral biely
        path = os.path.join(os.path.dirname(__file__))
        kralb = Image.open(path + '/kral_biely.png')
        test = ImageTk.PhotoImage(kralb)
        label=tkinter.Label(image=test)
        label.image = test
        slovo = 'kral_biely_1'
        x1 = self.postavicky[slovo]
        postavenie = self.miesta[x1]
        label.place(x = postavenie[1]+60, y = postavenie[0]-40)
        ###kral cierny
        path = os.path.join(os.path.dirname(__file__))
        kralc = Image.open(path + '/kral_cierny.png')
        test = ImageTk.PhotoImage(kralc)
        label=tkinter.Label(image=test)
        label.image = test
        slovo = 'kral_cierny_1'
        x1 = self.postavicky[slovo]
        postavenie = self.miesta[x1]
        label.place(x = postavenie[1]+60, y = postavenie[0]-40)
        

        

class Sach():
    Plocha.canvas = tkinter.Canvas(width = 900, height=700)
    Plocha.canvas.pack()
    Plocha()
    
Sach()
