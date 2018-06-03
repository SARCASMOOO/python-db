'''
Databases

December 5th 2015

This will accept GIF pictures
Simple Graphics was not used.

OOP was used to create several instanecs then saved to the dictionary, using 
student id as the key. The object was saved. Most of the script is basicly graphics.
'''

#imports
from tkinter import *

#Dictionary used for all objects private so get and set methods must be used

#This will store all the instances		
studentList = {}
counter = 0

class studentsWork:
	def __init__(self):
		#Initialize Create the object
		self.__id = 0
		self.__name = ''
		self.__average = 0
		self.__studentPicture = 0

	#Getter methods
	def getStudentinfo(self):
		#Return in a list all the info of this instance
		studentInfo = [self.__id, self.__name, self.__average,  self.__studentPicture]
		return studentInfo 
		
	#Setter methods
	def setStudent(self, id, name, average, studentPicture):
		#update database
		self.__id = id
		self.__name = name
		self.__average = average
		self.__studentPicture = studentPicture
	
def close():
	quit()
	
def ok(inputBox, input, input2, input3, input4):
	#Add the elements to the dictionary
	imageLoad = None
	#Convert from string var back to string
	input  = input.get()
	input2 = input2.get()
	input3 = input3.get()
	input4 = input4.get()
	
	#Lood For image
	try:
		imageLoad = PhotoImage(file="./" + input4)
		print(imageLoad)
	except: 
		print(chr(7) + 'Invalid Image')
		
	#Destroy the pop up window
	inputBox.destroy()
	
	#new instance of this class
	instance = studentsWork()
	
	#add the instance of the class to a dictionary
	global studentList
	instance.setStudent(input, input2, input3, imageLoad)
	studentList[str(input)] = instance
	
	
def updateDB():
	#Ask for all the student fields
	
	#GRAPHICS 
	inputBox = Tk()
	
	input = StringVar(inputBox)
	input2 = StringVar(inputBox)
	input3 = StringVar(inputBox)
	input4 = StringVar(inputBox)
	
	top = Toplevel(inputBox)
	
	Label(top, text="Student Id").pack()
	labelEntry1 = Entry(top, textvariable = input)
	labelEntry1.pack(padx=5)
	
	Label(top, text="Student Name").pack()
	labelEntry2 = Entry(top, textvariable = input2)
	labelEntry2.pack(padx=5)
	
	Label(top, text="Student Average").pack()
	labelEntry3 = Entry(top, textvariable = input3)
	labelEntry3.pack(padx=5)
	
	Label(top, text="Name of Student picutre").pack()
	labelEntry4 = Entry(top, textvariable = input4)
	labelEntry4.pack(padx=5)
	
	buttonOk = Button(top, text="OK", command= lambda: ok(inputBox, input, input2, input3, input4))
	buttonOk.pack(pady=5)
	
def getSearch(deleteKey):
	#New window and get search key
	inputBox = Tk()
	input = StringVar(inputBox)
	top = Toplevel(inputBox)
	
	if deleteKey == False:
		output = ("Please enter a key")
	else:
		output = ("Please enter a key to delete")
	Label(top, text= output).pack()
	labelEntry1 = Entry(top, textvariable = input)
	labelEntry1.pack(padx=5)
	
	buttonOk = Button(top, text="OK", command = lambda: query(input, inputBox, deleteKey))
	buttonOk.pack(pady=5)
	
	
	
def query(input, window, deleteKey):
	#Look up query then output results
	window.destroy()
	
	key = input.get()
	result = None
	found = False
	output = ''
	
	if len(studentList) == 1:
		if key in studentList:
			found = True
			result = studentList[key]
		else:
			print('Key Not found')
	elif len(studentList) < 1:
		print('database is empty')
	else:
		if key in studentList:	
			found = True
			result = studentList[key]
	
	#Display results
	if found == True:
		instance = studentList[key]
		info = instance.getStudentinfo()
		
		if deleteKey == False:
			output = ('Student ID: ' + str(info[0]) + 'Student Name: ' + str(info[1]) + 'Student Average: ' + str(info[2]))
		else:
			#Delete Key
			output = ('Key : ' + str(info[0]) + 'was succesfully deleted: Student Name: ' + str(info[1]) + 'Student Average: ' + str(info[2]))
			del studentList[key]
	else:	
		print('Invalid key' + chr(7))
		output = ('Invalid Key')
	#Display Text
	Label(text=(output)).pack()
	
	#Display image
	if info[3] != None:
		#Display image
		print('Image loading')
		pictureBox = Toplevel()
		Label(pictureBox, image=info[3]).pack() 


#Create the Menu
def graphics(master):
	
	master.resizable(width=False, height=False)
	master.maxsize(800,600)
	master.minsize(800,600)

	button1 = Button(master, text = 'Add New Student               ', command = updateDB)
	button1.pack(side="top")

	button2 = Button(master, text = 'Look up a specific key        ', command = lambda: getSearch(deleteKey = False))
	button2.pack(side="top")

	button3 = Button(master, text = 'Remove element using Key', command = lambda: getSearch(deleteKey = True))
	button3.pack(side="top")
	
	mainloop()

master = Tk()

counter += 1
if counter == 1:
	graphics(master)
	
quit()
