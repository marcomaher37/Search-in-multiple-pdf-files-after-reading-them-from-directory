# Read-and-search-from-multiple-pdf-files
## Read and search from multiple pdf files by python using os,re,PyPDF2 lib


## Import os module to get the files in a directory 
import os

## Import PyPDF2 module to work with the pdf files
import PyPDF2

## Import re module to search in the pdf files
import re

## Specify your path of directory
path = r"C:\Users\.."   # (your files directory path)

## Create array to save the files names
file_list=[] 

## Get the files from directory
file_list = os.listdir( path )

## Print the array of files name
print(file_list)

## The source code
    
    # Import os module to get the files in a directory 

    import os
    
    # Import PyPDF2 module to work with the pdf files

    import PyPDF2
    
    # Import re module to search in the pdf files

    import re
    
    # Specify your path of directory

    path = r"C:\Users\.."   # (your files directory path)
    
    # Create array to save the files names

    file_list=[] 
    
    # Get the files from directory

    file_list = os.listdir( path )
    
    # Print the array of files name

    print(file_list)
    
    for i in range(len(file_list)):
    
    # Message to tell the result of each file 
    print("Result of earch in file"+file_list[i])
    
    #Loop for iteration for each list items in array

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
    
