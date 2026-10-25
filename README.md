# myedenred

A full-screen image and sound web app. `image.png` is the final artwork,
without a clock, Wi-Fi, or battery indicators. It fills the app viewport;
the operating system supplies the real status bar. No additional safe-area
padding is added because the artwork already includes space above the greeting.
The app fits its container to `visualViewport.height` (falling back to
`innerHeight`) on resize and when the page is shown again. The image is positioned
inside that container, not fixed to iOS's layout viewport. No safe-area insets are
added to its height, so the complete artwork, including the bottom navigation
labels, stays within the visible area. CSS viewport sizing is the fallback when
JavaScript is unavailable.

On iPhone, open the hosted site in Safari and choose Share > Add to Home Screen.
The translucent status bar allows the artwork to extend behind it; iOS controls
the status-bar icon color.

The service worker bypasses the browser HTTP cache for online requests and
keeps successful responses for offline use. Installation also bypasses the HTTP
cache. The app checks for worker updates on load, when returning to the
foreground, and when reconnecting, then reloads once when a new worker takes
control.

For each release, increment the cache version in `service-worker.js` and keep
the image/audio `?v=` URLs in `index.html` and `APP_FILES` in sync. Deploy these
files together. An already installed older app may need to be closed completely
and reopened online once to receive this update behavior. If the server or CDN
still serves old files, refresh its deployment/cache too; client code cannot
invalidate a server-side cache. If iOS retains old installation settings, remove
the Home Screen app and add it again.
