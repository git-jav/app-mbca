# myedenred

A full-screen image and sound web app. `image.png` is the final artwork,
without a clock, Wi-Fi, or battery indicators. It fills the app viewport;
the operating system supplies the real status bar. No additional safe-area
padding is added because the artwork already includes space above the greeting.
In iOS Home Screen mode with a translucent status bar, the image compensates
for the top safe-area height that iOS removes from the app viewport. This keeps
the artwork at full-screen height instead of leaving extra white space below it.

On iPhone, open the hosted site in Safari and choose Share > Add to Home Screen.
The translucent status bar allows the artwork to extend behind it; iOS controls
the status-bar icon color.

After deploying an update, open the app online to refresh its offline cache,
then close and reopen it. If iOS retains old installation settings, remove the
Home Screen app and add it again.
