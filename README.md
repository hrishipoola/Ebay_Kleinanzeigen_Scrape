# Ebay Kleinanzeigen Scrape

My daughter Danae's birthday is on the horizon. Since she adores Peppa Pig, I scraped [Ebay Kleinanzeigen](https://www.ebay-kleinanzeigen.de) (Germany's eBay classifieds) for inspiration that I could later organize by seller neighborhood and price. 

I built 2 scrapers, each generating the same result - a dataframe of Peppa-related items in Berlin with product title, image, price, neighborhood, zipcode, and link. I was surprised by the variety of Peppa gear, including items for supporting characters!

First, I used BeautifulSoup and constructed urls based on search criteria for the first 8 pages (what I was allowed to scrape), looped through each page to scrape contents, and created a dataframe. I was able to scrape 125 items. 

Next, I used a more elegant approach building a [Scrapy Spider](https://docs.scrapy.org/en/latest/topics/spiders.html) that scraped each item for contents and, if there was a next page link, followed the next page link using a callback and continued to scrape until there were no more pages, finally creating a dataframe. I was able to scrape 174 items using this approach. 

In both, since I didn't use Selenium, in order to simulate natural queries, I cycled randomly through different user agents and sleep time intervals, an approach I learned from [Achim Tack](https://github.com/AchimTack/GoogleTrafficParser/blob/master/google_traffic_parser.py). As a note, for prices, I excluded the text 'VB', or verhandlungsbasis (negotiable), as, in my experience, any item on eBay is negotiable. I also found that for more challenging-to-parse text between elements, xpath worked better than css.
