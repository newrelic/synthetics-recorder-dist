# Frequently Asked Questions

### Is my API key stored locally to disk?

No, the User API key is stored in browser session storage only. It is cleared upon closing the browser.

### Will the extension record all browser activity?

Yes, but the extension only records while record mode is active (which requires the extension to be open). Therefore, record mode should only be active when actively recording steps, otherwise it will continue to record all activity until the 5 minute timeout is reached.

### Will my recorded steps be saved or exported anywhere automatically?

No, recorded steps are stored temporarily in browser session storage, and only exported via clicking `Save` or `Update` for a given monitor in the `Export` panel. They are cleared when closing the extension or the browser.

### Why can I only edit certain scripted monitors imported?

Since scripted monitors are highly flexible in design/code structure, only monitors that were created by this extension are editable (denoted by a tag `createdBy: nr-synthetics-recorder`). If you want to create scripts outside of this extension, the same script format must be followed as those scripts created by this extension (including specific metadata).