# WebScraping.github.io
import requests
from bs4 import BeautifulSoup

url = 'https://www.google.com/'
r = requests.get(url)
htmlContent = r.content
#print(htmlContent)

soup = BeautifulSoup(htmlContent, 'html.parser')
print(soup.prettify)

title = soup.title
print(title)
print(type(title)) #1.Tag -- Object
print(type(title.string)) # 2.NavigationString
print(type(soup)) # 3. BeautifulSoup

paras = soup.find_all('p') #To get all the paras
print(paras)

anchors = soup.find_all('a') #To get all the anchor tags
print(anchors)
for link in anchors:
    print(link.get('href')) #To get all the links from the page in a one by one - line by line manner

print(soup.find('p')) #To find the first paras
#print(soup.find('p')['class']) #To get classes of any element in the HTML page
print(soup.find_all("p", class_ = "lead"))#To find the elements with class lead

print(soup.find('p').get_text())#Get the text
print(soup.get_text()) # get the text from the entire text - no tags, no style, only texts
