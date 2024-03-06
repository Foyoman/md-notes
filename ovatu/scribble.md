✅: done | 🧑🏻‍💻: in progress
1. Read through and figure out what you need to do, step by step
2. Note it down here, so you have a visual grasp of what's to be done, so you don't get overwhelmed trying to figure out and remember everything in your head, and so you can come back to it later
3. Work through each step, checking things off one at a time
---
### - 🧑🏻‍💻 `feature/theme/preview`
- `mixins/layout` > `computed/siteStyles` > `rootVars`
- async data fetching in the store, location info in manage preferences

### - bruno

### - admin/wiki

### - 🧑🏻‍💻 [Re: questions with Ovatu Next](https://secure.helpscout.net/conversation/2471950954/191244?folderId=7922220)
- Appointments tab, click on scheduled appointment should show your whole day but doesn't work more often than not - instead it offers the move option and doesn't open the appointment, then you have to scroll to find them on the lefthand sidebar.
- When in a client profile under the add a note section, when you expand the viewing size of the note, the add note button disappears and all you can do is x out and usually lose everything on the note. It would be nice to see more than 4/5 lines of the note at a time. Only appears to happen in Safari
	- `Downloads/Notes problem.mov`
- Within the Ovatu Next app, when adding pictures taken in the client profile to their profile there is an uploading feature that now locks the entire system until the pictures are uploaded which if you have a few it can take a while making your system unusable. Images transferred from the old Ovatu to Ovatu Next are low quality.
- Form on the mobile app
	- `Downloads/Form problem.mov`
- Saving issue on the mobile platform. Appointment > form > save
	- `Downloads/Error and saving issue.mov`

### - [problem with sales](https://secure.helpscout.net/conversation/2497278849/193923?folderId=7922220)
- Jan 31st sales are displaying on the Sales page in the web app. However there seems to be an issue with the date picker on the Sales page as the system is showing sales from the previous day AS WELL AS the current date.
- Its not being converted to the locations timezone. Tash was getting offset results because the customer is in Canada
- files:
	- `pages/order/index.vue`
	- `components/order/elements/DateRange.vue`

Testing the autosave feature and how it works and stuff

testing this stuff

one two four