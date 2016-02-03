

1. What does a profile contain?

**FOAF**: Attributes (fixed in FOAF but extensible with other vocabs), connections, links to authored content (maybe).

**Indieweb**: Attributes (fixed as per microformats2 but extensible), authored content.

**Twitter**: Attributes (fixed set), connections (subset), authored content, activities within the network (heavily curated).

**Tumblr**: Content; original posts and reposts. Attributes: username, blog title, blog description. (Separate page for likes which is optionally public). No stats by default.

**Pump.io**: Attributes (name, hometown, bio, avatar) and content (major in main feed) and activities (minor down the side) (ActivityStreams)

**YouTube**: channel art, display picture, content (videos), liked videos, created playlists, curated connections, featured content. Links to: attributes (description, links, country); stats (subs, views, joined); discussion (comments on your content).

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
* Diaspora
* Reddit
* Imgur
* zooniverse
* runkeeper
* github

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
* Diaspora
* Reddit
* Imgur
* zooniverse
* runkeeper
* github

3. How are people notified of profile updates?

**FOAF**: not spec'd

**Indieweb**: not spec'd

**Twitter**: None.

**Tumblr**: None.

**Pump.io**: minor 'update' activity

**YouTube**: None.

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
* Diaspora
* Reddit
* Imgur
* zooniverse
* runkeeper
* github

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
* Diaspora
* Reddit
* Imgur
* zooniverse
* runkeeper
* github

5. Connections?

**FOAF**: `knows` - one way relationship, deliberately vague.

**Indieweb**: Under debate, some people use XFN (eg. `rel=following`)

**Twitter**: One directional; notifications sometimes sent to your followers when you follow someone, especially if others in your network also do; follows (some? all? curated how?) appear in your timeline; no notifications of unfollows; configurable notification when someone follows you.

**Tumblr**: `Follow` a blog. (Not a user).

**Pump.io**: `Follow` a user. Minor activity and notification when someone follows you. Added to 'follows' collection (public). One way.

**YouTube**: `Subscribe` to a channel, one way.

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
* Diaspora
* Reddit
* Imgur
* zooniverse
* runkeeper
* github

6. Portability?

**FOAF**: Server agnostic, move data as you please, but you need to control your domain.

**Indieweb**: Server agnostic, move data as you please, but you need to control your domain.

**Twitter**: You can download an archive of content and snapshot of profile attributes (and date of snapshot) but no changes history.

**Tumblr**: Third party tools only, references from some time ago, don't know if they still work.

**Pump.io**: Open format, AS JSON. No API for export, or anything in Web client. Can theoretically move between servers.

**YouTube**: Google Takeout export as JSON or OPML. Export analytics.

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
* Diaspora
* Reddit
* Imgur
* zooniverse
* runkeeper
* github

7. Restrictions?

**FOAF**: n/a

**Indieweb**: n/a

**Twitter**: ~"may not create multiple accounts with overlapping use cases"

**Tumblr**: Needs valid email. Create 10 secondary blogs per day. No way to have two primary blogs on the same email address.

Secondary blogs can't 'initiate social features' (follow, like, ask, fan mail etc).

**Pump.io**: Server specific ToS?

**YouTube**: Some ToS rules about linking to external sites.

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
* Diaspora
* Reddit
* Imgur
* zooniverse
* runkeeper
* github

8. Model?

TODO: *add diagrams*

**FOAF**: [ PersonalProfileDocument] -- maker --> [ Person ] -- {attributes} --> "value". Usually inferred that a foaf file is a PersonalProfileDocument where the subject is the `maker`. Definite distinction between the person and the document about them.

**Indieweb**: Use site URLs to refer to people. Attributes attached to `h-card`, embedded in homepage alongside other content.

**Twitter**: account ~= profile ~= person

**Tumblr**: Primary blog ~= user/account, but also blog. Secondary blog = blog. user can create many secondary blogs. Secondary blog can have many users as members.

**Pump.io**: AS Person: url, image, displayName, id, arbitrary extension properties. Profile URL + webfinger user@server id. `actor` relation with activities, `author` relation with objects.

**YouTube**: one Google account, many channels. Channels as personas (ie. you post comments / act as a channel)

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
* Diaspora
* Reddit
* Imgur
* zooniverse
* runkeeper
* github

9. What is a profile for?

**FOAF**:

**Indieweb**:

**Twitter**:

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
* Diaspora
* Reddit
* Imgur
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
* Facebook
* Quora
* OkCupid
* StackOverflow
* LinkedIn
* PeoplePerHour
* Academia.edu
* AirBnB
* Friendica
* Diaspora
* Reddit
* Imgur
* zooniverse
* runkeeper
* github
