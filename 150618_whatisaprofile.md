<!---
tags: phd,social profile,social web,socialwg,identity,privacy,self-representation,indieweb,braindump,soc-inf,study,online profile
-->

# What is a profile?

*..this post is a work in progress.*

Digital personhood is simultaneously becoming more fragmented and more centralised. People are giving more of themselves (consciously and unconsciously) to services which help manage communications and activities, and at the same time spreading themselves across multiple services in order to manage different aspects of themselves. (There's something to say about Goffman here). We perform roles in different social situations, to different audiences, in order to manage people's impressions of us and our place in the world. Interaction on social networks can involve a great deal of performance; there is potential for a high level of control over the version of oneself presented according to what data one makes available to the system, and what activities are explicitly published. However this control is diminished by increasing complexity and opactiy of systems, and users' limited understanding of how their data is propagated and presented to others. The more data given to third parties, the less control individuals have over their own presentation of self, even if (especially when?) the systems in question present the opposite impression (through privacy controls etc).

Since people can't exist on the web directly (yet), a profile is a document which exists on the web on a person's behalf. But what goes into that document, and how it is addressed, created and distributed, varies between social network providers.

Regardless of what the social network provider intends, how individuals choose to use the profile-related tools they are provided with also varies. Some systems impose rules, policies or technical barriers against certain things. People find ways to do 'certain things' anyway. The ways in which people subvert affordances of social systems - and why they do it - might give us some insight into how to improve social systems to better meet people's needs.

Aside: Profiles also exist for products, places, organisations, etc... I'm not ignoring this, but not focussing on it for this post.

## A taxonomy of profiles

To get started, we should observe existing profiles and compare them; try to find commonalities and differences, and eventually start to classify them. Even within networks, people use profiles differently of course, so I'll start by looking at the affordances of some systems with regards to profiles rather than individual instances of profiles for now.

### Existing taxonomies

I didn't find much, but I might have not looked hard enough. A few 'taxonomies' of social networks are on marketing blogs, and are aimed at helping companies leverage their social media presence; high level descriptions of networks focussed around the content people post, mostly, and not hugely useful here.

The [Classification Framework for Social Machines (Shadbolt et al, 2013)](http://sociam.org/www2013/papers/socm2013_submission_9.pdf) considers a broader scope than social networks and classifies systems fairly generally, but includes some useful constructs like roles of participants within a system, level of user autonomy and anonymity and motivations of participants to use a system.

I was pleasantly surprised to find [Taxonomy for Social Network Data Types from the Viewpoint of Privacy and User Control (Richthammer et al, 2013)](http://epub.uni-regensburg.de/28276/1/ARES.pdf) is fairly recent and focussed specifically on social networks. They used a methodology called 'design oriented research' which I haven't looked into yet, but appears to include a magic step between comparing existing taxonomies and deriving their own terms. They classify existing social networks *after* the fact, to evaluate their taxonomy. That aside, great critique of a few existing frameworks that are not sufficient along various dimensions, and they fill in the gaps pretty well (in my humble opinion). This seems like something I can build on by going deeper into the profiles part of things. In particular:

* Semantically specified and semantically unspecified data: the latter (like freeform bio text or posting a photo with no tags) impedes service providers from processing it automatically.
* Mandatory and extended profile data, and to what extent mandatory data can be hidden from public view. Only Facebook and Google+ offer "selective disclosure of attribute values"; on Twitter and LinkedIn something is either public or private only to yourself.
* Disclosed and disseminated data: data explicitly created by a user vs data created about them or in their space by someone else, including how much control a user has over visibility of data created in their space by someone else (like someone else posting on your Facebook wall).

### First pass

I made a list of things I want to find out about how profiles work in different systems that I should be able to figure out from looking:

* **What is displayed** on a profile? (Attributes, activities, other people's content, ...?)
* How are profiles **updated**?
  * via the UI?
  * via the API
* How are people **notified** of profile updates?
  * via the UI?
  * via the API
* What granluarity of **access control** exists for parts of a profile?
* How are different people's profiles **connected** together (within and between systems)?
* How **portable** is a profile? (Can it be exported? Can it be imported to a different system?)
* What **restrictions** are placed on the creation of profiles?

And other things that might require a bit more digging or analysis:

* How does a site appear to **model** a person and their relationship to profile documents and other activities or content objects in the system?
* **What** is a profile for? (To what end was it created? What results from its existence?)
* **Who** is a profile for? (You, others, a service, ...?)

And a list of services/ways-of-representing-people-online, of varying degrees of specialisation, that I know reasonably well which would be good to compare:

* FOAF
* Indieweb/Microformats
* Twitter
* Tumblr
* Pump.io
* YouTube
* CouchSurfing
* Facebook
* Quora
* OkCupid
* StackOverflow
* LinkedIn
* PeoplePerHour
* Academia.edu
* AirBnB
* Friendica

So I'll work my way through a few, refine the questions based on what I observe, and repeat. I'll see if this results in some kind of clustering or patterns that might bring us closer to an answer to 'what is a profile?'.

## Analysis

Ongoing.

>> Link to results.

## The many dimensions of lying online

People lie in online profiles for all kinds of reasons:

* to manage what people think of them.
* to protect themselves.
* to experiment.
* to mitigate against mass surveillence.
* because they don't understand why a system needs so much information about them in the first place.
* [...and others](http://rhiaro.co.uk/pub?p=websci15) (van Kleek et al, 2015).

People also break the rules: multiple accounts, fake names, etc.

And people 'misuse' mandatory content fields to force a system into meeting their needs (eg. using YouTube video description boxes for profile links and attribution).

These are all techniques for managing nuanced online self-representation. But people are fighting the systems to do this, not working with them. **We can learn from this.**

## Owning my profile data

Of work I've seen to do with Personal Data Stores so far [citation needed] there's little taking into account of faceted identity or different audiences for versions of oneself. There's an assumption of a single, consistent version of a person and a set of facts to describe them. PDSs in 'serious' domains like healthcare tend to also require a link to a 'real world' person. This doesn't resemble how people currently manage their data on the social web, and nor is it strictly necessary for services to function.

I'm gradually migrating my social web activities from the different services they're spread out over onto my own site. This is straightforward for generic things like twitter where I don't use a pseudonym or have any particularly tailored profile information or try in any way to curate my audience. It gets harder as I branch out into more specialised sites. How do I organise my content so people only see what they're interested in? (Presumably only my three friends on RunKeeper care about my runs so I don't need to subject everyone to them. Pretty sure *nobody* cares about recommendations on LinkedIn, but people insist on sending them so how best to pull them through to my site?). How do I organise my content so only the people I want to see certain things get to see it (I don't want to mix OkCupid and CouchSurfing)? Do I need new domains for my semi-anonymous (Quora) or anonymous (secret Tumblr anyone?) activities? What do I do with shared accounts (organisational Twitters, shared joke Tumblrs) especially where the content posted might be explicitly attributed to me. Some of the content in these profiles overlaps, as do some of the audiences. But there isn't a one-to-one mapping between most of them. My profiles are defined not only by the data about me they contain, but by others in the network, the social norms of the platform and related content.  I haven't figured any of this out yet, and one of my big questions is how I can be sufficiently methodological about this to make the process useful for helping to answer 'what is a profile?'. I suspect I'm going to do a lot of accidental oversharing in the process.

There is contention between controlling all of my data myself, and adequately managing my identity across social contexts. I want to own my data, so I need tools to resolve this.

## Understanding current practices of self-representation online for improved privacy and greater online freedom

I hear "people don't want to manage their online personas themselves" a lot, but people are *already doing it* despite the inadequate tooling. If we can understand the nature of online profiles, and examine how people are getting by at present, we can make things easier for them (and ourselves, since we're all participating in this). Then we can spend less time fiddling with Facebook privacy settings and wondering if we accidentally shared that inappropriate picture with our boss - or endlessly reporting Twitter abuse - and more time linking ideas, expressing ourselves and using the web to its full potential.