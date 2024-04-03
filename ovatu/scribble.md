✅: done | 🧑🏻‍💻: in progress
1. Read through and figure out what you need to do, step by step
2. Take notes here, so you have a visual grasp of what's to be done, so you don't get overwhelmed trying to figure out and remember everything in your head, and so you can come back to it later
	- Note each file you need to work in
3. Work through each step, checking things off one at a time
---
### meat
---
### 🧑🏻‍💻 `feature/theme/preview`
- `mixins/layout` > `computed/siteStyles` > `rootVars`
- Async data fetching in the store, location info in manage preferences
- when site loaded, brief flash of default theme
- preview of selected
- add more preset themes
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
### [Reports](https://secure.helpscout.net/conversation/2489486135/193096?folderId=7922220)
ticket:
- Reports > sales > view sales
- Daily reports adding different days to the total
- When you open the sales report and tap on the **Filter** button and select the **Daily** filter option, currently 2 dates are pre-selected. Those are yesterday and today. That then shows the sales for both days. When you tap on the calendar to select a different date, a date range is offered. To only show the sales for 1 day that one date needs to be entered into both those date fields. E.g. to see sales dated 12 December you'd add that date to both date filter fields.
---
### [Re: Notifications](https://secure.helpscout.net/conversation/2483654426/192514?folderId=7922220)
ticket:
- They moved to next purely for the reason so they could move clients without being notified, yet it's still happening
- They are referring to the SMS notification
- Moving bookings/appointments > 'Reset reminders' toggle option. That resends the reminder email and SMS
- Sometimes they just edit the name to move it as the other way is so sensitive and jumps into a different time by a few mins sending move notifications. They want default off setting
- When they change the employee or time on the service settings, no move alert or reminder update is sent. If the entire reservation is moved, turning off the reset reminders/move alert does not send a reminder update or move email
- They have the move reservation option switched off by default, so these are not sending when they move appointments. However, there is not currently a way of turning off the reset reminder toggle by default. This is always on, and must be manually turned off when making changes to a whole reservation. They will find out if we can edit the default for the reminder reset, in the same way we have with the move email. In the meantime, their option of editing the individual service is a good solution, and if you are making changes to the whole reservation, please ensure they untick/untoggle the reset reminder option
- Due to the system sending out reminder updates when an appointment is moved after the initial reminder is sent, we introduced a toggle to turn this off the 'reset reminders' when moving an appointment. They have asked if we can provide the option to have it switched off by default as turning it off every time is apparently not ideal. It's possible to turn off the move email by default so that you have to toggle it on, but the reset reminders option is always on by default
- When an appointment is created on one device, it doesn't show on another device until the appointments page is refreshed. Is there a way to auto refresh the appointments page in that scenario?
---
### [Changing 'receipt' template](https://secure.helpscout.net/conversation/2536523006/198137?folderId=7922220)
ticket:
- They have two issues, first, the customer address is not showing on the receipt template (A4 version). Nor is the information from the sales tax information from the manage > general > sales tax information box. They would also like to change the wording on the receipt template. Is that not possible?
---
### [Re: Assistance Required with Client Date of Birth Entry in Forms]()
ticket:
- Issue with **client forms**. Struggling to enter their date of birth. Individuals are unable to enter their date of birth, whether they try to add it in the day/month/year or month/day/year format.
- To enter their date of birth on a form, customers can click the **Date of Birth** field, which will open a calendar pop-up displaying the current month and year. They can then select the correct month and year using the navigation arrows and choose their birth date on the calendar. If their customers prefer to enter their date of birth manually, they should separate the day, month, and year with forward slashes and enter the day, month, and year in the dd/mm/yyyy format.
- Manual d.o.b. input gives an error message. 
- 'The date cannot be blank'
todo:
- client form: filling in a form, created and managed on the manager, and filled in by customers through the minisite/bookapp
- dob input field in forms
- recreate the bug
---
### 🧑🏻‍💻 [Changing 'receipt' template](https://secure.helpscout.net/conversation/2536523006/198137?folderId=7922220)
ticket:
- The customer address is not showing on the receipt template (A4 version). Nor is the information from the sales tax information from the manage > general > sales tax information box
- For now, they're welcome to add the sales tax info to the **Receipt footer**, which they'll find on the **Manage > Preferences** page
- Noted there are no taxes set up in their account. If they'd like to add a tax they can do that on the **Manage > Point of sale** page
- They would also like to change the wording on the receipt template
- With regards to the wording changes, they can add text in the Receipt header and Receipt footer on the page mentioned above. It's not possible to change any of the other text on printed receipts. They can however change the wording of the receipt email template. That's done by going to the **Manage > Reminders & notifications** page and selecting the **Templates** tab. Then **Edit** the 'Customer Order Email' template.
- When text is added to the 'Sales tax details' field on the Manage > Preferences page, that text is not included in the printed receipts. Is it possible to add that text to the printed receipts?
- Customer's address is not currently included on printed receipts, any interest in adding that?
todo:
- wait for Kristian to add customer address to order api
- add customer address to a4 order receipt
---
### [Re: passes](https://secure.helpscout.net/conversation/2550058849/199778?folderId=7922220)
- They set up a pass for 4x yoga sessions she paid £120 for 4 sessions. The pass now shows as -1 even though the last session is tomorrow. Also, they have pre booked her in until the end of 2024 and all the yoga sessions are showing as paid.
- Tara has their '4x hour personal yoga' pass. When that pass type was originally created, which was on 29 Feb at 8:19pm it was set to provide unlimited uses. Tara's pass was created shortly after that at 8:25pm while the pass was set to provide unlimited uses. At 8:28pm that pass type was edited to only allow 4 uses. Editing a pass type does not apply that change to passes already created for customers. As the pass created for Tara was set to provide unlimited uses, that's what the system is doing. To fix this they can:
1. Create a new pass for Tara. This new pass will include 4 uses as that's how it's currently set. 
2. Open and edit [sale number 653572e04e](https://retreatbrecon.ovatu.app/customer/15687904#/order/24392019) for Tara
3. Add the pass they just created for Tara to the sale and delete the pass that was there (which had the unlimited uses)
4. The sale will then include only the new pass and they can save and close it
5. Delete the old pass for Tara noted in her profile. It'll be the one with the negative 1 balance.
- As the original pass has been deleted, Tara's future appointments should then not be marked as paid with that pass. Tara does not have any ap