# Video Hosting Migration Guide

## Why SharePoint/OneDrive Doesn't Work

SharePoint and OneDrive have several critical limitations for embedding videos:

1. **CORS Blocking**: SharePoint doesn't send `Access-Control-Allow-Origin` headers, blocking cross-origin video playback
2. **Authentication Required**: Sharing links redirect (HTTP 302) to authentication pages
3. **Not Direct URLs**: SharePoint sharing links (`:v:/`, `:f:/`) are web viewer links, not direct video file URLs

**Bottom line**: SharePoint/OneDrive cannot be used for this application without a proxy or conversion service.

---

## Recommended Hosting Alternatives

### Option 1: GitHub Repository (Recommended for Small Files)

**Best for**: Video files under 100MB each

**Setup**:
1. Create a `videos/` folder in your repository
2. Add your video files directly to the folder
3. Commit and push to GitHub
4. Use URLs like: `https://raw.githubusercontent.com/USERNAME/REPO/main/videos/filename.mp4`

**Pros**:
- Simple, no external service needed
- Same repository as your app
- Reliable and fast
- Supports CORS out of the box

**Cons**:
- Not ideal for files over 100MB
- Consumes repository storage

**Example URL**:
```
https://raw.githubusercontent.com/etlerd/studiodisplay/main/videos/background.mp4
```

---

### Option 2: GitHub Git LFS (Large File Storage)

**Best for**: Video files 100MB - 2GB each

**Setup**:
1. Install Git LFS: `git lfs install`
2. Track video files: `git lfs track "*.mp4" "*.mov"`
3. Add and commit as normal
4. URLs are the same as regular GitHub files

**Pros**:
- Handles large files properly
- Same workflow as regular git
- Free tier: 1GB storage, 1GB bandwidth/month

**Cons**:
- Bandwidth limits on free tier
- Requires Git LFS setup

**Pricing**: $5/month for 50GB storage + 50GB bandwidth

---

### Option 3: GitHub Releases

**Best for**: Versioned video assets, larger files

**Setup**:
1. Create a new release in your GitHub repo
2. Attach video files as release assets
3. Use the direct download URL from the release

**Pros**:
- Designed for large binary files
- Doesn't bloat repository history
- Free and unlimited

**Cons**:
- Manual process for each update
- URLs change with each release

**Example**:
1. Go to Releases → Create new release
2. Upload `background.mp4` as an asset
3. Right-click the asset → Copy link address
4. URL format: `https://github.com/USER/REPO/releases/download/TAG/background.mp4`

---

### Option 4: Cloudflare R2 (Best for Large Files & High Traffic)

**Best for**: Multiple large videos, high bandwidth needs

**Setup**:
1. Sign up for Cloudflare account (free)
2. Create an R2 bucket
3. Upload videos via dashboard
4. Enable public access
5. Get public URL for each file

**Pros**:
- 10GB free storage
- **Zero egress fees** (unlimited bandwidth)
- Excellent performance
- CORS-friendly
- Custom domain support

**Cons**:
- Requires separate Cloudflare account
- Slight learning curve

**Free Tier**: 10GB storage, unlimited bandwidth

---

### Option 5: Backblaze B2 + Cloudflare CDN

**Best for**: Cost-effective large file storage

**Setup**:
1. Sign up for Backblaze B2
2. Create a bucket
3. Connect to Cloudflare CDN (free bandwidth)
4. Upload videos
5. Use Cloudflare CDN URL

**Pros**:
- Very cheap ($5/TB/month)
- Free bandwidth via Cloudflare
- Reliable

**Cons**:
- Two services to configure
- Slightly more complex setup

**Free Tier**: 10GB storage, 1GB/day download

---

### Option 6: Self-Hosted Web Server

**Best for**: You already have web hosting

**Setup**:
1. Upload videos to your web server
2. Configure CORS headers in `.htaccess` (Apache) or nginx config:

**Apache (.htaccess)**:
```apache
<IfModule mod_headers.c>
    Header set Access-Control-Allow-Origin "*"
</IfModule>
```

**Nginx**:
```nginx
location /videos/ {
    add_header Access-Control-Allow-Origin *;
}
```

**Pros**:
- Full control
- No third-party dependencies
- Use existing hosting

**Cons**:
- Requires web hosting
- Manual CORS configuration

---

## Quick Comparison Table

| Option | Cost | Max File Size | Bandwidth | Ease of Use | Best For |
|--------|------|---------------|-----------|-------------|----------|
| GitHub Repo | Free | 100MB | Good | ⭐⭐⭐⭐⭐ | Small files |
| Git LFS | $5/mo* | 2GB | 1GB/mo free | ⭐⭐⭐⭐ | Medium files |
| GitHub Releases | Free | No limit | Unlimited | ⭐⭐⭐⭐ | Large files |
| Cloudflare R2 | Free* | No limit | Unlimited | ⭐⭐⭐ | Professional use |
| Backblaze B2 | $5/TB | No limit | Via Cloudflare | ⭐⭐⭐ | Large storage |
| Self-hosted | Varies | Varies | Varies | ⭐⭐ | Existing hosting |

*Free tiers available

---

## Migration Steps from SharePoint

### Step 1: Download Your Videos
1. Go to SharePoint/OneDrive
2. Select your videos
3. Click Download
4. Save to a local folder

### Step 2: Choose a Hosting Provider
Select one from the options above based on your needs.

### Step 3: Upload to New Host
Follow the setup instructions for your chosen provider.

### Step 4: Get Direct URLs
Make sure you have direct URLs to the video files (not web viewer links).

Test your URL by pasting it in a browser - it should **download** or **play directly**, not open a viewer page.

### Step 5: Update Application Settings
1. Open the Podcast Video Player
2. Press F1 for Settings
3. Enter the new video directory URL or base path
4. Enter individual filenames if needed
5. Save settings

---

## URL Format Examples

### Good URLs (Direct video files):
```
✓ https://raw.githubusercontent.com/user/repo/main/videos/video.mp4
✓ https://github.com/user/repo/releases/download/v1.0/video.mp4
✓ https://pub-xxxxx.r2.dev/videos/video.mp4
✓ https://yourdomain.com/videos/video.mp4
✓ https://f000.backblazeb2.com/file/bucket-name/video.mp4
```

### Bad URLs (Won't work):
```
✗ https://iowa-my.sharepoint.com/:v:/g/personal/...  (SharePoint sharing link)
✗ https://onedrive.live.com/...  (OneDrive web viewer)
✗ https://drive.google.com/...  (Google Drive viewer)
✗ https://dropbox.com/s/...  (Dropbox preview link)
```

---

## Testing Your Setup

1. Copy your video URL
2. Paste it directly into browser address bar
3. The video should either:
   - Play directly in the browser, OR
   - Download immediately
4. If it opens a web page with a viewer, it won't work

### Test CORS
Open browser console and run:
```javascript
fetch('YOUR_VIDEO_URL', { method: 'HEAD' })
  .then(r => console.log('CORS OK!', r))
  .catch(e => console.log('CORS BLOCKED', e))
```

---

## Recommended Setup for This Project

**For most users**: Use **GitHub Releases**
- Free and unlimited
- Simple to use
- No bandwidth concerns
- Perfect for this use case

**Quick start**:
1. Go to your repo's Releases page
2. Create a new release (e.g., "v1.0-videos")
3. Drag and drop your video files
4. Publish release
5. Right-click each video → Copy link
6. Use those URLs in the app

---

## Need Help?

If you run into issues:
1. Check the browser console for specific errors
2. Verify your URLs are direct file links (not viewers)
3. Test CORS with the command above
4. Make sure files are publicly accessible (no authentication required)

For more help, open an issue on GitHub!
