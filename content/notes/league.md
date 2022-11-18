---
title: "League Versioning and Pipelines"
enableFooter: true
---

I have 14gigs of data from all regions. It's public in [here](https://www.kaggle.com/datasets/d4sein/league-of-legends-patch-109)
I'm trying to parse this big file into smaller region-partitioned parquet data. Then I can train a ml model to predict which team would win? I would build pipelines and make process easy. After those stuff, I would try model for another data and data-drift will trigger for model training.