# flipkart-website-for-all-the-MacBook-products
•	Firstly, Import selenium, Beautiful soup and Pandas packages.
•	Automate a blank browser using browser = webdriver.FireFox()
3.	url = https://www.flipkart.com/laptops/pr?sid=6bo%2Cb5g&fm=neo%2Fmerchandising&iid=M_8b3b3f65-7ceb-4375-912c-d2bcdde87c58_1_372UD5BXDFYS_MC.34WHNYFH5V2Y&otracker1=hp_rich_navigation_PINNED_neo%2Fmerchandising_NA_NAV_EXPANDABLE_navigationCard_cc_13_L1_view-all&cid=34WHNYFH5V2Y&p%5B%5D=facets.brand%255B%255D%3DAPPLE&otracker=clp_metro_expandable_6_26.metroExpandable.METRO_EXPANDABLE_Apple_laptops-store_SKIHMOPFPDC3_wp9&fm=neo%2Fmerchandising&iid=M_b4d0e2ef-aaac-4e7e-9272-9b8be53c2dc5_26.SKIHMOPFPDC3&ppt=clp&ppn=laptops-store&ssid=j5fwd6niaz0hnchs1645514684273
•	Initiate the required URL that we need to scrape using browser.get(“url”)
•	Since it is dynamic page we need to request  html code of the page using soup = BeautifulSoup(browser.page_source, 'html.parser')
•	To know the div and class we need to use inspect mode right clicking on the mouse
•	Now, lets scrape the product name and iterate for all using: [i.text.strip() for i in soup.select('div._4rR01T')]
•	To Scrape and iterate the price use [int(i.text.strip().replace('₹','').replace(',','')) for i in soup.select('div._30jeq3._1_WHN1')]
•	To convert the price into integer we need to remove Rupee symbol and comma. We need to use replace() in order to remove rupee symbol and comma.
•	To get Total_Ratings and Total_reviews which are in  same division and same class we need to use indexing.
•	The specs of the products are under tags : unordered list( ul) and List (li).
•	Get the list (li) using soup.select('ul._1xgFaf')[0]. find_all('li')[0].text.strip()
•	To iterate ul and li using list comprehension. We need to use for r in soup.select('ul._1xgFaf'): 
 data.append([i.text.strip() for i in r.find_all('li')])
•	Define a function named Flipkart() to combine all the scraped data in a dataframe using pd.DataFrame
•	Import the function dataframe to a csv file using .to_csv(‘file name’)
