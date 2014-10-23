PPP_Scraper
===========
This is an implementation of the scraperwiki package. The app connects to the UN Department of Peacekeeping (DPKO) report on troop contributions for the previous month hosted on their website. The url pattern uses the pattern `http://www.un.org/en/peacekeeping/contributors/<year>/<3 or 4 letter month abbr><last 2 numbers of year>_3.pdf`. March 2014's file would be at `http://www.un.org/en/peacekeeping/contributors/2014/mar14_3.pdf` for instance. 

The app then converts the pdf to xml and uses page position to parse into a sqllite db.  Country names are positioned between 130 and 140 px left, mission designations are between 276 and 280 px left, and data is anything more than 350 px left. This app is built to run on the Morph.io platform which contains an API that is used by the [PPP_Loader](https://github.com/IPIDataLab/PPP_Loader) app. It is also possible to run scraperwiki locally, though I've had trouble getting it to work.

Morph.io runs this script directly from GitHub once daily and data is only inserted if it doesnt exist in db.

## Dependencies
-	[scraperwiki](https://blog.scraperwiki.com/ "ScraperWiki") - Web scraping library. The PDF to XML functionality to convert into parsable format.
-	[Request](http://docs.python-requests.org/en/latest/ "Requests") - Python HTTP library to check connection
-	[lxml](http://lxml.de/ "lxml") - Python XML library to navigate the XML tree
-	python native modules: `time`, `datetime`, `calendar`, `urllib2`
-	Data source: [DPKO website](http://www.un.org/en/peacekeeping/resources/statistics/contributors.shtml "DPKO")