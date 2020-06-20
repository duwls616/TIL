# webscrapper
> https://www.indeed.com/jobs?q=python 링크에서 제목(job), 위치, 상세페이지 링크를 가져와본다.    
html 추출은 beautifulSoup을 이용하여 추출한다. 
     
     
## BeautifulSoup
> Beautiful Soup 은 HTML 및 XML 문서 를 구문 분석하기위한 Python 패키지      
      
	  
### 사용법   
1. html 추출      
soup = BeautifulSoup(html내용, 가져올타입)	  
       
2. 태그추출     
soup.find(추출할 태그이름,속성)    
-> 맨처음 데이터 하나만 추출된다.    
ex) soup.find("a",id="link3")     
soup.find("a",{"class":"link"})      
          
soup.find_all(추출할 태그이름, 속성)   
-> 모든 데이터 추출되어 리스트반환.    
      
      
```python
import requests
from bs4 import BeautifulSoup

LIMIT = 50
URL = f"https://www.indeed.com/jobs?q=python&limit={LIMIT}"

# 페이지 최대 갯수를 구함
def extract_indeed_pages():
  result = requests.get(URL)

  soup = BeautifulSoup(result.text,"html.parser")

  pagination = soup.find("div",{"class":"pagination"})

  links = pagination.find_all('a')

  pages = []
  for link in links[0:-1]:
    pages.append(int(link.string))

  pages = pages[0:-1]
  max_page = pages[-1]

  return max_page

# title, location, link 추출
def extract_job(html):
  title = html.find("h2",{"class":"title"}).find("a")["title"]
  company = html.find("span",{"class":"company"})
  company_anchor = company.find("a")
  if company_anchor is not None:
    company = str(company_anchor.string)
  else:
    company = str(company.string)

  #pythone strip - 파라미터의 문자를 모두 지워준다.
  company = company.strip()
  location = html.find("div",{"class":"recJobLoc"})["data-rc-loc"]
  job_id = html["data-jk"]
  
  return {'title':title,'company':company,'location':location,'link':f"https://www.indeed.com/viewjob?jk={job_id}"}

def extract_indeed_jobs(last_pages):
 
  jobs = []
  for page in range(last_pages):
    print(f"Scrapping page {page}")
    result = requests.get(f"{URL}&start={page*LIMIT}")
    soup = BeautifulSoup(result.text,"html.parser")
    results = soup.find_all("div",{"class":"jobsearch-SerpJobCard"})
    for result in results:
      job = extract_job(result)
      jobs.append(job)

  return jobs
```