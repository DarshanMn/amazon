from scrapy.spider import Spider
from scrapy.selector import Selector
from amazon.items import AmazonItem
class AmazonSpider(Spider):
    name = "amazon"
    allowed_domains = ["amazon.com"]
    start_urls = ["http://www.amazon.com/HTC-One-M8-Unlocked-Warranty/product-reviews/B00J3554KE/ref=cm_cr_pr_top_link_2?ie=UTF8&pageNumber=%d&showViewpoints=0&sortBy=bySubmissionDateDescending" % d for d in range (0,3)]
    i=0
    j=0
    k=0

    def parse(self, response):
		sel = Selector(response)
		sites = sel.xpath('//table[@id="productReviews"]/tr/td/div')
		items = []
		for site in sites:
			item = AmazonItem()
			item['date'] = site.xpath('div/span[2]/nobr/text()').extract()
			item['user'] = site.xpath('div[2]/div/div[2]/a/span/text()').extract()
			item['review'] = site.xpath('div[5]/text()').extract()
			item['review'] = [x.strip() for x in item['review']]
			items.append(item)
		return items
