---
title: "Ian's podcast about League MLOps"
enableFooter: true
enableToC: false

---
* They are using some recsys for riot games (e.g collaborative filtering)

* They uses binary format for making fast compile time.

* Riot story always continuous, so creating a model for writing stories in Demacian or Noxus would be great! **(Cool product idea!)**

- Java -> C++ -> Kafka db scrapes, data ingestion scheme, and everything logged.

After some process, output data is Json data as in my [league project](/notes/league). The process would be in Player level or Game Level. After the transformations of data, it sends Hive Data Warehouse, and then feature engineering/computation happens and new output are whether in Hive or S3 bucket. 

Also, they have Feature Store => riotsdb implemented on S3 feature store. I couldn't find a news about it, so it would be my imagination 😂

* Predicting which lane player go by recent activities? **(another project idea!)** They uses Decision Trees. 

Game personalization is **hard** for video games. Because you have to embed model into the game for speed, but even with Jax it's so hard. Updating leafs and parameters within the game etc, also there's another problem with security, needs a lot of extra steps (TCP connection, UDP only)

#### Technical Reasons of why ml is hard in video games:
* Rendering is hard when doing massive math computations well playing a game at the same time
* Adding a network kind of security stuff is takes a lot of time. (Safely and Ethically!)
* League is an older game and there is a lot of historical inertia and going against some of these changes. 

> How you can get into 10+ years of C++ code with 3 differents implementations and make inference? It's pretty hard... -Ian

>* How many ML Engineers writes C++?
>* How many ML Engineers have interest in game engines? 
	"not just writing C++, but how Riot writes C++ in their codebase" -Skylar

> Niche subjects that tied together along with the fact that this code base is nine or ten years old it makes it really difficult to go in there and make changes. -Ian

In the data field, the codes that you write for machine learning doesn't matter, the model that you've shipped has high level of accuracy and is delivering a lot of player matter. In the software engineering reliability and those clean code stuff really matters. 

#### MLOps becoming more of SE trade these days, some reflections here
- Write unit tests
- Use observability, monitoring (evidently ai is a tool for that -Mert)
- Code Quality matters! (Lazslo build a CQ4DS community check it out!)
	- A separation between essentially code analysis vs. code for production
- Data Science codes would suck in production, because there are not just enough software engineers people working in the data space!

* There are two different of data teams in the world
	* 1st one taking code quality seriously 
	* 2nd one is writing codes without code quality
	* At least do base level of quality, say "look, don't submit it, let's spend more time on it."
* About code quality, the approach should be like below;
	* Severly reduce the amount of notebooks.
	* Notebooks are fantastic tool for analysis but when it comes to hit production, unfortunately notebooks doesn't. -> Instead build a python package. 
