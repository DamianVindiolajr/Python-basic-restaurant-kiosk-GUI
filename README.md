# Python-basic-restaurant-kiosk-GUI
from tkinter import *
import tkinter.messagebox
import tkinter.font

class Application(Frame):
    """ A GUI application displays a restaurant bill with tip options. """
    def __init__(self, master):
        super(Application,self).__init__(master)
        self.grid()
        self.create_widgets()

    def create_widgets(self):
        """ create widgets for restaurant bill tips. """
        Label(self, text = "Please enter subtotal and select your preferred tip Percentage:").grid(row = 0, column = 0, sticky = W)

        self.Percent = StringVar()
        self.Percent.set(None)

        Radiobutton(self, text = "15% tip",
                    variable = self.Percent,
                    value = 1.15,
                    command = self.update_text
                    ).grid(row = 3, column = 0, sticky = W)
        Radiobutton(self, text = "20% tip",
                    variable = self.Percent,
                    value = 1.2,
                    command = self.update_text
                    ).grid(row = 4, column = 0, sticky = W)
        #create a label and text entry
        Label(self,
              text = "SUBTOTAL"
              ).grid(row=2, column=0, sticky=W)
        self.subtotal_ent = Entry(self)
        self.subtotal_ent.grid(row=2, column=0, sticky=W)
        
        self.results_txt = Text(self, width = 40, height = 5, wrap = WORD)
        self.results_txt.grid(row = 6, column = 0, columnspan = 3)

        Label(self,
              text = "                 Feedback! Let us know how we did:").grid(row=5, column = 0, sticky=W)
        self.feedback = Entry(self)
        
    

        
        
                    
    def update_text(self):
        """Update text widget and display choices """
        total_price = float(self.subtotal_ent.get())*float(self.Percent.get())

        user_message = "Your total price: $" + str("%.2f" % total_price)
                              
        self.results_txt.delete(0.0, END)
        self.results_txt.insert(0.0, user_message)
        

root = Tk()
root.geometry("1600x800+0+0)
root.title("Basic Modern Day Kiosk")
app = Application(root)
root.mainloop()
