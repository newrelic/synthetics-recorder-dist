# Frequently Asked Questions

### Is my API key stored locally?

No, the User API key is stored in browser session storage only. It is cleared upon closing the browser.

### Will the extension record all browser activity?

No, the extension only records while record mode is active (which requires the extension to be open). Therefore, record mode should only be active when actively recording steps, otherwise it will continue to record all activity until the 5 minute timeout is reached.

### Will my recorded steps be saved or exported anywhere?

No, recorded steps are stored temporarily in browser session storage, and only exported via clicking `Save` or `Update` for a given monitor in the `Export` panel.