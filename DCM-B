#!/bin/bash


files=$(cat links.txt)
for file in $files
do
  #Download all files
  #-q for quite
  wget -q $file
done



#Loops through all pdf files and put their name into a file
pdf_to_png=$(ls *.pdf)
for pdf_files in $pdf_to_png
do
  echo $pdf_files >> pdffiles.txt
done



#Loops through all files contaning pdf names
for files in $(cat pdffiles.txt)
do
  pdftoppm $files $files -png 
done
#Remove pdffiles.txt
rm pdffiles.txt


#Takes off ong extensions
takeoff_pngext=$(ls *.png)
for each_ext in $takeoff_pngext
do
  echo $each_ext  >> pngfiles.txt
done

#Remove everything containing a pdf extension
rm *.pdf


#Read two lines at once of pngfiles.txt
while read -r first_file;read second_file
do
  convert +append $first_file $second_file out-$first_file-$second_file
done < pngfiles.txt


#remove pngfiles.txt
rm pngfiles.txt

#remove everything ending with 5
rm 5*
