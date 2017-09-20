# Pythonn

#web crawler

#the script below crawls the web and find specific words found in the pages crawled
#the script crawls the furst 10 links foun in the page


import sys

from bs4 import BeautifulSoup #import beautifulsoup
from urllib2 import urlopen	#import urlopen to allow html parser

#url variable declared to hold the link
url = 'https://en.wikipedia.org/wiki/Bank'

#print the link
print url 

#download page and hold it in a variable page1
page1 = urlopen(url)
#variable to hold contents of downloaded page
conts = str(page1.read())

#parse the contents variable to beautifulsoup constructor
soup = BeautifulSoup(conts, 'html.parser')

#find words searching for, from soup constructor
text = soup.find_all('bank')

#find all the links in the parsed document
for link in soup.body.find_all('a'):
	#print the link
	print(link.get('href'))

#skip line
print ('')

#print number of pages found
print('Number of pages crawled ' + str(conts.count('href')))
print ('')

#check if words bank and money is in the links 
if "bank" in conts and "money" in conts:
	print('Bank and Money found in the pages')
else:
    print('Bank and Money was not found in the pages')
print('')

#check if words searching for are in the contents variable parsed
if "bank" in conts:
	#print the word
	print('The word Bank was found')
	#count number of times found and then print the result
	print('number of times used ' + str(conts.count('bank')))
	txt = ('number of times used ' + str(conts.count('bank')) + 'Level of conrcen less than 20%')
	nmbs = str(conts.count('bank'))
	if nmbs > 1000:
		print('Level of conrcen less than 20%')

#store the results in variable txt to be written to file
txt = ('number of times used ' + str(conts.count('bank')) + 'Level of conrcen less than 20%')
print('')

#check if word is in contents variable
if "money"in conts:
	#get the link and print the result
	nmb = str(conts.count('money'))
	print('The Word Money was found on this link ' + link.get('href'))
	print('number of times money was used: ' + nmb)
        if nmb > 30:
		print('Level of conrcen less than 70%')

print('')

#saving to file
fl = open('MyNFs.txt', 'w')
fl.write(str(txt)) #write the contents of variable conts to the file
fl.close() #close the file

def helloworldMethod():
	print("hello")
