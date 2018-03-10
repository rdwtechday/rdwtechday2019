# rdwtechday.github.io
Rdw Techday Conference Site

## Design of this site
The main layout is defined but the `/_layouts/home.html` page. All the other page lay-outs are defined by `/_layouts/page.html`. In the home.html and page.html pages a number of includes are loaded from `/_includes`.

The pages shown in the top right menu are all grouped in the root folder. Adding a page here will add an extra menu button.

We have three collections:
- Organizer
- Speaker
- Session

### Organizer collection
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
- `rol`: contains the role of he organizer.

### Speaker Collection
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


A session is linked to a speaker through the sprekers field, the sprekers field must contain spreker.ref field. If so it will be shown linked to 

### Session collection
The session pages are located in `/_sessions` and have five fields, the part beneath the last three dashes is used as a description for the session. 

- `speakers`: is a list of speakers doing the session. it is a list of the ref value in the speaker pages

The speaker list can be formatred like this
```yaml
speakers: single-speaker
```
or like this when you have multiple speakers
```yaml
speakers: 
- speaker-one
- speaker-two
```


## Network settings for this site
add the following A records to your DNS seettings
```
@ A 192.30.252.153
@ A 192.30.252.154
```
