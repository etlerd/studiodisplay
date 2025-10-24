# studiodisplay
A simple in-studio display for showing videos, images, sounds, and other media for podcasting co-hosts.

## Important: Media Hosting

**SharePoint/OneDrive URLs are NOT supported** due to CORS restrictions and authentication requirements.

For supported hosting options, see **[HOSTING_GUIDE.md](HOSTING_GUIDE.md)**

**Quick recommendations:**
- **GitHub Releases** (recommended) - Free, unlimited, easy to use, supports flexible filenames
- **GitHub raw URLs** - For files under 100MB
- **Cloudflare R2** - For large files and high bandwidth needs
- **Self-hosted** - Any web server with CORS enabled

See the [Hosting Guide](HOSTING_GUIDE.md) for detailed setup instructions.

## Setup

1. **Upload your media** to GitHub Releases (see [HOSTING_GUIDE.md](HOSTING_GUIDE.md) for details)
   - Upload your loop video (e.g., `background.mp4`)
   - Upload numbered files if needed (e.g., `01.png`, `02.mp4`, `03-applause.m4a`, etc.)

2. **Open the app** - Go to `https://YOUR_USERNAME.github.io/studiodisplay/podcast_video_player-26.html`

3. **Configure settings** (Press **F1**):
   - **Media Directory**: Base path ending with `/` (e.g., `https://github.com/user/repo/releases/download/TAG/`)
   - **Loop Video Filename**: Just the filename (e.g., `background.mp4`)
   - **Timer Duration**: Default countdown time (e.g., `20:00`)
   - Click **Save**

4. **Test it**:
   - Press **L** to play loop video
   - Press **1-8** for numbered videos/images
   - Press **Numpad 1-8** for sound effects

> **💡 Tip**: Use base path + filename (not full URL) so numbered files work when you press keys

## Media Storage

### Where Media is Stored

Media files (videos, images, and sounds) are **NOT stored in this repository**. Instead, they are hosted externally on:
- **GitHub Releases** (recommended - free, unlimited bandwidth, flexible filenames)
- **GitHub raw URLs** (for files under 100MB)
- **Cloudflare R2** (for large files and high bandwidth needs)
- **Self-hosted servers** (any web server with CORS enabled)
- **Local files** (using `file://` URLs)

See [HOSTING_GUIDE.md](HOSTING_GUIDE.md) for detailed setup instructions for each hosting option.

### Configuration Storage

Your media configuration (media directory path, loop video filename, timer settings) is saved in your **browser's localStorage**. This means:
- Settings are saved per-browser and per-device
- Settings persist across page reloads
- Each browser/device needs to be configured separately
- Clearing browser data will reset settings

### How to Change/Update Media Files

#### Updating Existing Media Files

1. **Upload new files** to your hosting location (e.g., GitHub Releases)
   - Use the same filenames to replace old files, OR
   - Use new filenames and update settings (see below)

2. **If using same filenames**: Your app will automatically load the new files on next reload

3. **If using new filenames**:
   - Press **F1** to open settings
   - Update the **Loop Video Filename** field with the new filename
   - Click **Save**

#### Adding New Numbered Files (1-8)

**For GitHub Releases (Flexible Naming):**
- **Videos**: `01-intro.mp4`, `02-sermon-clip.mov`, etc.
- **Images**: `03-announcement.png`, `04-worship-lyrics.jpg`, etc.
- **Sounds**: `05-applause.mp3`, `06-ding.m4a`, `07-sad-trombone.wav`, etc.

**For Other Hosting (Exact Names):**
- Use exact numbered filenames: `01.mp4`, `02.png`, `03.mp3`, etc.

**Supported Formats:**
- Videos: `.mp4`, `.mov`, `.avi`, `.webm`
- Images: `.jpg`, `.png`, `.gif`, `.jpeg`
- Sounds: `.mp3`, `.wav`, `.m4a`

**Setup:**
1. Upload to same location as your loop video (same GitHub Release, same directory, etc.)
2. **No configuration needed**: Press keys to access them instantly
   - Regular keys **1-8** → Play videos/images
   - Numpad keys **1-8** → Play sounds (overlay on current media)

#### Changing Hosting Location

To move your media to a different hosting provider:

1. **Upload files** to new hosting location
2. Press **F1** to open settings
3. Update **Media Directory Base Path** with new URL
4. Update **Loop Video Filename** if needed
5. Click **Save**
6. Press **L** to test the loop video

## Keyboard Shortcuts

- **F1** - Open settings
- **SPACE** - Start/stop timer
- **R** - Reset timer
- **L** - Return to loop video
- **1-8** (regular keys) - Play numbered videos/images (01-08)
- **Numpad 1-8** - Play sound effects (overlay on current media)
- **F11** - Fullscreen
- **ESC** - Exit fullscreen or close settings

## Features

- Loop video playback
- Countdown timer with visual and audio alerts
- Quick access to numbered media files (videos, images, and sounds)
- Sound effects that play over current media without interruption
- Flexible filename support for GitHub Releases (descriptive names)
- Multiple simultaneous sound playback
- Fullscreen support
- Persistent settings (saved in browser)

## Troubleshooting

### Videos won't load
1. **Check hosting provider**: SharePoint/OneDrive/Google Drive/Dropbox are NOT supported (see [HOSTING_GUIDE.md](HOSTING_GUIDE.md))
2. **Use GitHub Releases**: Recommended - free, unlimited, works perfectly
3. **Verify URL format**: Should be a direct link, not a sharing/viewer link
4. **Test the URL**: Paste it in your browser - it should download or play immediately, not open a web page

### Numbered files (1-8 keys) don't work
1. **Use base path + filename approach**: Don't use full URL in Media Directory
2. **Correct format**:
   - Media Directory: `https://github.com/user/repo/releases/download/TAG/` (ends with `/`)
   - Loop Video Filename: `background.mp4` (just the filename)
3. **Upload numbered files**: Upload `01.png`, `02.mp4`, `03-applause.m4a`, etc. to the same location
4. **For GitHub Releases**: Use descriptive names like `01-intro.mp4`, `02-announcement.png`, `03-applause.mp3`

### Image won't return to loop video
- This was fixed in recent updates. Make sure you have the latest version from GitHub Pages.

### More help
- Check the browser console (F12) for detailed error messages
- See [HOSTING_GUIDE.md](HOSTING_GUIDE.md) for complete setup instructions
