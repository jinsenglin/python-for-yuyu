# Sample project 5

Open terminal and run

```bash
pyenv shell 2.7.13

cd ~/Desktop/venvs

virtualenv sample5

source ~/Desktop/venvs/sample5/bin/activate

pip install scrapy

mkdir ~/Desktop/venvs/sample5/src
cd ~/Desktop/venvs/sample5/src
```

Create a file named main.py with following content:

```py
import scrapy

class BlogSpider(scrapy.Spider):
    name = 'blogspider'
    start_urls = ['https://blog.scrapinghub.com']

    def parse(self, response):
        for title in response.css('h2.entry-title'):
            yield {'title': title.css('a ::text').extract_first()}

        next_page = response.css('div.prev-post > a ::attr(href)').extract_first()
        if next_page:
            yield scrapy.Request(response.urljoin(next_page), callback=self.parse)
```

Run by

```bash
scrapy runspider main.py
```

Output

```
2017-03-17 18:47:43 [scrapy.utils.log] INFO: Scrapy 1.3.3 started (bot: scrapybot)
2017-03-17 18:47:43 [scrapy.utils.log] INFO: Overridden settings: {'SPIDER_LOADER_WARN_ONLY': True}
2017-03-17 18:47:43 [scrapy.middleware] INFO: Enabled extensions:
['scrapy.extensions.logstats.LogStats',
 'scrapy.extensions.telnet.TelnetConsole',
 'scrapy.extensions.corestats.CoreStats']
2017-03-17 18:47:43 [scrapy.middleware] INFO: Enabled downloader middlewares:
['scrapy.downloadermiddlewares.httpauth.HttpAuthMiddleware',
 'scrapy.downloadermiddlewares.downloadtimeout.DownloadTimeoutMiddleware',
 'scrapy.downloadermiddlewares.defaultheaders.DefaultHeadersMiddleware',
 'scrapy.downloadermiddlewares.useragent.UserAgentMiddleware',
 'scrapy.downloadermiddlewares.retry.RetryMiddleware',
 'scrapy.downloadermiddlewares.redirect.MetaRefreshMiddleware',
 'scrapy.downloadermiddlewares.httpcompression.HttpCompressionMiddleware',
 'scrapy.downloadermiddlewares.redirect.RedirectMiddleware',
 'scrapy.downloadermiddlewares.cookies.CookiesMiddleware',
 'scrapy.downloadermiddlewares.stats.DownloaderStats']
2017-03-17 18:47:43 [scrapy.middleware] INFO: Enabled spider middlewares:
['scrapy.spidermiddlewares.httperror.HttpErrorMiddleware',
 'scrapy.spidermiddlewares.offsite.OffsiteMiddleware',
 'scrapy.spidermiddlewares.referer.RefererMiddleware',
 'scrapy.spidermiddlewares.urllength.UrlLengthMiddleware',
 'scrapy.spidermiddlewares.depth.DepthMiddleware']
2017-03-17 18:47:43 [scrapy.middleware] INFO: Enabled item pipelines:
[]
2017-03-17 18:47:43 [scrapy.core.engine] INFO: Spider opened
2017-03-17 18:47:43 [scrapy.extensions.logstats] INFO: Crawled 0 pages (at 0 pages/min), scraped 0 items (at 0 items/min)
2017-03-17 18:47:43 [scrapy.extensions.telnet] DEBUG: Telnet console listening on 127.0.0.1:6023
2017-03-17 18:47:45 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com> (referer: None)
2017-03-17 18:47:45 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com>
{'title': u'Looking Back at 2016'}
2017-03-17 18:47:45 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com>
{'title': u'How to Increase Sales with Online Reputation Management'}
2017-03-17 18:47:45 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com>
{'title': u'How to Build your own Price Monitoring Tool'}
2017-03-17 18:47:45 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com>
{'title': u'How You Can Use Web Data to Accelerate Your Startup'}
2017-03-17 18:47:45 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com>
{'title': u'An Introduction to XPath: How to Get Started'}
2017-03-17 18:47:45 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com>
{'title': u'Why Promoting Open Data Increases Economic Opportunities'}
2017-03-17 18:47:45 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com>
{'title': u'Interview: How Up Hail uses Scrapy to Increase Transparency'}
2017-03-17 18:47:45 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com>
{'title': u'How to Run Python Scripts in Scrapy Cloud'}
2017-03-17 18:47:45 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com>
{'title': u'Embracing the Future of Work: How To Communicate Remotely'}
2017-03-17 18:47:45 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com>
{'title': u'How to Deploy Custom Docker Images for Your Web Crawlers'}
2017-03-17 18:47:46 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com/page/2/> (referer: https://blog.scrapinghub.com)
2017-03-17 18:47:46 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/2/>
{'title': u'Improved Frontera: Web Crawling at Scale with Python 3 Support'}
2017-03-17 18:47:46 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/2/>
{'title': u'How to Crawl the Web Politely with Scrapy'}
2017-03-17 18:47:46 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/2/>
{'title': u'Introducing Scrapy Cloud with Python 3 Support'}
2017-03-17 18:47:46 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/2/>
{'title': u'What the Suicide Squad Tells Us About Web Data'}
2017-03-17 18:47:46 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/2/>
{'title': u'This Month in Open Source at Scrapinghub August 2016'}
2017-03-17 18:47:46 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/2/>
{'title': u'Meet Parsel: the Selector Library behind Scrapy'}
2017-03-17 18:47:46 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/2/>
{'title': u'Incremental Crawls with Scrapy and DeltaFetch'}
2017-03-17 18:47:46 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/2/>
{'title': u'Improving Access to Peruvian Congress Bills with Scrapy'}
2017-03-17 18:47:46 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/2/>
{'title': u'Scrapely: The Brains Behind Portia Spiders'}
2017-03-17 18:47:46 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/2/>
{'title': u'Introducing Portia2Code: Portia Projects into Scrapy Spiders'}
2017-03-17 18:47:47 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com/page/3/> (referer: https://blog.scrapinghub.com/page/2/)
2017-03-17 18:47:47 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/3/>
{'title': u'Scraping Infinite Scrolling Pages'}
2017-03-17 18:47:47 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/3/>
{'title': u'This Month in Open Source at Scrapinghub June 2016'}
2017-03-17 18:47:47 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/3/>
{'title': u'Introducing the Datasets Catalog'}
2017-03-17 18:47:47 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/3/>
{'title': u'Introducing the Crawlera Dashboard'}
2017-03-17 18:47:47 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/3/>
{'title': u'Data Extraction with Scrapy and Python 3'}
2017-03-17 18:47:47 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/3/>
{'title': u'How to Debug your Scrapy Spiders'}
2017-03-17 18:47:47 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/3/>
{'title': u'Scrapy + MonkeyLearn: Textual Analysis of Web Data'}
2017-03-17 18:47:47 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/3/>
{'title': u'Introducing Scrapy Cloud 2.0'}
2017-03-17 18:47:47 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/3/>
{'title': u'A (not so) Short Story on Getting Decent Internet Access'}
2017-03-17 18:47:47 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/3/>
{'title': u'Scraping Websites Based on ViewStates with Scrapy'}
2017-03-17 18:47:48 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com/page/4/> (referer: https://blog.scrapinghub.com/page/3/)
2017-03-17 18:47:48 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/4/>
{'title': u'Machine Learning with Web Scraping: New MonkeyLearn Addon'}
2017-03-17 18:47:48 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/4/>
{'title': u'Mapping Corruption in the Panama Papers with Open Data'}
2017-03-17 18:47:48 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/4/>
{'title': u'Web Scraping to Create Open Data'}
2017-03-17 18:47:48 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/4/>
{'title': u'Scrapy Tips from the Pros: March 2016 Edition'}
2017-03-17 18:47:48 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/4/>
{'title': u'This Month in Open Source at Scrapinghub March 2016'}
2017-03-17 18:47:48 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/4/>
{'title': u'Join Scrapinghub for Google Summer of Code 2016'}
2017-03-17 18:47:48 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/4/>
{'title': u'How Web Scraping is Revealing Lobbying and Corruption in Peru'}
2017-03-17 18:47:48 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/4/>
{'title': u'Splash 2.0 Is Here with Qt 5 and Python 3'}
2017-03-17 18:47:48 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/4/>
{'title': u'Migrate your Kimono Projects to Portia'}
2017-03-17 18:47:48 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/4/>
{'title': u'Scrapy Tips from the Pros: February 2016 Edition'}
2017-03-17 18:47:49 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com/page/5/> (referer: https://blog.scrapinghub.com/page/4/)
2017-03-17 18:47:49 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/5/>
{'title': u'Portia: The Open Source Alternative to Kimono Labs'}
2017-03-17 18:47:49 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/5/>
{'title': u'Web Scraping Finds Stores Guilty of Price Inflation'}
2017-03-17 18:47:49 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/5/>
{'title': u'Python 3 is Coming to Scrapy'}
2017-03-17 18:47:49 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/5/>
{'title': u'Happy Anniversary: Scrapinghub Turns 5'}
2017-03-17 18:47:49 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/5/>
{'title': u'Scrapy Tips from the Pros: Part 1'}
2017-03-17 18:47:49 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/5/>
{'title': u'Vizlegal: Rise of Machine-Readable Laws and Court Judgments'}
2017-03-17 18:47:49 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/5/>
{'title': u'Christmas Eve vs New Year\u2019s Eve: Last Minute Price Inflation?'}
2017-03-17 18:47:49 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/5/>
{'title': u'Looking Back at 2015'}
2017-03-17 18:47:49 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/5/>
{'title': u'Winter Sales Showdown: Black Friday vs Cyber Monday vs Green Monday'}
2017-03-17 18:47:49 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/5/>
{'title': u'Chats With RINAR Solutions'}
2017-03-17 18:47:50 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com/page/6/> (referer: https://blog.scrapinghub.com/page/5/)
2017-03-17 18:47:50 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/6/>
{'title': u'Black Friday, Cyber Monday: Are They Worth It?'}
2017-03-17 18:47:50 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/6/>
{'title': u'Tips for Creating a Cohesive Company Culture Remotely'}
2017-03-17 18:47:50 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/6/>
{'title': u'Parse Natural Language Dates with Dateparser'}
2017-03-17 18:47:50 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/6/>
{'title': u'Aduana: Link Analysis to Crawl the Web at Scale'}
2017-03-17 18:47:50 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/6/>
{'title': u'Scrapy on the Road to Python 3 Support'}
2017-03-17 18:47:50 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/6/>
{'title': u'Introducing Javascript support for Portia'}
2017-03-17 18:47:50 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/6/>
{'title': u'Distributed Frontera: Web Crawling at Scale'}
2017-03-17 18:47:50 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/6/>
{'title': u'The Road to Loading JavaScript in Portia'}
2017-03-17 18:47:50 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/6/>
{'title': u'EuroPython 2015'}
2017-03-17 18:47:50 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/6/>
{'title': u'StartupChats Remote Working Q&A'}
2017-03-17 18:47:51 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com/page/7/> (referer: https://blog.scrapinghub.com/page/6/)
2017-03-17 18:47:51 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/7/>
{'title': u'PyCon Philippines 2015'}
2017-03-17 18:47:51 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/7/>
{'title': u'Google Summer of Code 2015'}
2017-03-17 18:47:51 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/7/>
{'title': u'Link Analysis Algorithms Explained'}
2017-03-17 18:47:51 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/7/>
{'title': u'EuroPython, here we go!'}
2017-03-17 18:47:51 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/7/>
{'title': u'Using git to manage vacations in a large distributed team'}
2017-03-17 18:47:51 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/7/>
{'title': u'Gender Inequality Across Programming Languages'}
2017-03-17 18:47:51 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/7/>
{'title': u'Traveling Tips for Remote Workers'}
2017-03-17 18:47:51 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/7/>
{'title': u'A Career in Remote Working'}
2017-03-17 18:47:51 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/7/>
{'title': u'Frontera: The Brain Behind the Crawls'}
2017-03-17 18:47:51 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/7/>
{'title': u'Scrape Data Visually with Portia and Scrapy Cloud'}
2017-03-17 18:47:52 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com/page/8/> (referer: https://blog.scrapinghub.com/page/7/)
2017-03-17 18:47:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/8/>
{'title': u'Scrapinghub: A Remote Working Success Story'}
2017-03-17 18:47:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/8/>
{'title': u'Why we moved to Slack'}
2017-03-17 18:47:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/8/>
{'title': u'The History of Scrapinghub'}
2017-03-17 18:47:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/8/>
{'title': u'Skinfer: A Tool for Inferring JSON Schemas'}
2017-03-17 18:47:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/8/>
{'title': u'Handling JavaScript in Scrapy with Splash'}
2017-03-17 18:47:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/8/>
{'title': u'Scrapinghub Crawls the Deep Web'}
2017-03-17 18:47:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/8/>
{'title': u'New Changes to Our Scrapy Cloud Platform'}
2017-03-17 18:47:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/8/>
{'title': u'Introducing ScrapyRT: An API for Scrapy spiders'}
2017-03-17 18:47:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/8/>
{'title': u'Looking Back at 2014'}
2017-03-17 18:47:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/8/>
{'title': u'XPath Tips from the Web Scraping Trenches'}
2017-03-17 18:47:53 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com/page/9/> (referer: https://blog.scrapinghub.com/page/8/)
2017-03-17 18:47:53 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/9/>
{'title': u'Introducing Data Reviews'}
2017-03-17 18:47:53 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/9/>
{'title': u'Extracting schema.org Microdata Using Scrapy Selectors and XPath'}
2017-03-17 18:47:53 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/9/>
{'title': u'Announcing Portia, the Open Source Visual Web Scraper!'}
2017-03-17 18:47:53 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/9/>
{'title': u'Optimizing Memory Usage of Scikit-Learn Models Using Succinct Tries'}
2017-03-17 18:47:53 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/9/>
{'title': u'Open Source at Scrapinghub'}
2017-03-17 18:47:53 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/9/>
{'title': u'Looking Back at 2013'}
2017-03-17 18:47:53 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/9/>
{'title': u'Marcos Campal Is a ScrapingHubber!'}
2017-03-17 18:47:53 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/9/>
{'title': u'Introducing Dash'}
2017-03-17 18:47:53 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/9/>
{'title': u'Why MongoDB Is a Bad Choice for Storing Our Scraped Data'}
2017-03-17 18:47:53 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/9/>
{'title': u'Introducing Crawlera, a Smart Page Downloader'}
2017-03-17 18:47:54 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com/page/10/> (referer: https://blog.scrapinghub.com/page/9/)
2017-03-17 18:47:54 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/10/>
{'title': u'Git Workflow for Scrapy Projects'}
2017-03-17 18:47:54 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/10/>
{'title': u'How to Fill Login Forms Automatically'}
2017-03-17 18:47:54 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/10/>
{'title': u'Spiders activity graphs'}
2017-03-17 18:47:54 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/10/>
{'title': u'Finding Similar Items'}
2017-03-17 18:47:54 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/10/>
{'title': u'Scrapy 0.15 dropping support for Python 2.5'}
2017-03-17 18:47:54 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/10/>
{'title': u'Autoscraping casts a wider net'}
2017-03-17 18:47:54 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/10/>
{'title': u'Scrapy 0.14 released'}
2017-03-17 18:47:54 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/10/>
{'title': u'Dirbot \u2013 a new example Scrapy project'}
2017-03-17 18:47:54 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/10/>
{'title': u'Introducing w3lib and scrapely'}
2017-03-17 18:47:54 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/10/>
{'title': u'Scrapy 0.12 released'}
2017-03-17 18:47:55 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://blog.scrapinghub.com/page/11/> (referer: https://blog.scrapinghub.com/page/10/)
2017-03-17 18:47:55 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/11/>
{'title': u'Spoofing your Scrapy bot IP using tsocks'}
2017-03-17 18:47:55 [scrapy.core.scraper] DEBUG: Scraped from <200 https://blog.scrapinghub.com/page/11/>
{'title': u'Hello, world'}
2017-03-17 18:47:55 [scrapy.core.engine] INFO: Closing spider (finished)
2017-03-17 18:47:55 [scrapy.statscollectors] INFO: Dumping Scrapy stats:
{'downloader/request_bytes': 2933,
 'downloader/request_count': 11,
 'downloader/request_method_count/GET': 11,
 'downloader/response_bytes': 123061,
 'downloader/response_count': 11,
 'downloader/response_status_count/200': 11,
 'finish_reason': 'finished',
 'finish_time': datetime.datetime(2017, 3, 17, 10, 47, 55, 479063),
 'item_scraped_count': 102,
 'log_count/DEBUG': 114,
 'log_count/INFO': 7,
 'request_depth_max': 10,
 'response_received_count': 11,
 'scheduler/dequeued': 11,
 'scheduler/dequeued/memory': 11,
 'scheduler/enqueued': 11,
 'scheduler/enqueued/memory': 11,
 'start_time': datetime.datetime(2017, 3, 17, 10, 47, 43, 396545)}
2017-03-17 18:47:55 [scrapy.core.engine] INFO: Spider closed (finished)
```

References

* https://scrapy.org/
