# Ebay Kleinanzeigen Scrape

My daughter Danae's birthday is approaching. She loves Peppa Pig. I decided to scrape Ebay Kleinanzeigen (Germany's eBay classifieds) for inspiration and ideas that I could later organize by seller neighborhood and price. I was surprised by the variety and creativity of Peppa gear! 

With a search for 'Peppa' in Berlin, I scraped product title, image, price, neighborhood, zipcode, and link for each item using 2 approaches. 

First, I used BeautifulSoup and constructed urls based on search criteria for the first 8 pages (what I was allowed to scrape), looped through each page to scrape contents, and created a dataframe. I was able to scrape 125 items. 

Next, I used a more elegant approach building a [Scrapy Spider](https://docs.scrapy.org/en/latest/topics/spiders.html) that scraped each item for contents and, if there was a next page link, followed the next page link using a callback and continued to scrape until there were no more pages, finally creating a dataframe. I was able to scrape 174 items using this approach. 

In both, since I didn't use Selenium, in order to simulate natural queries, I cycled randomly through different user agents and sleep time intervals, an approach I learned from [Achim Tack](https://github.com/AchimTack/GoogleTrafficParser/blob/master/google_traffic_parser.py). I also found that for more challenging-to-parse text between unique elements, xpath worked better than css.  
