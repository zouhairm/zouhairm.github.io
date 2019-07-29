---
layout: proj
author: zouhair
image: projects/writerblock/landing.png
imageLink: https://zouhairm.github.io/nomadsVue
tags: [webdev, datavisualization, graphs, machinelearning]
title: Visualizing Traveller's stories with Doc2Vec and WebGL graph renderer
venue: Sri Lanka, 2019
description: An Interactive Data Visualization of Travelers' stories [writing still in progress]
  
links:
  - title: Website Link
    url: https://zouhairm.github.io/nomadsVue
  - title: Nomad Travel Stories
    url: https://www.worldnomads.com/create/scholarships/writing/
  - title: VivaGraphJS
    url: https://github.com/anvaka/VivaGraphJS

featured: true
video: true
---

# The Why 

Although I occasionally find the time to write down musings about life and the universe, they rarely are the kind of stuff that'd captivate your imagination.
In contrast, my wife Olivia is a talented story-teller and writer. One of her goals during our sabbatical was to work on a short story (if you know her, ask her to send you the draft!). Naturally she was the trip's official travel writer and sent out a few diary-emails to friends and family, who without a fail wrote back everytime with great praise.

So when I found out that our travel insurance provider - WorldNomads - was sponsoring a travel writing contest, I convinced her to submit an excerpt. At first, I was certain that she'd win; however when we realized that there were over 10,000 submissions, it became obvious that the odds were not favorable.

Sure enough, the results came out, and she wasn't event shortlisted. While disappointing, the whole thing got me thinking about how many other awesome stories all these people have shared, and how few of them would be read. And I had all these different questions and musings running through my head:
* How did the judges go through so many stories and rate them?
* Wouldn't it be great if they made those ratings available to see how she ranked?
* Unfortunately they didn't -  so how do I know how good or unique her story was?
* Aside from the 3 winners and 10 shortlists, how can I find other great stories?
* Given all of the data, would I be able to have a computer generate similar stories?

With this in mind, I set out to try to do something intersting with this dataset. I knew that it would be a challenge because aside from that Naive Bayes Spam Filter homework every CS student implements at some point, I don't have any experience with natural language processing (NLP). Still, I figured it would be a good opportunity to learn how machine learning tools can be used with documents. This also coincided with our last week in Sri Lanka - exactly when the prospect to returning to real life started materializing, and I was feeling the urge to do something "fun" before getting back to a full-time job (little did I know it'd end up taking another 2 countries and 4 months before I'd finally start working again)


![Typer Writer](/assets/img/projects/writerblock/Banner-typewriter.jpg)

# The What

I did some research on what tools I could use to extract interesting relations between stories. I found what seems to be an increasingly popular technique (a neural-network approach known as Doc2Vec) which converts each document in a collection into a high-dimensional vector, therefore making it possible to compare the stories just by computing the distance between them. 

But before digging into the technical details I think it's more worthwhile and fun to talk about how utterly cool the results are (it's great writing on a blog - I wouldn't be able to say this on a peer-reviewed paper! You can scroll down to [The How](#the-how) section to read about the scraper, the model building/tuning, and the designing/coding of the visualization website).

Olivia's story was titled **Calling in for Galaxy, Galaxy, over.** That was the transmission we'd hear on our radio when our friends wanted us to come over for dinner or needed to borrow the spare dhingy motor. It is set on a sailboat off the coast of Zanzibar - an idylic archipelago with deserted beaches and welcoming people. The intro went something like this: 

> We spent Christmas aboard Galaxy with our makeshift family, a collection of humans as joyfully mismatched as the cutlery we used to dig into our shared meal. A Swiss captain who travels the world before a degenerative eye disease takes it away. A Canadian couple mourning a baby. South African parents who found space for exploration within their empty nest. Molly the hound. And Zouhair and me. I wonder how others would describe us [...]

Out of the 10,000 entries, the 2nd most similar story to Olivia's was Justin's **The 12 Day Changeover** whose intro quickly draws you in:
> We travel by battered boat, seaweed-stained, but its tiller still works, its radio, its hand-cranked orange juicer. A fresh coat of pistachio. There is a crew of three: a captain, a navigator, a cook. One of them is a ghost; they know one of them is a ghost, hear the rattling chains every night, but the other two haven't figured out which of them it is.

This alone feels like a mini-success: the model identified another story set on a boat, with a captain and some companions, and (if you squint) a similar writing style! Let's now look at the story that is most similar to Olivia's. According to the model, that would be Kirstin's **Take a Break**. At first glance, this tale of lost Australians in Mexico doesn't seem that similar. It could be that they are related because Kirstin talks about arriving at a beach and finding helpful people, and Olivia describes the curiosity of the children and warm welcome of the people when we land on Pemba's beaches? But I'd like to believe that the strong similarity comes from the stories' concluding paragraphs. Here is Kirstin's:

>  Every time we offer our assistance in the kitchen, Wiley pulls out his favourite catchphrase, “Take a break”. Still a child at heart, he’s in awe of our youthful moxie to leave everything behind to travel and his eyes glaze over as he dreams of a past in which he wishes he had done the same. 
We still can’t quite believe the generosity of Helen and Wiley to adopt us strays. Just two months later we learn that Wiley has suffered a stroke. It is one of those sobering, albeit cliché ‘life is too short, do it while you’re young’ moments. <br> And so we took a break.

And here is Olivia's:
> For all the wonder, there’s been equal hardship. The romantic vision paints this life, who knows no master but the weather, as the pinnacle of freedom. But I’ve felt stranded on this boat. Galaxy is urging me to sit still although the b\*tch gets to rock constantly, and I resent her for it. [...]
> Galaxy couldn’t care less about what I want. Maybe it’s because she’s been focused on giving me what I need instead. Time to stop and digest momentous life changes undertaken all at once. A chance to face my fears and find my edges. A view of the horizon, and what might lay right behind it. 

And there it is - both have endings with mixed emotions. Despite the sudden death in one and the hardship in the other, both speak of the importance of taking time - to travel and to digest life.

...

Ok, you might think I'm blowing some hot air here, and that would be a fair criticism. It's hard to tell though, as this illustrates one of the difficulties of neural-networks and other ML techniques: interpertability. The model says that based on the stories it was trained on, these two are similar, but it's hard to know why without digging into its details.
For example, the vocabulary it has encountered on is important, and these stories are only similar within the context of the "corpus" it has seen so far. To get an intuition for that, checkout this [(king - man) + woman = queen](https://p.migdal.pl/2017/01/06/king-man-woman-queen-why.html){:target="&#95;blank"} post which gives an analysis for Word2Vec, the basis behind Doc2Vec.
Not being an NLP expert, I am not sure if there are similar ways to analyse the output of Doc2Vec to understand *why* two documents are similar. If you are one, hit me up :)


<!-- <video id="scenario-1" class="video-js vjs-default-skin vjs-big-play-centered" controls
 preload="auto" width="640" height="480" data-setup='{}'> -->
<!--  <video  class="video-js autoplay loop muted playsinline">
  <source src="/assets/img/projects/writerblock/cluster.mp4" type='video/mp4'>
</video> -->


{:refdef: style="text-align: center;"}
![Clusters](/assets/img/projects/writerblock/cluster_stars.jpg)
{: refdef}

## Visualization and Layouts

So far I've focused on Olivia's story, but I've spent hours reading various other ones for fun. 
I was soon finding myself doing a lot of this story comparison by hand: randomly selecting one from the corpus, and running code to display the most similar story to it. I wanted a more streamlined alternative that I imagined could be a great way to share all of these travelers' stories with a wider audience.

At first I thought that maybe using the computed distances to generate a [Dendrogram](https://en.wikipedia.org/wiki/Dendrogram){:target="&#95;blank"} would expose interesting structures in the stories. However, it turned out that displaying a dendrogram with so
many nodes is not very informative nor easy to use. Instead, I decided it'd be easier to start by laying out the stories geographically on a map. 

#### Geographical Clusters

{:refdef: style="text-align: center;"}
![Clusters](/assets/img/projects/writerblock/landing.png)
{: refdef}

Although the easiest to understand conceptually, it took the longest to get this view working because it was the first. I needed to find the right framework to use. I initially gravitated to using Plotly/Dash given my recent experience with it from the [DivetheData](https://www.divethedata.com){:target="&#95;blank"} project. But after a few false starts, I eventually settled on [VivaGraphJS](https://github.com/anvaka/VivaGraphJS){:target="&#95;blank"} - hailed as the fastest graph visualization framework; and it lived up to its promise!

I chose to center the nodes at the locations were the stories were written, and to color them based on the continent of origin of the author. Since the metadata lacks the exact geo location details, I got creative with the positioning and made co-located stories build-up into a spiral. The resulting interface was colorful, fast, and smooth; and it quickly exposed some interesting insights:

* *Populated countries tend to have a large proportion of "local" travellers*. The majority of the dots in the US are green (stories written by North-American travellers), likewise with India and Indonesia with yellow dots (stories by Asian travellers), Nigeria and South Africa with orange dots (stories by African travellers); and Brazil with purple dots (stories by South Americans). This is in contrast to popular tourist destinations which have more of a mix: The UK, France, Spain, Portugal, Italy, Morocco, Turkey, Thailand, Vietnam, Nepal, and Japan all have a mix of stories from writers all over the world. 

* *Stories are rarely connected by their location*. Except for India, if you quickly mouse-over stories, you will see that the other ones they're connected to are often not set in the same country. I specifically avoided using any of the metadata (author country, submission category, etc.) in the model as I wanted only the story text to influence the relations.

* *The location of many stories are mis-labeled*. If you take the time to read some of the entries, you will quickly realize that writers sometimes mistakenly put their country of origin as the location.


### Similarity Constellations

{:refdef: style="text-align: center;"}
![Clusters](/assets/img/projects/writerblock/cluster.gif)
{: refdef}

Aside from a constant layout, VivaGraphJS implements [Force Directed Graph Drawing](https://en.wikipedia.org/wiki/Force-directed_graph_drawing){:target="&#95;blank"}, a super nifty way to layout graphs. It's basically an n-body simulation where the links between nodes act as springs pulling related nodes together, therefore doubling as a clustering algorithm.

I initially attempted to do this with all of the connections, but there are too many and the result is a hot mess. However, when the links are restricted to the Most-Similar connections only, the resulting graph is interesting.
I like to think of it as a collection of constellations, each with a common thread, making it easier to explore stories by "topics". Unfortunately, there is no elegant way to label the topics, as discussed in this [Automatic Topic Clustering Using Doc2Vec](https://towardsdatascience.com/automatic-topic-clustering-using-doc2vec-e1cea88449c){:target="&#95;blank"} which ends up using the most frequent occuring words in news articles titles.

Nonetheless, as one explores these constellations, it is interesting how clustered stories will often share similar settings (hiking, ocean, city/urban, airport, train, etc.). That is not surprising as even a rudimentary "bag of words" approach should be able to cluster them together. However, what's ice-cold is when the similarities appear to be driven by the story's structure or sentiment: being lost at the beginning and getting help from a local, trouble with immigration officers that eventually gets resolved, etc. Here are some specific ones I think are worthwhile to highlight.

* Challenges arising from a clash of Nationality, identity, and/or religion.
  * **Hola Libertat!** In this story Tsz Kwan Lam (Hong Kong) finds parallels between the Catalanians' fight for preseving their distinct culture within Spain to his Hongkongese compatriotes fight for political freedom from China. 
  * **My Dearly Beloved Br-EX-it London** Yelena Novikova (Kazakhstan) describes how a "Brexit tantrum" makes its beloved host country "sound like a racially-charged bus fight" and blames it for almost being evicted from her rental.
  * **The Smile of Homeland**  Julya Fransisca relates the difficulties of growing ethnically Chinese in Indonesia. 
  * **Lebanese Luster** Richard Chemaly (South Africa) ponders how the Meronites' fight for religious freedom has given rise to a unique beauty to Lebanon's mountains.

* Overcoming Fears (of travelling alone, flying, sky-diving, jumping off-boats ...) - This is one of the biggest constellations, and is self-explanatory Here is a small sample:
  * **Fear is temporary, regret is forever** This story by Sarah Corrigan (USA) about her study abroad in Australia is at the center of one of the biggest clusters. It contains almost all the elements found in the other ones: travelling alone, being held back by fear or social pressures, queasy feelings about/during flights, becoming more adventurous, and jumping! 
  * **Riding Solo** Michael Houston (UK) recounts overcoming his fear of travelling alone to Berlin.
  * **Introducing Kay Cabernet** Kyndra Rothermel (USA) describes how she overcame difficulties of being an expat and eventually became an adrenaline junkie going paragliding and cage diving with sharks.

* This is a bit of a complicated cluster to interpret, but I think it is basically a mix of buying tickets, not speaking the local language, getting lost, and getting help from locals:
  * **My Christmas Serendipity** In an attempt to escape tourist-laden Muich, Zhanna Ganeva (Bulgaria) unexpectedly finds herself in Austria after buying a ticket to Salzburg
  * **Russian glasses** Giovanni D'Amico (Italy) struggles with Cyrillic alphabet but fortunately gets help from Masha with buying a train ticket
  * **The door who gave me a Finish speaker friend** Nicole Da Silva Fleck (Brazil) finds out from the Finnish speaking airline staff that her luggage was lost.

Here are a couple of other interesting clusters, but without the additional examples of the composing stories:

* Travel minutes: stories written in a detailed "hour by hour, day by day" chronological order
* Brochures for island beaches: These stories almost read like advertisments describing the scenic beauty of the beaches on iconic islands such as Goa, Boracay, Borneo, Maldives, and Phuket.
* Jungles and their noises: a tiny cluster of stories about the cacophony one finds in forests and jungles.
* Trekking up a mountain


### Di-Similarity Nuclei

It is normal to think of clustering stories based on their 
The natural way 





I experimented with displaying the stories in an Ipython Notebook, but with 10,000+ nodes that a graph on a geographical map could work. In [The How](#the-how) section I discuss the different packages I considered, and it took a lot of work (surprisingly much more than downloading the data and training the model) to get it to work, but I am quite happy with the result.


**Finding Mongolia's Silent Secret** by Bea Gilbert (UK) showcases how this approach can bubble-up some fascinating stories. Bea's story comes up as the least similar story to over 20 other stories, and a quick glance at her introduction paragraph makes it obvious that her writing style (and choice of words) makes her story one of a kind:

> A breadcrumb trail of skulls studs the forest as we labour North. Each beckons a reliving of the previous evening, where a goat hangs dead in the dark. Pearly skin is tethered taut to the swollen canopy of a ger, scuffed hooves still outstretched, stubbed into the gravel



more than 20 


 United Kingdom


seeing how similar stories will often share similar settings (hiking, ocean, city/urban, airport, train, etc.). It's not surprising that would be the case as even a rudimentary "bag of words" approach should be able to cluster them together. However, what's ice-cold is when the similarities appear to be driven by the story's structure: being lost at the beginning and getting help from a local, trouble with immigration officers that eventually gets resolved, etc. Here are some specific ones I thought were interesting:

* Breakup stories
  * Yelena breaking up with London in **My Dearly Beloved Br-EX-it London** 
  * Iember travelling in Europe after his breakup in **Soul Searching: An Intrinsic and Extrinsic Journey**

* Complicated relationship with home countries:

* Mountains: 


 wo

Stories aside,


# The Next?

Time allowing, there are a couple of extra things I'd like to do with this project.

I am starting a new job so we will see how much free time I have to work on it, but if someone wants to get their hands dirty with it, let me know! All of the code can be found on [github](https://github.com/zouhairm/nomadsVue){:target="&#95;blank"} so you can fork it or submit pull-requests!

* Implement story generation 
* The interface is still buggy - Although I spent a lot of time polishing it, there are a lot of corner cases that can throw the interface into weird behaviors. Fix bugs in the interface: 


# The How

When I first started working on this project, I figured that I would be doing most of it in python. After all, that's the de-facto scripting language nowadays and the increasing number of ML tools makes it a natural choice. Sure enough, I wrote the webscraper using `BeautifulSoup` which made downloading the stories and storing them with the relevant meta-data straightforward. It actually ended up taking longer to download the stories than to write the script, but that's mostly because Sri Lanka doesn't have the fastest of broadband connections.

Once the stories were stored into yaml files, I spent some time choosing what I was going to do with them. There is a lot of NLP packages out there, but Word2Vec and Doc2Vec repeatedly came up as being straightforward to understand and implement and apparently yielded good results. I ended up following tutorials for [GenSim](https://radimrehurek.com/gensim/models/doc2vec.html){:target="&#95;blank"}, and sure enough, within a day of some python scripting and jupyter notebook experimenting, I had the first results where I could cluster stories

I didn't use the categories ... 


This is unsupervised. There is a lot of other things that could be done with some supervision by labeling the stories


Mapbox for the map background. I tried using a static background, but getting the zoom/pan to work smoothly and seamlessly was challenging. Fortunately, with mapbox 


