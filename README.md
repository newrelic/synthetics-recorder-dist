# New Relic Synthetics Recorder

A Chrome extension for recording browser interactions and creating associated New Relic Synthetics Step Monitors.

## Features

- **Record Interactions**: Capture clicks, form inputs, navigation, and more
- **Assertion Mode**: Add validation steps to verify page content
- **Live Preview**: See recorded steps in real-time as you interact
- **Monitor Type Selection**: Record as either a Step Monitor or a Scripted Browser monitor
- **Export to New Relic**: Create Step Monitor or Scripted Browser monitors directly via NerdGraph API
- **Edit Steps & Configuration**: Modify, reorder, or delete recorded steps, or modify monitor configuration.
- **Add Steps**: Manually add steps without re-recording from the start.
- **Import Monitors**: Fetch existing monitors across accessible accounts for editing, with monitor-type filtering in the Import tab
- **Replay**: Replay steps to validate or troubleshoot steps 

## Installation

1. Download the latest [release](https://github.com/newrelic/synthetics-recorder-dist/releases)
2. Unzip the extension
3. Load in Chrome:
   - Open `chrome://extensions`
   - Enable "Developer mode"
   - Click "Load unpacked"
   - Select the unzipped directory

## Usage

### Recording a Monitor

1. Click the extension icon in Chrome toolbar
2. Enter the URL you want to record, choose `Step Monitor` or `Scripted Browser`, and click "Start Recording"
3. Interact with the website - your actions are captured automatically for up to 5 minutes per recording session
4. Click `Stop Recording` when finished

> Recording sessions automatically stop after 5 minutes from the moment recording starts, even if the session is paused. When that happens, the Record tab will display a timeout message.

### Adding Assertions

1. While recording, click `Add Assertion` in the Side Panel
2. Click on any element to create a text assertion
3. Choose assertion type (text present, element visible, etc.)
4. Disable assertion mode in the extension to revert back to recording mode (or press `ESC`)

### Exporting to New Relic

1. Go to Settings tab and enter your New Relic [User key](https://docs.newrelic.com/docs/apis/intro-apis/new-relic-api-keys/)
2. Navigate to Export tab
3. Review the selected monitor type, then choose the destination account and configure monitor name, frequency, browsers, device, locations, etc
4. Click `Save to New Relic` when finished and then scroll back to the top to view a link to the created monitor.


### Importing from New Relic

1. Go to Settings tab and enter your New Relic [User key](https://docs.newrelic.com/docs/apis/intro-apis/new-relic-api-keys/)
2. Navigate to Import tab, choose the monitor type you want to browse, and wait for the first page of monitors across accessible accounts to load automatically
3. Use the search box to narrow the list by name, or page forward to load more results when available
3. Select a monitor to navigate to the monitor page in New Relic or select `Edit` to load and edit that monitor's steps or configuration.

Scripted Browser imports are limited to recorder-generated monitors that include the extension's `createdby: nr-synthetics-recorder` tag and embedded recorder metadata. This keeps scripted imports deterministic and editable in the extension.

### Updating a Monitor's Steps/Config

After exporting a monitor to New Relic, the extension will switch to Edit mode, where you can modify steps or monitor configuration. Alternatively, clicking edit on any imported monitor via `Import` tab will load the monitor's current steps/config. Edit any desired steps/configuration settings, and then click `Update monitor` on the `Export` tab. 

To exit edit mode, select `Cancel` on the edit panel at the top of the `Export` tab.

## Additional Notes & Tips

- It is recommended to assert elements/text after any clicks or interactions that trigger additional page loads or DOM changes. This adds a layer of validation to ensure elements that will be interacted with are loaded/available before interacting directly with them.
- Your New Relic API key is kept only for the current browser session. Using `Clear` in the Settings tab removes it immediately from both the side panel state and the active background session.
- Password fields are determined by any HTML `<input>` element that has a `type="password"` attribute. When recorded steps match those elements, `{{SECURE_CREDENTIAL}}` is stored as the placeholder (instead of the input password text). Therefore, prior to exporting, it is expected that this placeholder is replaced by an existing [New Relic secure credential](https://docs.newrelic.com/docs/synthetics/synthetic-monitoring/using-monitors/store-secure-credentials-scripted-browsers-api-tests/) that holds the value within New Relic (i.e: `$secure.PASSWORD`).
- Element hovers are captured by hovering over a desired element for 2 seconds.
- Scrolls are captured after a 2 second wait (to ensure all scrolling is complete).
- A single recording mode lasts a maximum of 5 minutes after recording is started.
- Recording in Chrome's Incognito mode is recommended, to more closely mirror Synthetics behavior of executing monitors in browser with no cache.

## Support

<a href="https://github.com/newrelic?q=nrlabs-viz&amp;type=all&amp;language=&amp;sort="><img src="https://user-images.githubusercontent.com/1786630/214122263-7a5795f6-f4e3-4aa0-b3f5-2f27aff16098.png" height=50 /></a>

This project is actively maintained by the New Relic Labs team. Connect with us directly by [creating issues](../../issues) or [asking questions in the discussions section](../../discussions) of this repo.

We also encourage you to bring your experiences and questions to the [Explorers Hub](https://discuss.newrelic.com) where our community members collaborate on solutions and new ideas.

New Relic has open-sourced this project, which is provided AS-IS WITHOUT WARRANTY OR DEDICATED SUPPORT.

## Security

As noted in our [security policy](https://github.com/newrelic/nr-labs-pages/security/policy), New Relic is committed to the privacy and security of our customers and their data. We believe that providing coordinated disclosure by security researchers and engaging with the security community are important means to achieve our security goals.

If you believe you have found a security vulnerability in this project or any of New Relic's products or websites, we welcome and greatly appreciate you reporting it to New Relic through [HackerOne](https://hackerone.com/newrelic).

## License

This project is distributed under the [New Relic Software License](LICENSE).
