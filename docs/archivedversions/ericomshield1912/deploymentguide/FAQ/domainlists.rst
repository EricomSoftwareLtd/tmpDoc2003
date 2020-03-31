*************
Domains Lists
*************

When browsing to a domain, many times there are redirections to other domains along the way, until the original domain is reached and opened.
This may also happen in websites that include different resources within the page.
If a domain is shielded but its redirections/resources are whitelisted - browsing to this domain may fail and page will not be loaded properly (sometimes even not loaded at all).
Same outcome may occur if the original domain is whitelisted and one of the redirections/resources is shielded.
For certain domains to work properly as shielded or as whitelisted within Shield, additional domains should also to be defined in the Policies table (with the same Access policy value).
Here is a detailed list of highly used domains and their additional related domains. Once the original domain (in the title) is added to the Policies table, all related domains should be included as well.

.. note:: When adding these domains to the Policies table, please clear the cache and allow a few minutes for updates to take effect.

**Amazon**

ssl-images-amazon.com

**Dropbox**

db.tt

dropbox.com

dropboxapi.com

dropboxbusiness.com

dropboxforums.com

dropboxforum.com

dropboxinsiders.com

dropboxmail.com

dropboxpartners.com

dropboxstatic.com

dropbox.zendesk.com

getdropbox.com

instructorledlearning.dropboxbusiness.com

paper.dropbox.com

For a more updated list, please see: `here <https://www.dropbox.com/help/security/official-domains#domains>`_.

**Ebay**

ebaystatic.com

ebayimg.com

ebayrtm.com

**Facebook**

s-static.ak.facebook.com

static.ak.facebook.com

graph.facebook.com

upload.facebook.com 

chat.facebook.com

apps.facebook.com

channel.facebook.com

pixel.facebook.com

star.facebook.com

star.c10r.facebook.com

vupload2.facebook.com

vupload2.t.facebook.com

b-api.facebook.com

fbcdn.net

fbsbx.com

**Google Chat**

xmpp-server.l.google.com

chatenabled.mail.google.com

talkgadget.google.com

talk.google.com

talks.l.google.com

**Google Talk**

talkx.l.google.com

talk.l.google.com

talk.google.com

**Google Drive**

www.google.com

accounts.google.com

clients3.google.com

talk.google.com

drive.google.com

www.googleapis.com

ssl.gstatic.com

docs.google.com

drive.google.com

googleusercontent.com

s.ytimg.com

video.google.com

lh3.google.com

lh4.google.com

lh5.google.com

lh6.google.com

**iTunes**

itunes.apple.com

ax.itunes.apple.com

ax.init.itunes.apple.com

albert.apple.com

gs.apple.com

phobos.apple.com

mzstatic.com

akamai.net

**LinkedIn**

edge.quantserve.com

secure-us.imrworldwide.com

b.scorecardresearch.com

pixel.quantserve.com

**Microsoft OneDrive**

akadns.net

akamai.net

edgesuite.net

live.com

live.net

mesh.com

microsoft.com

msn.com

nexus.passport.com

nsatc.net

verisign.com

windows.com

windowsupdate.com

windowsupdate.nsatc.net

**Netflix**

btstatic.com

customerevents.netflix.com

movies.netflix.com

nccp.netflix.com

nflxext.com

nflximg.com 

nflximg.net

nflxvideo.net

secure.netflix.com

**Pinterest**

pinterest.com

s-media-cache-ak0.pinimg.com

s-passets-cache-ak0.pinimg.com

pinimg.com

**Slack**

slack.com

a.slack-edge.com

**Spotify Browser Player**

akamaiedge.net

ap.spotify.com

apresolve.spotify.com

cdn.betrad.com

cloudfront.net

d2c87l0yth4zbw.cloudfront.net

embed.spotify.com

gslb.spotify.com

l.betrad.com

play.spotify.com

play.spotify.edgekey.net

spapps.co

spapps.spotify.edgekey.net

**Twitter**

twimg.com

api.twitter.com

pic.twitter.com

dev.twitter.com

platform.twitter.com

search.twitter.com

userstream.twitter.com

twimg0-a.akamaihd.net

upload.twitter.com

api.twitter.com

**Vimeo**

vimeo.com

vimeocdn.com

**Windows Live Messenger**

login.live.com

contacts.msn.com

storage.msn.com

c.msn.com

messenger.msn.com

g.msn.com

crl.microsoft.com

messenger.hotmail.com

rsi.hotmail.com

sqm.microsoft.com

messenger.live.com

rad.msn.com

spaces.live.com

dp.msnmessenger.akadns.com

echo.edge.messenger.live.com

livefilestore.com

**Yahoo Messenger**

messenger.yahoo.com

msg.edit.yahoo.com

msg.yahoo.com

webcam.yahoo.com

vc.yahoo.com

**YouTube**


www.youtube-nocookie.com

c.youtube.com

ytimg.l.google.com

googlesyndication.com

ytimg.com

accounts.google.com

youtube.l.google.com

**How To Discover Additional Domains**

When a domain (not from this list) is added to the Policies table but does not function as expect, it is possible that related domains are involved but were not added to the table yet.
To discover if additional domains should be added to the table, open the **Connections** report and inspect the entries that were registered **immediately after** browsing to the specific domain.
This method may help to decide which additional domains should be added.

If there are still domains that cannot be browsed properly, please contact Ericom Shield Professional Servicess for further assistance.
