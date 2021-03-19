import sys #импорт системы
from PyQt5 import QtWidgets, QtGui, QtCore #импорт нужных виджетов для программы
from PyQt5.QtWidgets import QApplication #импорт нужных виджетов для программы
from hack import Ui_Window #импорт Меню
from Rule import Ui_WindowRule #импорт кнопки Правило
from lvl import Ui_windowLvl #импорт кнопки Уровень
from Easy1 import Ui_Easy1 #импорт кнопки Легкий
from Easy2 import Ui_Easy2 #импорт Задачи2
from Easy3 import Ui_Easy3 #импорт Задачи3
from EasyEnd import Ui_EasyEnd #импорт окна(Конец уровня)
from Medium1 import Ui_Medium1 #импорт Средний
from Medium2 import Ui_Medium2 #импорт Задачи2.Средний
from Medium3 import Ui_Medium3 #импорт Задачи3.Средний
from Hard1 import Ui_Hard1 #импорт кнопки Сложный
from Hard2 import Ui_Hard2 #импорт Задачи2. Сложный
from Hard3 import Ui_Hard3 #импорт Задачи3. Сложный


class windowHack(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self, parent)
        self.hk = Ui_Window()
        self.hk.setupUi(self)
        self.hk.btnExit.clicked.connect(self.close) #Добавление функционала
        self.hk.btnRule.clicked.connect(self.openRule) #Добавление функционала
        self.hk.btnLvl.clicked.connect(self.openLvl) #Добавление функционала
    def openRule(self): #Функия
        self.hide()
        q = windowRule(self)
        q.show()
    def openLvl(self): #Функия
        self.hide()
        l = windowLvl(self)
        l.show()
class windowRule(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self, parent)
        self.re = Ui_WindowRule()
        self.re.setupUi(self)
        self.re.btnBack.clicked.connect(self.Back_1)
    def Back_1(self):
        self.hide()
        w.show()
class windowLvl(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self, parent)
        self.ll = Ui_windowLvl()
        self.ll.setupUi(self)
        self.ll.btnBack.clicked.connect(self.Back_2)
        self.ll.btnEasy.clicked.connect(self.openEasy_1)
        self.ll.btnMedium.clicked.connect(self.openMedium1)
        self.ll.btnHard.clicked.connect(self.openHard1)
    def Back_2(self):
        self.hide()
        w.show()
    def openEasy_1(self):
        self.hide()
        eas=windowEasy1(self)
        eas.show()
    def openMedium1(self):
        self.hide()
        med = windowMedium1(self)
        med.show()
    def openHard1(self):
        self.hide()
        had = windowHard1(self)
        had.show()
class windowEasy1(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self,parent)
        self.ey1 = Ui_Easy1()
        self.ey1.setupUi(self)
        self.ey1.btnBack.clicked.connect(self.Back_3)
        self.ey1.btnRes.clicked.connect(self.otvet_1)
        self.ey1.btnNext.clicked.connect(self.next)
    def Back_3(self):
        self.hide()
        l = windowLvl(self)
        l.show()
    def otvet_1(self):
        if self.ey1.lineEdit.text()==str(9):#Проверка ответа
            self.ey1.labelStat.setText("<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>")
        else:
            self.ey1.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")
    def next(self):
        if self.ey1.labelStat.text()=="<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>":
            self.hide()
            s = Easy2(self)
            s.show()
            #self.ey1.labelStat.setText('')
            #self.ey1.labelText.setText("<html><head/><body><p>2. Ученики 2 класса по заданию учительницы взяли в библиотеке по 2 сказки</p><p>Пушкина. Сколько всего сказок Пушкина выдал библиотекарь </p><p>второклассникам, если известно, что во втором классе учится 20 человек?</p></body></html>")
            #self.ey1.label.setText("Задача 2. Легкий")
        else:
            self.ey1.labelStat.setText("<html><head/><body><p align=\"center\">Сначала решите задачу</p></body></html>")

class Easy2(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self,parent)
        self.ey2 = Ui_Easy2()
        self.ey2.setupUi(self)
        self.ey2.btnBack.clicked.connect(self.Back_4)
        self.ey2.btnRes.clicked.connect(self.otvet_2)
        self.ey2.btnNext.clicked.connect(self.next2)
    def Back_4(self):
            self.hide()
            eas = windowEasy1(self)
            eas.show()

    def otvet_2(self):
        if self.ey2.lineEdit.text() == str(40):#Проверка ответа
            self.ey2.labelStat.setText("<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>")
        else:
            self.ey2.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")

    def next2(self):
        if self.ey2.labelStat.text()=="<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>":
            self.hide()
            s1 = Easy3(self)
            s1.show()
        else:
            self.ey2.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")

class Easy3(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self,parent)
        self.ey3 = Ui_Easy3()
        self.ey3.setupUi(self)
        self.ey3.btnBack.clicked.connect(self.close)
        self.ey3.btnRes.clicked.connect(self.otvet_3)
        self.ey3.btnNext.clicked.connect(self.next3)

    def otvet_3(self):
        if self.ey3.lineEdit.text() == str(132):#Проверка ответа
            self.ey3.labelStat.setText("<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>")
        else:
            self.ey3.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")

    def next3(self):
        if self.ey3.labelStat.text()=="<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>":
            self.hide()
            s3 = EasyEnd(self)
            s3.show()
        else:
            self.ey3.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")

class EasyEnd(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self,parent)
        self.eyEnd = Ui_EasyEnd()
        self.eyEnd.setupUi(self)
        self.eyEnd.btnBack.clicked.connect(self.back)
    def back(self):
        self.hide()
        sEnd = windowHack(self)
        sEnd.show()

class windowMedium1(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self, parent)
        self.md1 = Ui_Medium1()
        self.md1.setupUi(self)
        self.md1.btnBack.clicked.connect(self.Back_5)
        self.md1.btnRes.clicked.connect(self.otvet_4)
        self.md1.btnNext.clicked.connect(self.next_med)
    def Back_5(self):
        self.hide()
        l = windowLvl(self)
        l.show()
    def otvet_4(self):
        if self.md1.lineEdit.text()==str(4890):#Проверка ответа
            self.md1.labelStat.setText("<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>")
        else:
            self.md1.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")
    def next_med(self):
        if self.md1.labelStat.text()=="<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>":
            self.hide()
            s_med = windowMedium2(self)
            s_med.show()
        else:
           self.md1.labelStat.setText("<html><head/><body><p align=\"center\">Сначала решите задачу</p></body></html>")

class windowMedium2(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self,parent)
        self.md2 = Ui_Medium2()
        self.md2.setupUi(self)
        self.md2.btnBack.clicked.connect(self.Back_6)
        self.md2.btnRes.clicked.connect(self.otvet_5)
        self.md2.btnNext.clicked.connect(self.next_med)
    def Back_6(self):
        self.hide()
        med = windowMedium1(self)
        med.show()
    def otvet_5(self):
        if self.md2.lineEdit.text()==str(30):#Проверка ответа
            self.md2.labelStat.setText("<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>")
        else:
            self.md2.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")
    def next_med(self):
        if self.md2.labelStat.text()=="<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>":
            self.hide()
            s_med1 = windowMedium3(self)
            s_med1.show()
        else:
           self.md2.labelStat.setText("<html><head/><body><p align=\"center\">Сначала решите задачу</p></body></html>")

class windowMedium3(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self, parent)
        self.md3 = Ui_Medium3()
        self.md3.setupUi(self)
        self.md3.btnBack.clicked.connect(self.Back_7)
        self.md3.btnRes.clicked.connect(self.otvet_5)
        self.md3.btnNext.clicked.connect(self.next_med)
    def Back_7(self):
        self.hide()
        s_med = windowMedium2(self)
        s_med.show()
    def otvet_5(self):
        if self.md3.lineEdit.text()==str(50):#Проверка ответа
            self.md3.labelStat.setText("<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>")
        else:
            self.md3.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")
    def next_med(self):
        if self.md3.labelStat.text()=="<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>":
            self.hide()
            s_med2 = EasyEnd(self)
            s_med2.show()
        else:
           self.md1.labelStat.setText("<html><head/><body><p align=\"center\">Сначала решите задачу</p></body></html>")

class windowHard1(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self,parent)
        self.hd1 = Ui_Hard1()
        self.hd1.setupUi(self)
        self.hd1.btnBack.clicked.connect(self.Back_8)
        self.hd1.btnRes.clicked.connect(self.otvet_6)
        self.hd1.btnNext.clicked.connect(self.next_had1)
    def Back_8(self):
        self.hide()
        l = windowLvl(self)
        l.show()
    def otvet_6(self):
        if self.hd1.lineEdit.text()==str(25):#Проверка ответа
            self.hd1.labelStat.setText("<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>")
        else:
            self.hd1.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")
    def next_had1(self):
        if self.hd1.labelStat.text()=="<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>":
            self.hide()
            h = windowHard2(self)
            h.show()
        else:
           self.hd1.labelStat.setText("<html><head/><body><p align=\"center\">Сначала решите задачу</p></body></html>")


class windowHard2(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self, parent)
        self.hd2 = Ui_Hard2()
        self.hd2.setupUi(self)
        self.hd2.btnBack.clicked.connect(self.Back_9)
        self.hd2.btnRes.clicked.connect(self.otvet_7)
        self.hd2.btnNext.clicked.connect(self.next_had2)
    def Back_9(self):
        self.hide()
        h1 = windowHard1(self)
        h1.show()


    def otvet_7(self):
        if self.hd2.lineEdit.text() == str(40):
            self.hd2.labelStat.setText("<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>")
        else:
            self.hd2.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")


    def next_had2(self):#Проверка ответа
        if self.hd2.labelStat.text() == "<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>":
            self.hide()
            h1 = windowHard3(self)
            h1.show()
        else:
            self.hd2.labelStat.setText("<html><head/><body><p align=\"center\">Сначала решите задачу</p></body></html>")


class windowHard3(QtWidgets.QMainWindow): #Создание класса(Отображения окна)
    def __init__(self, parent=None):
        QtWidgets.QWidget.__init__(self,parent)
        self.hd3 = Ui_Hard3()
        self.hd3.setupUi(self)
        self.hd3.btnBack.clicked.connect(self.Back_10)
        self.hd3.btnRes.clicked.connect(self.otvet_8)
        self.hd3.btnNext.clicked.connect(self.next_had3)
    def Back_10(self):
        self.hide()
        hd = windowHard2(self)
        hd.show()
    def otvet_8(self):
        if self.hd3.lineEdit.text()==str(22): #Проверка ответа
            self.hd3.labelStat.setText("<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>")
        else:
            self.hd3.labelStat.setText("<html><head/><body><p align=\"center\">Неправильный ответ</p></body></html>")
    def next_had3(self):
        if self.hd3.labelStat.text()=="<html><head/><body><p align=\"center\">ЗАДАЧА РЕШЕНА<br/></p></body></html>":
            self.hide()
            h = EasyEnd(self)
            h.show()
        else:
           self.hd3.labelStat.setText("<html><head/><body><p align=\"center\">Сначала решите задачу</p></body></html>")


if __name__=='__main__': #Запуск Программы
    app = QtWidgets.QApplication(sys.argv)
    w = windowHack()
    w.show()
    sys.exit(app.exec_())
