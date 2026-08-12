OUTLET METER LOG
================

A single-page web app for logging daily energy and water meter readings
across outlets, with search, filters, Excel export, and reminder emails
for outlets that haven't reported.

This package is self-contained — index.html is the whole app. It loads
its fonts and the Excel-export library from public CDNs, so an internet
connection is needed when the page is open, but there are no separate
asset or image files to manage.


1. PUBLISHING
--------------
For readings to sync between everyone using this tool, index.html needs
to be opened as a published Claude artifact link, not just double-clicked
as a local file. Opening it locally works for trying it out, but data
entered won't be shared with anyone else or saved between visits.

To publish: open the file in Claude, click Publish on the artifact
panel, and share that link with everyone who needs to log readings.
No Claude account is required to use a published link.

Note: a published link is publicly viewable by anyone who has the URL.
There is no login wall — only the owner passcode described below for
deleting data.


2. ADDING A READING
--------------------
Fill in Outlet, Date, Type (Energy or Water), Reading, and an optional
Note, then click Add reading. Status (On-time / Late) is set
automatically based on whether it was logged before 8:00 AM for that
date.


3. SEARCH AND FILTERS
-----------------------
- Search box: text match on outlet name
- Outlet dropdown: exact outlet, populated from the imported outlet list
- Date, Status, Type: narrow the table further

If the table looks empty right after adding data, check that none of
these filters are set to something that excludes the new row — this is
the most common cause of "my entries aren't showing."


4. IMPORTING THE OUTLET LIST
------------------------------
Footer -> "Import outlet list" -> select an .xlsx or .csv file with
these columns:
  - Code            (optional)
  - Location/Outlet (required)
  - Regional manager (optional)
  - Email           (needed for reminder emails)

Re-importing updates existing outlets and adds new ones without
duplicating. Re-import whenever the outlet roster changes.


5. EXPORT TO EXCEL
--------------------
Exports whatever the current filters show as a .xlsx file.


6. OWNER MODE (DELETE PROTECTION)
------------------------------------
Delete buttons and "Clear all readings" are disabled until unlocked
with a passcode via the "Owner mode: off" button. The default passcode
is set in the file itself — search for OWNER_PASSCODE in index.html and
change it to something only you know.


7. REMINDER EMAILS
---------------------
The panel above the entry form shows how many outlets haven't reported
for a chosen date and reading type. "Generate reminder email" builds a
recipient list from the outlets missing that day (using the Email
column from your import) and opens it in your own default mail app to
send. Outlets with no email on file are listed separately so you know
who was skipped. This opens a compose window for you to send manually —
it does not send automatically in the background.


8. LIMITATIONS
-----------------
- Persistent storage is capped at 20MB of text — far more than typical
  readings data needs.
- The published link is public to anyone who has it.
- Reminder emails require manual sending unless a Gmail/Outlook account
  is connected for automatic scheduled sending.
