1. What does a profile contain?

**FOAF**: Attributes (fixed in FOAF but extensible with other vocabs), connections, links to authored content (maybe).

**Indieweb**: Attributes (fixed as per microformats2 but extensible), authored content.

**Twitter**: Attributes (fixed set), connections (subset), authored content, activities within the network (heavily curated).

2. How are profiles updated?

**FOAF**: not spec'd (likely hand editing or through a client).

**Indieweb**: not spec'd (likely editing static HTML).

**Twitter**: Web form / client UI.

3. How are people notified of profile updates?

**FOAF**: not spec'd

**Indieweb**: not spec'd

**Twitter**: None.

4. Access control?

**FOAF**: not spec'd (WebID+TLS/WebAccessControl for protecting whole documents not individual attributes).

**Indieweb**: not spec'd

**Twitter**: All or nothing for content. A blocked user can still see some attributes (avatar, banner, name). Protected accounts show all profile data but not content or followers/ing

5. Connections?

**FOAF**: `knows` - one way relationship, deliberately vague.

**Indieweb**: Under debate, some people use XFN (eg. `rel=following`)

**Twitter**: One directional; notifications sometimes sent to your followers when you follow someone, especially if others in your network also do; follows (some? all? curated how?) appear in your timeline; no notifications of unfollows; configurable notification when someone follows you.

6. Portability?

**FOAF**: Server agnostic, move data as you please, but you need to control your domain.

**Indieweb**: Server agnostic, move data as you please, but you need to control your domain.

**Twitter**: You can download an archive of content and snapshot of profile attributes (and date of snapshot) but no changes history.

7. Restrictions?

**FOAF**: n/a

**Indieweb**: n/a

**Twitter**: ~"may not create multiple accounts with overlapping use cases"

8. Model?

TODO: *add diagrams*

**FOAF**: [ PersonalProfileDocument] -- maker --> [ Person ] -- {attributes} --> "value". Usually inferred that a foaf file is a PersonalProfileDocument where the subject is the `maker`. Definite distinction between the person and the document about them.

**Indieweb**: Use site URLs to refer to people. Attributes attached to `h-card`, embedded in homepage alongside other content.

**Twitter**: account ~= profile ~= person

9. What is a profile for?

**FOAF**:

**Indieweb**:

**Twitter**:

10. Who is a profile for?
 
**FOAF**:

**Indieweb**:

**Twitter**:
