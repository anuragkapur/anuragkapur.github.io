---
layout: post
title:  "ETL is dead; Long live streams"
date:   2017-06-08 18:00:00 +0000   
categories: highlight engineering
tags: engineering
teaser: Looking back into traditional ETL architecture and how Kafka based stream processing makes things better 
img-url: /assets/blog/training/etl-is-dead/trie-vs-hast-table.png
---

My notes from the webinar: [ETL is dead; Long live streams](https://vimeo.com/220846693/305dfdb663?mkt_tok=eyJpIjoiTXpVNFlUVmpNVEkzT0RsayIsInQiOiJmbCthcWZFN05jMWtuMkxMcGprd2xZT3dXZDlFT1B4anplMk9BQlJNSE9BR0I3S1hBZkR1NmRCUVNFdnJsNHdWNWZ1UHZOUnVybHlmWkNzSzN6WnlyXC9VRmlIWWxNRFErbW1oTHVXZHdUazhacnZjNHdSXC85QnNWU1hRT0w5NGJUIn0%3D)

* Traditional model involved: Operational DB, data warehouse and data flowing from operational to the warehouse no
more than a few times a day
* Challenges of traditional approach
  - Single server DBs being replaced by distributed data platforms
  - More data sources, ex: logs, sensors, metrics, not just relational data
  - Faster data processing is needed
* Vision architecture:
![](/assets/blog/training/etl-is-dead/img1.png)
* Traditional ETL drawbacks
  - Need to a global schema
  - Data cleansing and curation is manual and error-prone
  - Operationally expensive
  - Batch processing paradigm
* Early take on real-tome ETL = Enterprise Application Integration (EAI), involved
  - ESBs
  - MQs
  - but they didn't scale
  - ![](/assets/blog/training/etl-is-dead/img2.png)
* Event centric thinking
![](/assets/blog/training/etl-is-dead/img3.png)
![](/assets/blog/training/etl-is-dead/img4.png)
  - Decoupling via a pub-sub model, brings isolation across publishers and subscribers
  - Forward compatible data architecture ability to add mode applications that need to process the same data, but
    differently
* Modern streaming approach
![](/assets/blog/training/etl-is-dead/img5.png)
* Apache Kafka
  - Open source distributed streaming platform
  - Log abstraction - append only, multi-offset per reader/subscriber
  - ![](/assets/blog/training/etl-is-dead/img6.png)
  - Messaging APIs
  - Connect APIs: E & L of ETL
    * Sources and Sink
    * ![](/assets/blog/training/etl-is-dead/img7.png)
  - Streams API: T of ETL
    * A java library
    * ![](/assets/blog/training/etl-is-dead/img8.png)
    

  
