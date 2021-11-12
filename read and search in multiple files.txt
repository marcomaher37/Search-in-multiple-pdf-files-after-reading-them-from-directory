# -*- coding: utf-8 -*-

# Import os module to get the files in a directory 
import os

# Import PyPDF2 module to work with the pdf files
import PyPDF2

# Import re module to search in the pdf files
import re

# Specify your path of directory
path = r"C:\Users\m\Desktop\Untitled Folder\week2\data files"

# Array list to save the files names
file_list=[] 

# Get the files from directory
file_list = os.listdir( path )
# Print the array of files name

print(file_list)
# Read each file in the directory

# Loop for iteration for each list in array
for i in range(len(file_list)):
    
    # Message to tell the result of each file 
    print("Result of earch in file"+file_list[i])
    # Open the file and read it
    f = open(path+'\\'+file_list[i],'rb') 
    pdf_text = [0]
    pdf_reader = PyPDF2.PdfFileReader(f) 
   
    # Read each page in the file  
    for p in range(pdf_reader.numPages):
        page = pdf_reader.getPage(p)
        pdf_text.append(page.extractText())
        
    # Show all result of search in file    
    for match in re.finditer("learning",str(pdf_text)):
        print(match.span())
   
    # New line to begin a new iteration   
    print("")
    