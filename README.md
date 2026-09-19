# 📱 Xiaohongshu (RedNote / 小红书) Scraper & API

<div align="center">

[![Available on Apify](https://img.shields.io/badge/Available_on-Apify-28B52A?style=for-the-badge&logo=apify&logoColor=white)](https://apify.com/scraperpro/xiaohongshu-rednote-trend-scraper?fpr=939u3w&fp_sid=gh_xhs)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg?style=for-the-badge)](#)
[![Success Rate](https://img.shields.io/badge/Success_Rate-99%25+-brightgreen?style=for-the-badge)](#)
[![Zero Cookies](https://img.shields.io/badge/Cookies-None_Required-blue?style=for-the-badge)](#)
[![Pricing](https://img.shields.io/badge/Pricing-Pay_Per_Result-orange?style=for-the-badge)](#)

**The most powerful, cost-effective, and reliable Xiaohongshu (RedNote / 小红书 / RED) scraper and API on Apify. Extract viral posts, influencer analytics, consumer buying sentiment signals, and watermark-free original HD media — 100% autonomously with Zero Login & Zero Cookies Needed.**

[**🚀 Try it Live on Apify**](https://apify.com/scraperpro/xiaohongshu-rednote-trend-scraper?fpr=939u3w&fp_sid=gh_xhs) • [**📖 Documentation**](https://apify.com/scraperpro/xiaohongshu-rednote-trend-scraper?fpr=939u3w&fp_sid=gh_xhs) • [**💬 Support**](mailto:radwanfaris13@gmail.com)

</div>

---

<div align="center">
  <img src="xiaohongshu_scraper_banner.jpg" alt="Xiaohongshu RedNote Scraper by ScraperPro" width="100%">
</div>

---

## 📖 Overview

**Xiaohongshu (Little Red Book / 小红书 / RED)** is China’s #1 lifestyle, fashion, and social commerce network with over 300 million monthly active users. It is the premier platform for uncovering viral product trends, consumer buying signals, and influencer (KOL) marketing performance.

However, extracting data from Xiaohongshu has historically been painful: aggressive WAF rate-limits, mandatory Chinese phone logins, session token expirations, and strict anti-bot mechanisms.

**Xiaohongshu (RedNote) Scraper by ScraperPro** solves this completely. Using autonomous device emulation and server-side stream cursors, you can scrape up to **10,000 notes per run** without supplying a single cookie or login credential.

---

## 🌟 Why Choose ScraperPro Over Other Xiaohongshu Scrapers?

| Feature | ScraperPro Xiaohongshu Scraper | Other Scrapers | Commercial Data APIs |
| :--- | :---: | :---: | :---: |
| **Pricing Model** | **Pay-Per-Result (PPE)** | Expensive Monthly Subs ($50-$200/mo) | High Per-Request Rates |
| **Account / Cookie Requirement** | **None (100% Zero Cookies Needed)** | User Must Supply Personal Cookies | Personal API Keys |
| **Maintenance** | **Instant 1-Click Run** | Broken Sessions / Constant Expiry | Complex Webhooks |
| **E-Commerce Buyer Sentiment** | **Included (NLP Commercial Intent)** | ❌ Not Available | ❌ Not Available |
| **Media Quality** | **Original HD & Watermark-Free MP4** | Compressed Low-Res Thumbnails | Compressed Thumbnails |
| **Official Category Feeds** | **11 Built-in Lifestyle Channels** | Keyword Search Only | Limited Endpoints |
| **Mobile Share Link Resolution** | **Automatic (`xhslink.com`)** | Manual Conversion Required | ❌ Not Supported |
| **Deep Pagination Resumption** | **Stateful Token (`resumptionToken`)** | ❌ None (Duplicate posts on restart) | Complex Offsets |
| **Anti-Bot Reliability** | **Automated Device Handshake** | Frequent IP & Session Bans | Cloudflare Captchas |

---

## ✨ Key Features

- **🛡️ 100% Zero-Cookie Guest Mode:** Never risk your personal Xiaohongshu account or hassle with QR codes and expiring tokens. Works right out of the box.
- **📈 E-Commerce Buyer Sentiment Intelligence:** Built-in NLP algorithms automatically detect high-conversion commercial intent flags (*"where to buy"*, *"link please"*, *"how much"*, *"dupe for"*), product inquiries, and positive consumer praise.
- **🎬 Watermark-Free HD Media:** Extracts direct uncompressed photo galleries and watermark-free MP4 video stream URLs ready for creative analysis or moodboards.
- **🔄 Stateful Resumption Engine (`resumptionToken`):** Checkpoints pagination state so you can resume multi-page scrapes seamlessly with **0 duplicate notes across runs**.
- **📂 11 Real-Time Lifestyle Category Feeds:** Discover breaking trends across Fashion, Cosmetics, Food, Travel, Home, Gaming, Fitness, Movies, Career, Relationships, and Trending Videos.
- **🔗 Universal URL Dispatcher:** Paste raw search URLs, desktop explore links, bare 24-character note IDs, or mobile shortlinks (`xhslink.com`).
- **⚡ High Concurrency & Speed:** 10 parallel detail workers enrich posts concurrently while staying strictly under 150 MB container RAM.

---

## 💡 Practical Use Cases

1. **E-Commerce & Dropshipping Product Discovery:**
   Identify viral products surging on Little Red Book before they hit Amazon, TikTok Shop, or Western markets. Filter by `hasPurchaseIntent: true` to find items users are begging to buy.
2. **Influencer (KOL) & Campaign Analytics:**
   Audit creator engagement, viral engagement ratios (`viralScore`), like-to-collect distribution, and comment volume.
3. **Consumer Sentiment & Social Listening:**
   Track brand sentiment, customer feedback, and product reviews for cosmetics, luxury goods, fashion, and lifestyle brands.
4. **AI & Machine Learning Training Datasets:**
   Gather rich, structured multimodal datasets (high-resolution imagery, text, hashtags, engagement statistics) for computer vision and LLM fine-tuning.

---

## 🛠️ How to Use via API

You can run this scraper directly via the [Apify Console](https://apify.com/scraperpro/xiaohongshu-rednote-trend-scraper?fpr=939u3w&fp_sid=gh_xhs), or integrate it into your backend using the Apify API in Python, JavaScript/Node.js, or cURL.

### 🐍 Python Example

```bash
pip install apify-client
```

```python
from apify_client import ApifyClient

# Initialize the client with your Apify API token
client = ApifyClient("YOUR_APIFY_TOKEN")

# Configure the search parameters
run_input = {
    "keywords": ["OOTD", "Cleanfit"],
    "maxItems": 50,
    "sort": "popularity_descending",
    "noteType": "all",
    "enrichDetails": True,
}

# Start the Actor and wait for it to finish
print("🚀 Starting Xiaohongshu scrape...")
run = client.actor("scraperpro/xiaohongshu-rednote-trend-scraper").call(run_input=run_input)

# Fetch results from the default dataset
dataset_items = client.dataset(run["defaultDatasetId"]).list_items().items
print(f"✅ Successfully scraped {len(dataset_items)} notes!")

for note in dataset_items[:3]:
    print(f"\nTitle: {note.get('title')}")
    print(f"Author: {note.get('author', {}).get('nickname')}")
    print(f"Likes: {note.get('likedCount')}")
    print(f"Purchase Intent: {note.get('sentiment', {}).get('hasPurchaseIntent')}")
    print(f"URL: {note.get('url')}")
```

---

### 🟨 JavaScript / Node.js Example

```bash
npm install apify-client
```

```javascript
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({
    token: 'YOUR_APIFY_TOKEN',
});

const runInput = {
    keywords: ['OOTD', '秋季穿搭'],
    maxItems: 50,
    sort: 'popularity_descending',
    noteType: 'all',
    enrichDetails: true,
};

console.log('🚀 Launching Xiaohongshu Scraper...');
const run = await client.actor('scraperpro/xiaohongshu-rednote-trend-scraper').call(runInput);

const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(`✅ Fetched ${items.length} Xiaohongshu notes!`);

console.log(items.slice(0, 2));
```

---

### 🌐 cURL Example

```bash
curl -X POST "https://api.apify.com/v2/acts/scraperpro~xiaohongshu-rednote-trend-scraper/runs?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "keywords": ["OOTD"],
    "maxItems": 30,
    "sort": "popularity_descending",
    "noteType": "all"
  }'
```

---

## 📤 Sample Output Data

Every dataset record contains 25+ enriched fields, engagement heuristics, and sentiment signals:

```json
{
  "id": "6a7568cc00000000050328d9",
  "title": "Autumn Capsule Wardrobe: 5 Minimalist Outfits for Office & Daily Wear",
  "desc": "Sharing my favorite autumn minimalist styling guide! Coat from vintage thrift store, trousers matched with loafers. Where to buy link below! #AutumnOOTD #CapsuleWardrobe #MinimalistStyle #OfficeFashion",
  "type": "video",
  "url": "https://www.xiaohongshu.com/explore/6a7568cc00000000050328d9?xsec_token=AB4829fa...&xsec_source=pc_feed",
  "author": {
    "id": "647b64a400000000120349b8",
    "nickname": "Elena Daily Style",
    "avatarUrl": "https://sns-avatar-qc.xhscdn.com/avatar/647b64a400000000120349b8.jpg",
    "profileUrl": "https://www.xiaohongshu.com/user/profile/647b64a400000000120349b8",
    "redId": "elena_fashion",
    "bio": "Fashion & Lifestyle Creator in Shanghai | Daily Outfit Inspo",
    "isVerified": false
  },
  "likedCount": 18450,
  "collectedCount": 12890,
  "commentCount": 420,
  "sharedCount": 3150,
  "canShare": true,
  "viralScore": 62450.0,
  "engagementRate": 89.21,
  "imageCount": 2,
  "hasVideo": true,
  "isLivePhoto": false,
  "coverUrl": "https://sns-webpic-qc.xhscdn.com/265/user/1040/01f016a7568cc.jpg",
  "images": [
    "https://sns-webpic-qc.xhscdn.com/265/user/1040/01f016a7568cc.jpg",
    "https://sns-webpic-qc.xhscdn.com/265/user/1040/02f016a7568dd.jpg"
  ],
  "videoUrl": "https://sns-video-qc.xhscdn.com/stream/110/258/01e403d154784a0d9b1a23.mp4",
  "videoDuration": 48,
  "hashtags": ["AutumnOOTD", "CapsuleWardrobe", "MinimalistStyle", "OfficeFashion"],
  "tags": ["OOTD", "Fashion", "Minimalist"],
  "sentiment": {
    "hasPurchaseIntent": true,
    "hasInquiry": false,
    "hasPraise": true,
    "emojis": ["🧥", "✨", "🍂"],
    "intentKeywords": ["求链接", "哪里买"]
  },
  "pagination": {
    "currentPage": 1,
    "nextPage": 2,
    "itemPosition": 1,
    "target": "OOTD",
    "targetType": "keyword",
    "searchId": "2GWYZH99W1ZX7ZHB78AKZ",
    "resumptionToken": "eyJwYWdlIjoyLCJ0YXJnZXQiOiJPT1REIiwidHlwZSI6ImtleXdvcmQiLCJzZWFyY2hJZCI6IjJHV1laSDk5VzFaWDdaSEI3OEFLWiIsImN1cnNvciI6IiIsInRzIjoxNzg5ODEwOTE3LCJsYXN0SWRzIjpbIjZhNzU2OGNjMDAwMDAwMDAwNTAzMjhkOSJdfQ",
    "hasMore": true
  },
  "scrapedAt": "2026-09-19T13:40:00.000Z"
}
```

---

## 🔄 How Deep Resumption Works

At the conclusion of each scrape, the Actor saves an operational summary to the default Key-Value Store under the key `OUTPUT`.

To continue pagination without scraping duplicates, copy the `resumptionToken` from the `OUTPUT` tab into your next run's input:

```json
{
  "resumptionToken": "REPLACE_WITH_YOUR_RESUMPTION_TOKEN",
  "maxItems": 100
}
```

The Actor will automatically restore the target keyword/channel, jump to the next page, and use its embedded `lastIds` deduplication filter to guarantee **0 duplicate notes across runs**.

---

## ❓ Frequently Asked Questions (FAQ)

### Do I need a Xiaohongshu account or cookies?
**No.** The scraper operates entirely in Zero-Cookie Guest Mode using automated device emulation and recommendation stream harvesting. You do not need an account, phone number, or login cookies.

### Can I download watermark-free MP4 videos and HD photos?
**Yes.** The scraper extracts direct CDN links to raw, uncompressed HD gallery photos and watermark-free MP4 video streams.

### What proxies should I use?
We strongly recommend using **Apify Residential Proxies** for maximum reliability and throughput.

---

## 📞 Support & Custom Scrapers

Need a custom data solution, higher concurrency, or enterprise SLAs?

- **Apify Actor Store:** [Xiaohongshu (RedNote) Scraper](https://apify.com/scraperpro/xiaohongshu-rednote-trend-scraper?fpr=939u3w&fp_sid=gh_xhs)
- **Email:** [radwanfaris13@gmail.com](mailto:radwanfaris13@gmail.com)
- **Author:** ScraperPro

<div align="center">
  <br>
  <a href="https://apify.com/scraperpro/xiaohongshu-rednote-trend-scraper?fpr=939u3w&fp_sid=gh_xhs">
    <img src="https://img.shields.io/badge/Start_Scraping_Now-Apify-28B52A?style=for-the-badge&logo=apify&logoColor=white" height="40" alt="Start Scraping Now">
  </a>
</div>

---

## 🔍 Keywords & Search Tags

`xiaohongshu-scraper` • `xiaohongshu-api` • `rednote-scraper` • `rednote-api` • `little-red-book-scraper` • `小红书爬虫` • `小红书数据采集` • `xiaohongshu-python` • `xhs-scraper` • `scrape-xiaohongshu-without-login` • `xiaohongshu-video-downloader-no-watermark` • `xiaohongshu-buyer-sentiment` • `ecommerce-product-discovery` • `chinese-social-media-data` • `apify-actor` • `kol-influencer-analytics` • `rednote-crawler` • `xiaohongshu-trending-topics`
