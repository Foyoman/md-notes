✅: done | 🧑🏻‍💻: in progress
1. Read through and figure out what you need to do, step by step
2. Take notes here, so you have a visual grasp of what's to be done, so you don't get overwhelmed trying to figure out and remember everything in your head, and so you can come back to it later
	- Note each file you need to work in
3. Work through each step, checking things off one at a time
---
### 🧑🏻‍💻 `feature/theme/preview`
- `mixins/layout` > `computed/siteStyles` > `rootVars`
- Async data fetching in the store, location info in manage preferences
---
### admin/wiki
---
### 🧑🏻‍💻 [Re: questions with Ovatu Next](https://secure.helpscout.net/conversation/2471950954/191244?folderId=7922220)
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
---
### ✅ [problem with sales](https://secure.helpscout.net/conversation/2497278849/193923?folderId=7922220) `bugfix/order-ymd-filter`
- Timezones
- Jan 31st sales are displaying on the Sales page in the web app. However there seems to be an issue with the date picker on the Sales page as the system is showing sales from the previous day as well as the current date.
- Its not being converted to the locations timezone. Tash was getting offset results because the customer is in Canada
- Files:
	- `pages/order/index.vue`
	- `components/order/elements/DateRange.vue`
- 
---
### [Reports](https://secure.helpscout.net/conversation/2489486135/193096?folderId=7922220)
- Timezones
- Daily reports adding different days to the total
- When you open the sales report and tap on the **Filter** button and select the **Daily** filter option, currently 2 dates are pre-selected. Those are yesterday and today. That then shows the sales for both days. When you tap on the calendar to select a different date, a date range is offered. To only show the sales for 1 day that one date needs to be entered into both those date fields. E.g. to see sales dated 12 December you'd add that date to both date filter fields.
---
### ✅ [Translation](https://secure.helpscout.net/conversation/2526780345/197035?folderId=7922220)
- Some of the strings are still not translated (Croatian):
	- Date & time = Datum i vrijeme
	- Apply promo code / gift card = Upotrijebi promotivni kod / poklon karticu
	- Pay later = Plati kasnije  
	- Use pass = Koristi paket
- inspect other language translation files 
---
### ✅ `bugfix/rebook-datepicker`
---
### [Re: Notifications](https://secure.helpscout.net/conversation/2483654426/192514?folderId=7922220)
- They moved to next purely for the reason so they could move clients without being notified, yet it's still happening
- They are referring to the SMS notification
- Moving bookings/appointments > 'Reset reminders' toggle option. That resends the reminder email and SMS
- Sometimes they just edit the name to move it as the other way is so sensitive and jumps into a different time by a few mins sending move notifications. They want default off setting
- When they change the employee or time on the service settings, no move alert or reminder update is sent. If the entire reservation is moved, turning off the reset reminders/move alert does not send a reminder update or move email
- They have the move reservation option switched off by default, so these are not sending when they move appointments. However, there is not currently a way of turning off the reset reminder toggle by default. This is always on, and must be manually turned off when making changes to a whole reservation. They will find out if we can edit the default for the reminder reset, in the same way we have with the move email. In the meantime, their option of editing the individual service is a good solution, and if you are making changes to the whole reservation, please ensure they untick/untoggle the reset reminder option
- Due to the system sending out reminder updates when an appointment is moved after the initial reminder is sent, we introduced a toggle to turn this off the 'reset reminders' when moving an appointment. They have asked if we can provide the option to have it switched off by default as turning it off every time is apparently not ideal. It's possible to turn off the move email by default so that you have to toggle it on, but the reset reminders option is always on by default
- When an appointment is created on one device, it doesn't show on another device until the appointments page is refreshed. Is there a way to auto refresh the appointments page in that scenario?
---
### ✅ [No way to reset password from mobile](https://secure.helpscout.net/conversation/2502362516/194413?folderId=7922220)
- Issues logging into Next mobile app on iPad when the password isn't known
- No way to reset password if it's not known or request a login code
- Copy 'Request password reset' functionality from web app
- [auth/login/email]() in a domain, enter email then 'Enter password' > [auth/login/password]()
- 'Request password reset' link is on [auth/login/password](), it leads to [auth/reset/email]()
- [auth/reset/email]() has email input and 'Request code' button
- 'Request code' links to [auth/reset/confirm]()
- `confirm.vue` on mounted `handleRequestCode()` 
- `handleRequestCode`: `this.$auth.requestCode(params)` where `params` is `{ ...location, email }`
- `requestCode` > `resetPassword`
- The same `requestCode` is used for logging in with a code as resetting a password
- Files:
	- manager web (reference):
		- `pages/auth/index/login/index/password.vue`
		- `pages/auth/index/reset/index/email.vue`
		- `pages/auth/index/reset/index/confirm.vue`
		- `api/models/auth.js`
	- manager_flutter:
		- `lib/views/auth/login.dart`
		- `lib/data/api/auth_api.dart`
---
### [Changing 'receipt' template](https://secure.helpscout.net/conversation/2536523006/198137?folderId=7922220)
- They have two issues, first, the customer address is not showing on the receipt template (A4 version). Nor is the information from the sales tax information from the manage > general > sales tax information box. They would also like to change the wording on the receipt template. Is that not possible?
---
### `feature/customer-register`
---
### `formbuilder/preview`
- "Hey [@Edward Do]() for the Annotation form item, can this be hooked up to the Asset Library? I.e. so it works similar to image uploads in the custom pages editor"