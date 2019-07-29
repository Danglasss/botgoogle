from bs4 import BeautifulSoup
from urllib.request import urlopen, Request
        
def main():
    page = get_page("https://www.google.com/search?ei=hKE8XZ3qD6iCjLsP84qcwA0&q=hypnotherapeute+paris&oq=hypotherapeute+&gs_l=psy-ab.3.0.35i304i39j0i13l9.1549.3659..5051...0.0..0.94.435.7......0....1..gws-wiz.......35i39j0i10i203j0i10j35i305i39.TzPyd8p5fXg")
    find_link(page)

def get_page(reg_url):
    headers = {'User-Agent': 'Mozilla/5.0 (Window NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/42.0.2228.0 Safari/537.3'}
    req = Request(url=reg_url, headers=headers)
    if req is not None :
        html = urlopen(req).read()
        if html is not None :
            page = BeautifulSoup(html, 'lxml')
    return (page)

def find_link(html):
    websites = list()
    link = html.find_all('a')
    for url in link:
        liens = url.get("href")
        if liens is not None and liens.count('google') == 0 and liens.find('https://') == 0:
            websites.append(liens)
    websites.append(None)
    print(websites)
    scraping_page(websites, 0)

def scraping_page(websites, index):
    tab = [["Liens"], ["Numeros"], ["Adresse mail"], ["Nom"], ["prenom"]]
    if websites[index] != None:
        page = get_page(websites[index])
        #if websites[index].count('doctilib')
        #    programme(page)
        #    scraping_page(websites, index + 1)
        link = page.find_all('a')
        for url in link:
            liens = url.get("href")
            if liens is not None and liens.count('contact') and liens.count('A propos'):
                data_collect(lien, tab)
        scraping_page(websites, index + 1)

def data_collect(lien, tab):
    tab[0].append()  
    tab[1].append() 
    tab[2].append()  
    tab[3].append()
    tab[4].append() 

if __name__ == "__main__":
    main()
