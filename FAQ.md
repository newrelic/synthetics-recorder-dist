# Frequently Asked Questions

### Does the extension use browser local storage for storing sensitive data?

No, the extension only uses browser session storage for api keys and recording state (steps, etc) which is cleared when closing the browser. The only data stored in local storage are the user's region (US or EU) and debug mode toggle (enabled/disabled).

### Will the extension record all browser activity?

Yes, but the extension only records while record mode is active (which requires the extension to be open). Therefore, record mode should only be active when actively recording steps, otherwise it will continue to record all activity until the 5 minute timeout is reached.

### What happens if I close the browser or extension while recording or if I have unsaved recorded steps?

Recording will cease and any steps recorded will be discarded.

### Why can I only edit certain scripted monitors imported?

Since scripted monitors are highly flexible in design/code structure, only monitors that were created by this extension are editable (denoted by a tag `createdBy: nr-synthetics-recorder`). If you want to create scripts outside of this extension, the same script format must be followed as those scripts created by this extension (including specific metadata).