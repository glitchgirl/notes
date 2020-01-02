HTML web storage 
Before everything had to be stored in cookies*

*cookies are small files on clients machine designed to hold data specific to a client/website and can be accessed by the client or the server. This gives us the ability to tailor pages. Or it can load scripts with data from the cookies Note about GDPR 

Web Storage API
sessionStorage maintains a separate storage area for each given origin that's available for the duration of the page session (as long as the browser is open, including page reloads and restores)
Stores data only for a session, meaning that the data is stored until the browser (or tab) is closed.
Data is never transferred to the server.
Storage limit is larger than a cookie (at most 5MB).
localStorage does the same thing, but persists even when the browser is closed and reopened.
Stores data with no expiration date, and gets cleared only through JavaScript, or clearing the Browser cache / Locally Stored Data.
Storage limit is the maximum amongst the three
