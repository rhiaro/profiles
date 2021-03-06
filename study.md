

1. What does a profile contain?

**FOAF**: Attributes (fixed in FOAF but extensible with other vocabs), connections, links to authored content (maybe).

**Indieweb**: Attributes (fixed as per microformats2 but extensible), authored content.

**Twitter**: Attributes (fixed set), connections (subset), authored content, activities within the network (heavily curated).

**Tumblr**: Content; original posts and reposts. Attributes: username, blog title, blog description. (Separate page for likes which is optionally public). No stats by default.

**Pump.io**: Attributes (name, hometown, bio, avatar) and content (major in main feed) and activities (minor down the side) (ActivityStreams)

**YouTube**: channel art, display picture, content (videos), liked videos, created playlists, curated connections, featured content. Links to: attributes (description, links, country); stats (subs, views, joined); discussion (comments on your content).

**CouchSurfing**: Attributes (name, age, location, occupation, education, hometown, languages. member since, photo, availability), free text (about me, interests, music movies & books, one amazing thing done, teach learn share, what I can share, countries visited, countries lived in), % complete profile (pushes to connect to fb), verified; links to My Home, Photos, References, Friends.

**Facebook**: Attributes (literally everything you can think of, free text and enum and select from content created by others eg. pages). Content (status updates, notes, photos, videos, other media). Stats (friends, following, likes, groups). Activities (interactions with other people and content, stuff cross posted from linked apps and sites).

**Quora**: Attributes (name, photo, bio, description, social media links, location, knows about); Activity (questions, answers, votes, comments, edits, posts); stats (# ^, # followers, # following, highlights (badges basically), views on answers)

**Okcupid**: Attributes (photo, age, location, gender, Self-summary, What I'm doing with my life, I'm really good at, Favorite books, movies, shows, music and food; The six things I could never do without; The first thing people usually notice about me; I spend a lot of time thinking about; On a typical Friday night I am; You should message me if; I'm looking for [Men/Women/Everyone], ages between, near me?, must be single?, for [new friends / long-term dating / short-term dating / casual sex]; orientation; ethnicity; status; relationship type; height; body type; diet; smoking; drinking; drugs; religion; sign; education; offspring; pets; languages spoken). Stats (personality traits compared to average; % match with person reading profile). Content (photos, questions and answers).

**StackOverflow**: Attributes (name, role, company, about me, location, links and social media); stats (answers, questions, people reached, member for, profile views, last seen, visits, badges, accept rate, vote counts); content (posts q&q, tags); links to activity, reputation, everything done.

**LinkedIn**: Attributes (name, photo, location, hometown, experience, education, summary, languages, voluntary experience, organisations, honors and awards, test scores, courses, patents, projects, publications, certifications, interests, personal details, contact information, skills, background photo); Content (posts, media) (not on profile: likes, status updates); Stats (groups, following, rank, views); from others (endorsements).

**PeoplePerHour**: Attributes (name, job title, cover image, profile picture, per hour rate, phone, about you, skills (enum), location, remote only or onsite possible, miles willing to travel. Content (intro video; portfolio files). Stats (# reviews, online presence, rating, projects completed, buyers worked with, last project). From others (reviews, endorsements).

**ResearchGate**: Attributes (name, institution, discipline and subject(s), skills, photo, email, topics, degree, position, awards and achievements, about, advisors, scientific societies, ORCHID, journal referree, interests. Content (publications, many types). Stats (# publications, reads, citations, impact points, top co-authors, following, followers).

**AirBnB**: Attributes (name, location, ID type, school, languages, photo, about; private by default: email, phone, gender, date of birth). Stats: member since, # reviews, (un)verified). Others (reviews). Content ('symbol', profile video 30 secs).

**Friendica**: Attributes (photo, relationship status, sexual preference, display name, name, gender, birthday, homepage, birthday, address, location, public keywords, bio (free text), a bunch of other free text fields for interests etc). Content (status, photos, videos, personal notes). Activity (shares, likes, dislikes, stars, events, rsvps). Stats (member since). Others (messages).

**Zooniverse**: Attributes (name, display name, photo, header image); Activities (favourites, contributions); Content (comments, collections).

**runkeeper**: Attributes (name, photo, location, motivation, gender, birthday, weight, body measurements, nutrition, certain health conditions); Activities (recent PRs, summaries, exercise tracked); Stats (miles, # activities, calories, # friends, active since)

**github**: Attributes (name, location, email, website, bio, photo, company, available for hire?); Activity (code contributions, issues, comments); stats (joined, followers, starred, following, organisation membership)

2. How are profiles updated?

**FOAF**: not spec'd (likely hand editing or through a client).

**Indieweb**: not spec'd (likely editing static HTML).

**Twitter**: Web form / client UI.

API:

WAIT THESE ARE ALL GET. No POST for update o.O

* `/user/info`: following, default_post_format, name, likes, blogs [name, url, title, primary (bool), followers, tweet (bool), facebook (bool), type (pub/priv)]
* `/user/dashboard` (which is feed of what they see that they're subscribed to etc)
* `/user/likes`, `/user/following`

**Tumblr**: Web form, mixed in with blog appearance/settings.

**Pump.io**: Web form / client UI

API:

```
To create a new user, POST a user representation (see below) to the list.

The JSON object representing the user has the following properties:

* nickname: The user's nickname. 1-64 characters, including only ASCII capital and lowercase letters and numbers as well as "-", ".", and "_". The nickname is immutable and unique per server; it can't be changed.
* password: The plain-text password. This isn't returned when you GET the user object, but you have to provide it when registering or updating the user.
* profile: a "person" object. This is created automatically when you create a new user; don't try to add it yourself. Don't update this directly; update the person through its object endpoint.
```

**YouTube**: Web form(s) / client UI

**CouchSurfing**: Web form

**Facebook**: Various web forms, some inline.

```
You can update a User by making a POST request to /{user_id}.

id
firstname
lastname
label_cohort
```

Also various endpoints for types of content that might appear on profiles.

**Quora**: Web form, built into profile view.

**Okcupid**: Web forms, some inline, some separate.

**StackOverflow**: Web form

**LinkedIn**: Web form built into profile view.

**PeoplePerHour**: Web form

**ResearchGate**: Web form built into profile view.

**AirBnB**: Web form.

**Friendica**: Web form (API for profile updates not implemented)

**Zooniverse**: Web form.

API: The currently logged in User may edit their record by sending a partial representation of the resource including their changes. A User cannot edit linked resources:

```
PUT https://panoptes-staging.zooniverse.org/api/users/{id}

Accept:application/vnd.api+json; version=1
Content-Type:application/json

{
  "users": {
    "credited_name": "Dr. Stuart Lynn, DDS"
  }
}
```

**runkeeper**: Web form. API:

```
PUT /profile HTTP/1.1
Host: api.runkeeper.com
Authorization: Bearer xxxxxxxxxxxxxxxx
Content-Type: application/vnd.com.runkeeper.Profile+json

{
"athlete_type": "Ultra Marathoner"
}
```

**github**: Web form. `PATCH /user`: name, email, blog, company, location, hireable, bio

3. How are people notified of profile updates?

**FOAF**: not spec'd

**Indieweb**: not spec'd

**Twitter**: None.

**Tumblr**: None.

**Pump.io**: minor 'update' activity

**YouTube**: None.

**CouchSurfing**: None.

**Facebook**: Some (most) attributes in timeline; particularly profile pics, cover photos, relationship status (except when option not to publish is chosen, per thing). When you update attributes it asks if you want them to be a story. Some things as life events.

**Quora**: None.

**Okcupid**: Yes, in your activity stream (people wh you looked at or in any way interacted with or who okc just decided to show you).

**StackOverflow**: None.

**LinkedIn**: If enabled by subject.

**PeoplePerHour**: None.

**ResearchGate**: None.

**AirBnB**: None.

**Friendica**: Profile pic updates.

**Zooniverse**: None.

**runkeeper**: None.

**github**: None.

4. Access control?

**FOAF**: not spec'd (WebID+TLS/WebAccessControl for protecting whole documents not individual attributes).

**Indieweb**: not spec'd

**Twitter**: All or nothing for content. A blocked user can still see some attributes (avatar, banner, name). Protected accounts show all profile data but not content or followers/ing

**Tumblr**: "a primary blog is public facing", secondary blogs can be password protected. Per-blog basis.

No automatic links between primary and secondary blogs, and no way to tell if a blog is primary or secondary, or who which user owns a secondary blog (even from API without trial and error).

You can block users: they can't follow, send fan mails or asks, see your posts in their dashboard, like, reblog or reply to your posts, see you in search results.

Can grant write access and transfer admin between users for secondary blogs.

**Pump.io**: Individual resources can be addressed to groups or users, but profile attributes are all public (but none required). No anonymous activities. No way to invisibly do minor activities.

**YouTube**: Pretty granular. pub/priv: liked videos, saved playlists, subscriptions; subscribers. exist or not: name, country, keywords. Appear as a recommended channel on/off.

**CouchSurfing**: Most things optional. Options: First or full name; restrict to log in members.

**Facebook**: Can restrict access to individual attributes on profile. Also per-post. Can set defaults to include or exclude people/groups/public/networks. Super complex. Can restrict findability of profile. Can set commeting access on public posts and profile info separately (ie. read and write acl are separate).

**Quora**: Online presence on/off. Nothing for profile attributes. Can choose to ask/answer as Anonymous, but still logged in.

**Okcupid**: Requires okc login on/off. Nothing required.

**StackOverflow**: Most fields optional, not granular visibility.

**LinkedIn**: Some individual attributes visibility: My Connections / My Network / Everyone. Public profile visible to: No-one / Everyone with on/off for (Basics, Picture, Headline, Websites, Summary, Skills, Organisations, Groups). Connections: Connections / Only You. Public posts: Everyone / Connections. Activity feed: Everyone / Network / Connections / Only You.

**PeoplePerHour**: Show hourlies on/off. Index by search engines on/off.

**ResearchGate**: Research data: everyone / mutual followers / researchgate members. If you've read other peoples' on/off. Fixed on/off settings for some things: public profile, photo, questions and answers.

**AirBnB**: Some things are private by default. Social connections to share activity on fb only with other airbnb users, and suck some data through from fb. Hosts can require certain profile attributes are filled in.

**Friendica**: Tags have separate fields for public/private. Friends/contacts visibility on/off. Everything optional. "This is your public profile. It may be visible to anybody using the internet."

**Zooniverse**: All optional.

**runkeeper**: 'Sharing' Everyone/Friends/Just Me, profile things in groups of different levels of granularity (body measurements, weight, diabetes, nutrition, sleep, activities). Anything not in this list is an optional thing to fill in I guess, ie no way to say 'name' is friends only.

**github**: Most optional, can choose to keep email private.

5. Connections?

**FOAF**: `knows` - one way relationship, deliberately vague.

**Indieweb**: Under debate, some people use XFN (eg. `rel=following`)

**Twitter**: One directional; notifications sometimes sent to your followers when you follow someone, especially if others in your network also do; follows (some? all? curated how?) appear in your timeline; no notifications of unfollows; configurable notification when someone follows you.

**Tumblr**: `Follow` a blog. (Not a user).

**Pump.io**: `Follow` a user. Minor activity and notification when someone follows you. Added to 'follows' collection (public). One way.

**YouTube**: `Subscribe` to a channel, one way.

**CouchSurfing**: Friends - specify hosted/surft/traveled/never met, and closeness. Couch request/offer (but this doesn't create a persistant connection). References.

**Facebook**: Friends - mutual, accept/reject request. You can choose to let anyone 'follow' your public posts (or not). You can follow pages. Following is one way.

**Quora**: follow a user (one way)

**Okcupid**: Like/bookmark (same thing, interchangeable language). Only revealed if mutual.

**StackOverflow**: none? RSS feeds for user activity..

**LinkedIn**: Follow (one way) someone if they allow. 2 way 'Connect' can require reason or input contact details as proof.

**PeoplePerHour**: Add user to favourites.

**ResearchGate**: Follow (one way).

**AirBnB**: n/a (only references, nothing persistant)

**Friendica**: Follow request. Reciever gets to accept as one way (fan/admirer; they read you) or two way (friend; you also see updates from them).

**Zooniverse**: n/a

**runkeeper**: 2 way friendship (request-accept); used with access control as 4, and delivery/notifications.

**github**: follow a user (see all activity in feed), but primary method seems to be to follow content/threads.

6. Portability?

**FOAF**: Server agnostic, move data as you please, but you need to control your domain.

**Indieweb**: Server agnostic, move data as you please, but you need to control your domain.

**Twitter**: You can download an archive of content and snapshot of profile attributes (and date of snapshot) but no changes history.

**Tumblr**: Third party tools only, references from some time ago, don't know if they still work.

**Pump.io**: Open format, AS JSON. No API for export, or anything in Web client. Can theoretically move between servers.

**YouTube**: Google Takeout export as JSON or OPML. Export analytics.

**CouchSurfing**: n/a

**Facebook**: You can download all of your data. https://www.facebook.com/help/405183566203254 "This includes a lot of the same information available to you in your account and activity log, including your Timeline info, posts you have shared, messages, photos and more. Additionally, it includes information that is not available simply by logging into your account, like the ads you have clicked on, data like the IP addresses that are logged when you log into or out of Facebook, and more."

**Quora**: No export, no API

**Okcupid**: No official API, no export.

**StackOverflow**: Profiles reusable across StackExchange sites. Export n/a through UI, but there are public dumps of q&a data.

**LinkedIn**: Can download a full archive of all data, activity, connections, *everything*.

**PeoplePerHour**: n/a

**ResearchGate**: Export profile as csv.

**AirBnB**: Nothing for profile. Export csv of transaction history, and various calendar syncing.

**Friendica**: ActivityStreams. Various levels of compatability with APIs of GNU Social, pump.io, Twitter, diaspora. Profile and connections portable to another server. You can also use your friendica identity via webfinger to identify with a bunch of other things like remotestorage, owncloud.

```
* Friendica uses DFRN as message protocol.
* The messages uses ActivityStreams.
* Webfinger is used for the discovery of users
* Salmon is used as a message exchange protocol for replies and mentions.
* Portable Contacts is used for friends lists.
* pubsubhubbub is used for OStatus.
```

**Zooniverse**: n/a

**runkeeper**: All data exportable, not standard format.

**github**: repo content is inherantly portable via git; other stuff avaiable through API but no standard format.

7. Restrictions?

**FOAF**: n/a

**Indieweb**: n/a

**Twitter**: ~"may not create multiple accounts with overlapping use cases"

**Tumblr**: Needs valid email. Create 10 secondary blogs per day. No way to have two primary blogs on the same email address.

Secondary blogs can't 'initiate social features' (follow, like, ask, fan mail etc).

**Pump.io**: Server specific ToS?

**YouTube**: Some ToS rules about linking to external sites.

**CouchSurfing**:

```
5. Do Create Only One Profile: Duplicate, fake, and joke profiles are not allowed. The first profile that you create must be you and is the only one that you may have. Our trust network needs everyone to stand by their reputation.

6. Do Be Yourself: Misrepresenting yourself as someone else is prohibited. This includes representation as an agent, representative, employee, or affiliate of Couchsurfing.
```

**Facebook**:

```
Registration and Account Security

Facebook users provide their real names and information, and we need your help to keep it that way. Here are some commitments you make to us relating to registering and maintaining the security of your account:

* You will not provide any false personal information on Facebook, or create an account for anyone other than yourself without permission.
* You will not create more than one personal account.
* If we disable your account, you will not create another one without our permission.
...
* You will keep your contact information accurate and up-to-date.
* You will not share your password (or in the case of developers, your secret key), let anyone else access your account, or do anything else that might jeopardize the security of your account.
* You will not transfer your account (including any Page or application you administer) to anyone without first getting our written permission.
* If you select a username or similar identifier for your account or Page, we reserve the right to remove or reclaim it if we believe it is appropriate (such as when a trademark owner complains about a username that does not closely **relate to a user's actual name**).
```

**Quora**:

```
... you must provide us accurate information, including your real name, when you create your account on Quora.

agree that you have not and will not contribute any Content that ... (e) creates an impression that you know is incorrect, misleading, or deceptive, including by impersonating others or otherwise misrepresenting your affiliation with a person or entity;
```

**OkCupid**:

```
Unique and bona fide profile
You agree to create only one unique profile. In addition, in order to maintain the integrity of the Website, by joining, you agree that your use of the Website shall be for bona fide relationship-seeking purposes (for example, you may not use the Website solely to compile a report of compatible singles in your area, or to write a school research paper). From time to time, we may create test profiles in order to monitor the operation of our services.
```

**StackOverflow**:

```
Subscriber shall provide Stack Exchange with accurate, complete, and updated registration information, including Subscriber’s e-mail address. Failure to do so shall constitute a breach of this Agreement, which may result in immediate termination of Subscriber's account. Subscriber may not (a) select or use as a profile name a name of another person with the intent to impersonate that person; or (b) use as a profile name a name subject to any rights of a person other than Subscriber without appropriate authorization.
```

**LinkedIn**:

```
To use the Services, you agree that: ... (2) you will only have one LinkedIn account, which must be in your real name

You agree to ... (3) not transfer any part of your account (e.g., connections, groups)
```

**PeoplePerHour**:

```
To use PPH, Users have to register for an account, provide accurate and complete information, and keep their account information updated. Both Buyers and Sellers undergo the same account registration process.
Each account must be a personal account, but Users may trade as a sole trader, company or any other legal entity (whether incorporated or unincorporated).
Users cannot register for more than one account.
The information that Users supply in the public profile of their account must comply with PPH profile policies (http://support.peopleperhour.com/hc/en-us/articles/205218177-Profile-policies)

Your profile is your “shop front” as a Seller so it is recommended that you invest the time to include as much information as you can to highlight your skills and credentials.   When creating your profile we have a few policies that Sellers are expected to adhere to.  These policies form part of our T&Cs.

 

Do

make sure that all of the information contained in your profile is a true and accurate representation.  Including your name, location and details of your credentials;
include a professional image of yourself as your profile image.  You can choose to have your company logo instead however we strongly recommend a personal photo instead.  The PPH marketplace is built on trust and personal photos rather than logos have been shown to make a significant difference to success;
include as profile cover a quality image or photo of yourself or a scenery. Avoid excessive amount of text keeping it to the length of a tagline. You can include visual representation of your work or part of your actual portfolio if visual.
Don't

include your full name, or contact details in your profile description, cover image, portfolio items or any other section of your profile.  This rule is first and foremost to protect you; we would discourage you from publishing your contact details visibly on any public site.
open more than one user account with PeoplePerHour.  Duplicate accounts will be closed;
include any links to your website or any third party website anywhere in your profile including your profile image or portfolio images;
upload any content to your profile that breaches our terms and conditions including all the obvious things like abusive, offensive, defamatory or infringing content.
share your bank account or any other withdrawal method. Such practice is against our Terms and Conditions of Website Use and leads to permanent account suspension.
```

**ResearchGate**: Nothing to do with profiles?!

**AirBnB**:

```
Your Airbnb Account and your Airbnb Account profile page will be created for your use of the Site and Application based upon the personal information you provide to us or that we obtain via an SNS as described above. You may not have more than one (1) active Airbnb Account. You agree to provide accurate, current and complete information during the registration process and to update such information to keep it accurate, current and complete. Airbnb reserves the right to suspend or terminate your Airbnb Account and your access to the Site, Application and Services if you create more than one (1) Airbnb Account, or if any information provided during the registration process or thereafter proves to be inaccurate, fraudulent, not current or incomplete.

you will not: ...
* register for more than one Airbnb Account or register for an Airbnb Account on behalf of an individual other than yourself;
* unless Airbnb explicitly permits otherwise, request or book a stay at any Accommodation if you will not actually be staying at the Accommodation yourself;
* impersonate any person or entity, or falsify or otherwise misrepresent yourself or your affiliation with any person or entity;
```

**Friendica**: ToS per server presumably.

**Zooniverse**: Nothing profile related

**runkeeper**:

```
agree that you will not: ... (v) impersonate another person.
```

**github**:

```
You must be a human. Accounts registered by "bots" or other automated methods are not permitted.

You must provide your name, a valid email address, and any other information requested in order to complete the signup process.

Your login may only be used by one person - a single login shared by multiple people is not permitted. You may create separate logins for as many people as your plan allows.

One person or legal entity may not maintain more than one free account.
```

8. Model?

TODO: *add diagrams*

**FOAF**: [ PersonalProfileDocument] -- maker --> [ Person ] -- {attributes} --> "value". Usually inferred that a foaf file is a PersonalProfileDocument where the subject is the `maker`. Definite distinction between the person and the document about them.

**Indieweb**: Use site URLs to refer to people. Attributes attached to `h-card`, embedded in homepage alongside other content.

**Twitter**: account ~= profile ~= person

**Tumblr**: Primary blog ~= user/account, but also blog. Secondary blog = blog. user can create many secondary blogs. Secondary blog can have many users as members.

**Pump.io**: AS Person: url, image, displayName, id, arbitrary extension properties. Profile URL + webfinger user@server id. `actor` relation with activities, `author` relation with objects.

**YouTube**: one Google account, many channels. Channels as personas (ie. you post comments / act as a channel)

**CouchSurfing**: real people with info about them.

**Facebook**: "When something has a profile, Graph API returns the fields for that object. (User, Page, Group, Event, Application)"

**Quora**: real people with info about them; content-oriented where reputation is built on content votes, and trust from completing profile.

**Okcupid**: personas with attributes.

**StackOverflow**: content-oriented.. people/personas with info about them.

**LinkedIn**: Real people with attributes and experiences.

**PeoplePerHour**: Real people with attributes and experience and endorsements from others.

**ResearchGate**: Real people.

**AirBnB**: real people.

**Friendica**: Personas with profiles. [This](https://github.com/friendica/friendica/blob/master/doc/Profiles.md) describes how alternative profiles work, but I can't find these settings in friendica.eu right now (I have seen them before for sure). You can create versions of yourself with different attributes, and assign them so certain people see certain profiles when the look at you. Ie. profiles as views on a person. Also your profile can be a different 'page type' which automates connections settings in different ways, eg. for celebrities.

**Zooniverse**: From http://www.arfon.org/how-the-zooniverse-works-the-domain-model

```
User

People are core to the Zooniverse. When talking publically about the Zooniverse I almost always use the term 'citizen scientist' or 'volunteer' because it feels like an appropriate term for someone who donates their time to one of our projects. When writing code however, the shortest descriptive term that makes sense is usually selected so in our domain model the term we use is User.

A User is exactly what you'd expect, it's a person, it has a bunch of information associated with it such as a username, an email address, information about which projects they've helped with and a host of other bits and bobs. Crucially though for us, a User is the same regardless of which project they're working - that is Users are pan-Zooniverse. Whether you're classiying galaxies over at Galaxy Zoo or identifying animals on Snapshot Serengeti we're associating your efforts with the same User record each time which turns out to be useful for a whole bunch of reasons (more later).
```

**runkeeper**: person with IRL attributes and activities logged.

**github**: content/activity-oriented.. people/users with attriutes about them, and relationships to content/actions.

9. What is a profile for?

**FOAF**:

**Indieweb**:

**Twitter**:

* Tumblr
* Pump.io
* YouTube
* CouchSurfing
**Facebook**:
* Quora
**Okcupid**:
* StackOverflow
* LinkedIn
* PeoplePerHour
**ResearchGate**:
* AirBnB
* Friendica



* zooniverse
* runkeeper
* github

10. Who is a profile for?
 
**FOAF**:

**Indieweb**:

**Twitter**:

* Tumblr
* Pump.io
* YouTube
* CouchSurfing
**Facebook**:
* Quora
**Okcupid**:
* StackOverflow
* LinkedIn
* PeoplePerHour
**ResearchGate**:
* AirBnB
* Friendica



* zooniverse
* runkeeper
* github
