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

1. Open `podcast_video_player-26.html` in a web browser
2. Press **F1** to open settings
3. Configure your video hosting URL (see [HOSTING_GUIDE.md](HOSTING_GUIDE.md))
4. Set your loop video filename
5. Configure timer duration
6. Save settings

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

If you see CORS errors or videos won't load:
1. Check that you're using a supported hosting provider (see [HOSTING_GUIDE.md](HOSTING_GUIDE.md))
2. Verify your URL is a direct link to the video file (not a sharing or viewer link)
3. Test the URL by pasting it directly in your browser - it should download or play immediately
4. Check the browser console for detailed error messages
