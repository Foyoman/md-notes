✅: done | 🧑🏻‍💻: in progress
1. Read through and figure out what you need to do, step by step
2. Take notes here, so you have a visual grasp of what's to be done, so you don't get overwhelmed trying to figure out and remember everything in your head, and so you can come back to it later
	- Note each file you need to work in
3. Work through each step, checking things off one at a time
---
### - 🧑🏻‍💻 `feature/theme/preview`
- `mixins/layout` > `computed/siteStyles` > `rootVars`
- async data fetching in the store, location info in manage preferences

### - bruno

### - admin/wiki

### - 🧑🏻‍💻 [Re: questions with Ovatu Next](https://secure.helpscout.net/conversation/2471950954/191244?folderId=7922220)
- Appointments problem:
	- Appointments tab, click on scheduled appointment should show your whole day but doesn't work more often than not - instead it offers the move option and doesn't open the appointment, then you have to scroll to find them on the lefthand sidebar.
- ✅ Notes problem:
	- When in a client profile under the add a note section, when you expand the viewing size of the note, the add note button disappears and all you can do is x out and usually lose everything on the note. It would be nice to see more than 4/5 lines of the note at a time. Only appears to happen in Safari
	- `Downloads/Notes problem.mov`
- Form problem:
	- Within the Ovatu Next app, when adding pictures taken in the client profile to their profile there is an uploading feature that now locks the entire system until the pictures are uploaded which if you have a few it can take a while making your system unusable. Images transferred from the old Ovatu to Ovatu Next are low quality.
	- Form on the mobile app
	- `Downloads/Form problem.mov`
- Saving problem:
	- Saving issue on the mobile platform. Appointment > form > save
	- `Downloads/Error and saving issue.mov`

### - [problem with sales](https://secure.helpscout.net/conversation/2497278849/193923?folderId=7922220)
- timezones
- Jan 31st sales are displaying on the Sales page in the web app. However there seems to be an issue with the date picker on the Sales page as the system is showing sales from the previous day AS WELL AS the current date.
- Its not being converted to the locations timezone. Tash was getting offset results because the customer is in Canada
- files:
	- `pages/order/index.vue`
	- `components/order/elements/DateRange.vue`

### - [Reports](https://secure.helpscout.net/conversation/2489486135/193096?folderId=7922220)
- timezones
- Daily reports adding different days to the total
- When you open the sales report and tap on the **Filter** button and select the **Daily** filter option, currently 2 dates are pre-selected. Those are yesterday and today. That then shows the sales for both days. When you tap on the calendar to select a different date, a date range is offered. To only show the sales for 1 day that one date needs to be entered into both those date fields. E.g. to see sales dated 12 December you'd add that date to both date filter fields.

### - ✅ [Translation](https://secure.helpscout.net/conversation/2526780345/197035?folderId=7922220)
- Some of the strings are still not translated (Croatian):
	- Date & time = Datum i vrijeme
	- Apply promo code / gift card = Upotrijebi promotivni kod / poklon karticu
	- Pay later = Plati kasnije  
	- Use pass = Koristi paket
- inspect other language translation files 

### - ✅ `bugfix/rebook-datepicker`

### - [Re: Notifications](https://secure.helpscout.net/conversation/2483654426/192514?folderId=7922220)

### - [No way to reset password from mobile](https://secure.helpscout.net/conversation/2502362516/194413?folderId=7922220)
- Issues logging into Next mobile app on iPad when the password isn't known
- No way to reset password if it's not known or request a login code
- Copy 'Request password reset' functionality from web app
- 'Request password reset' link is on [auth/login/password], it leads to [auth/reset/email]
- [auth/reset/email] has email input and 'Request code' button
- 'Request code' links to [auth/reset/confirm]
- `confirm.vue` on mounted `handleRequestCode()` 
- `handleRequestCode`: `this.$auth.requestCode(params)` where `params` is `{ ...location, email }`
```js
static requestCode ({ oauth_client, location, email }) {
	const url = this.modelBaseURL() + '/requestCode'
	const params = {
		  oauth_client,
		  location,
		  email
	}
	
	return this.requestData(Request.post(url, JSON.stringify(params)))
}
```
- files:
	- `pages/auth/index/login/index/password.vue`
	- `pages/auth/index/reset/index/email.vue`
	- `pages/auth/index/reset/index/confirm.vue`
	- `api/models/auth.js`