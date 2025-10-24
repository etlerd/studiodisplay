# studiodisplay
A simple in-studio display for showing videos, images, and other media for podcasting co-hosts.

## Important: Video Hosting

**SharePoint/OneDrive URLs are NOT supported** due to CORS restrictions and authentication requirements.

For supported hosting options, see **[HOSTING_GUIDE.md](HOSTING_GUIDE.md)**

**Quick recommendations:**
- **GitHub Releases** (recommended) - Free, unlimited, easy to use
- **GitHub raw URLs** - For files under 100MB
- **Cloudflare R2** - For large files and high bandwidth needs
- **Self-hosted** - Any web server with CORS enabled

See the [Hosting Guide](HOSTING_GUIDE.md) for detailed setup instructions.

## Setup

1. **Upload your videos** to GitHub Releases (see [HOSTING_GUIDE.md](HOSTING_GUIDE.md) for details)
   - Upload your loop video (e.g., `background.mp4`)
   - Upload numbered files if needed (e.g., `01.png`, `02.mp4`, etc.)

2. **Open the app** - Go to `https://YOUR_USERNAME.github.io/studiodisplay/podcast_video_player-26.html`

3. **Configure settings** (Press **F1**):
   - **Video Directory**: Base path ending with `/` (e.g., `https://github.com/user/repo/releases/download/TAG/`)
   - **Loop Video Filename**: Just the filename (e.g., `background.mp4`)
   - **Timer Duration**: Default countdown time (e.g., `20:00`)
   - Click **Save**

4. **Test it**: Press **L** to play loop video, **1-8** for numbered files

> **💡 Tip**: Use base path + filename (not full URL) so numbered files work when you press 1-8

## Keyboard Shortcuts

- **F1** - Open settings
- **SPACE** - Start/stop timer
- **R** - Reset timer
- **L** - Return to loop video
- **1-8** - Play numbered videos/images (01-08)
- **F11** - Fullscreen
- **ESC** - Exit fullscreen or close settings

## Features

- Loop video playback
- Countdown timer with visual and audio alerts
- Quick access to numbered media files (videos and images)
- Fullscreen support
- Persistent settings (saved in browser)

## Troubleshooting

### Videos won't load
1. **Check hosting provider**: SharePoint/OneDrive/Google Drive/Dropbox are NOT supported (see [HOSTING_GUIDE.md](HOSTING_GUIDE.md))
2. **Use GitHub Releases**: Recommended - free, unlimited, works perfectly
3. **Verify URL format**: Should be a direct link, not a sharing/viewer link
4. **Test the URL**: Paste it in your browser - it should download or play immediately, not open a web page

### Numbered files (1-8 keys) don't work
1. **Use base path + filename approach**: Don't use full URL in Video Directory
2. **Correct format**:
   - Video Directory: `https://github.com/user/repo/releases/download/TAG/` (ends with `/`)
   - Loop Video Filename: `background.mp4` (just the filename)
3. **Upload numbered files**: Upload `01.png`, `02.mp4`, etc. to the same location

### Image won't return to loop video
- This was fixed in recent updates. Make sure you have the latest version from GitHub Pages.

### More help
- Check the browser console (F12) for detailed error messages
- See [HOSTING_GUIDE.md](HOSTING_GUIDE.md) for complete setup instructions
