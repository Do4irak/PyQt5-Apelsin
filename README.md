import sys #импорт ситстемы

from PyQt5 import QtCore, QtGui, QtWidgets

from hack import Ui_Window   # импорт файла qt

from Rule import Ui_WindowRule # импорт файла qt

from lvl import Ui_windowLvl # импорт файла qt

class ADDWINDOW1(QtWidgets.QMainWindow): #Создание окна Уровень

    def __init__(self, parent=None):
    
        QtWidgets.QWidget.__init__(self, parent)
        
        self.lvl = Ui_windowLvl()
        
        self.lvl.setupUi(self)
        
        self.lvl.btnBack.clicked.connect(self.back1)
        
    def back1(self):
    
        self.close()

class ADDWINDOW(QtWidgets.QMainWindow): #Создание окна Правила

    def __init__(self, parent=None):
    
        QtWidgets.QWidget.__init__(self, parent)
        
        self.ins = Ui_WindowRule()
        
        self.ins.setupUi(self)
        
        self.ins.pushButton.clicked.connect(self.back)
        
    def back(self):
    
        self.close()


class MyWin(QtWidgets.QMainWindow): #Создание основного меню

    def __init__(self, parent=None):
    
        QtWidgets.QWidget.__init__(self, parent)
        
        self.ui = Ui_Window()
        
        self.ui.setupUi(self)
        
        self.ui.btnRule.clicked.connect(self.openRule) #добавление функционала
        
        self.ui.btnExit.clicked.connect(sys.exit) #выход из программы
        
        self.ui.btnLvl.clicked.connect(self.openLvl)
        
    def openRule(self): #открытие окна Правила
    
        a = ADDWINDOW(self)
        
        a.show()
        
    def openLvl(self): #открытие окна Уровень
    
        s = ADDWINDOW1(self)
        
        s.show()

if __name__ == '__main__': #Запуск программы

    app = QtWidgets.QApplication(sys.argv)
    
    w = MyWin()
    
    w.show()
    
    sys.exit(app.exec_())
