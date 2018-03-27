# rdwtechday.github.io
Rdw Techday Conference Site

## Design of this site
This site is using the github pages mechanism. You can use [Jekyll](https://jekyllrb.com/) to run the site content locally on your machine. 
The CNAME file contains the external URL through which this site can be reached. This site uses bootstrap to render responsive content.

The main layout is defined but the `/_layouts/home.html` page. All the other page lay-outs are defined by `/_layouts/page.html`. In the `home.html` and `page.html` pages a number of includes are loaded from `/_includes`.

The pages shown in the top right menu are all grouped in the root folder. Adding a page here will add an extra menu button. The order of the menu is determined
by the order field in the page file.examples of page files are: `sessies.html` and `about.md`. The first is in html, the latter in markdown.

We have three collections:
- Speakers
- Sessions
- Organizers

### Speakers Collection
The speaker pages are located in `/_sprekers` and have three fields, the part beneath the last three dashes is used as a bio for the speaker. 
```yaml
---
naam: John Doe
ref: john-doe
titel: Chief Mugwump
---
bio
```
- `naam:` contains the name of the speaker
- `ref`: contains a reference value which is used by the session collection and to find the speaker image in `/assets/people/<ref>.jpg`. No spaces allowed. I make it lower case and replace spaces by a `-` sign.
- `titel`: The titel of the speaker
-  `bio`: The text is a markdown formatted text and will be converted to html automatically when the site is loaded by github pages.

The connection between a speaker and a session is made in the session files, see next section.

### Sessions collection
The session pages are located in `/_sessions` and have five fields, the part beneath the last three dashes is used as a description for the session. 

```yaml
---
sprekers: john-doe
track: Track A
titel: A wonderfull session
tijd: "11:00-12:00"
---
session description
```

- `speakers:` is a list of speakers doing the session. it is a list of the ref value found in each speaker page
- `track:` the track in which the session resides
- `titel` the title of the session
- `tijd` the time of the session

The speaker list can be formatted like this
```yaml
speakers: john-doe
```
or like this when you have multiple speakers
```yaml
speakers: 
- john-doe
- zaphod-beeblebrox

#alternative notation
speakers: [john-doe, zaphod-beeblebrox]
```


### Organizers collection
The organizer pages are located in `/_organizers` and have three fields, the part beneath the last three dashes is not used. Organizers are shown in the `/about.html` page.
```yaml
---
naam: John Doe
ref: john-doe
rol: Organizing endboss
---
```
- `naam:` contains the name of the organizer
- `ref`: contains a reference value which is used by the session collection and to find the speaker image in `/assets/people/<ref>.jpg`. No spaces allowed. I make it lower case and replace spaces by a `-` sign.
- `rol`: contains the role/function of the organizer.


## Network settings for this site
add the following A records to your DNS settings for the name in the CNAME file, this will point it to Github and through the CNAME file github knows which site to render.
```
@ A 192.30.252.153
@ A 192.30.252.154
```
