# 📊 GitHub Metrics Profile Setup Guide

This guide will help you set up an auto-updating GitHub profile with beautiful SVG infographics using lowlighter/metrics.

## 🚀 Quick Setup (10 minutes)

### Step 1: Create Profile Repository

1. Go to GitHub and create a **new repository**
2. Name it **exactly** `IamMichael23` (same as your username)
3. Make it **Public**
4. ✅ Check "Add a README file"
5. Click "Create repository"

### Step 2: Generate GitHub Token

1. Go to **Settings** → **Developer settings** → **Personal access tokens** → **Tokens (classic)**
2. Click **Generate new token** → **Generate new token (classic)**
3. Name it: `METRICS_TOKEN`
4. Select scopes:
   - ✅ `public_repo` (if you want private repos included, select full `repo`)
   - ✅ `read:user`
   - ✅ `user:email` (optional)
5. Click **Generate token**
6. **COPY THE TOKEN** (you won't see it again!)

### Step 3: Add Token to Repository

1. Go to your `IamMichael23` repository
2. Click **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Name: `METRICS_TOKEN`
5. Value: Paste the token you copied
6. Click **Add secret**

### Step 4: Upload Files

Upload these files to your repository:

```
IamMichael23/
├── README.md                     ← Main profile README
└── .github/
    └── workflows/
        └── metrics.yml           ← GitHub Actions workflow
```

**Option A: Via GitHub Web Interface**
1. In your repository, click **Add file** → **Upload files**
2. Upload `README.md` to the root
3. Create folder `.github/workflows/` and upload `metrics.yml`

**Option B: Via Git Command Line**
```bash
git clone https://github.com/IamMichael23/IamMichael23.git
cd IamMichael23
# Copy the files to this directory
git add .
git commit -m "Add metrics profile"
git push
```

### Step 5: Trigger First Run

1. Go to **Actions** tab in your repository
2. Click on **Metrics** workflow on the left
3. Click **Run workflow** → **Run workflow**
4. Wait 2-5 minutes for completion
5. Refresh your profile page - SVGs should appear!

## 🎨 Customization Options

### Change Update Frequency

Edit `.github/workflows/metrics.yml`:

```yaml
# Daily at midnight
schedule: [{cron: "0 0 * * *"}]

# Every 6 hours
schedule: [{cron: "0 */6 * * *"}]

# Weekly on Sunday
schedule: [{cron: "0 0 * * 0"}]
```

### Customize Featured Repositories

In `metrics.yml`, edit the General GitHub Stats section:

```yaml
plugin_repositories_featured: IamMichael23/your-repo-1, IamMichael23/your-repo-2
```

Replace with your actual repository names.

### Add More Plugins

Visit the [lowlighter/metrics documentation](https://github.com/lowlighter/metrics) to explore 30+ plugins:

**Popular additions:**
- **Stars graph** - Show repository stars over time
- **Topics** - Display your favorite topics
- **Tweets** - Show recent tweets
- **Spotify** - Display recently played music
- **WakaTime** - Coding time tracking
- **Chess.com** - Recent games and stats

### Change Timezone

Edit in `metrics.yml`:

```yaml
config_timezone: America/Toronto    # ← Change this
```

[List of timezones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

## 🔧 Troubleshooting

### SVGs Not Showing

**Problem:** Images show broken links  
**Solution:** 
1. Check Actions tab for errors
2. Verify `METRICS_TOKEN` is set correctly
3. Make sure repository is public
4. Wait for workflow to complete (~3-5 min)

### Token Expired

**Problem:** Workflow fails with authentication error  
**Solution:**
1. Generate new personal access token
2. Update `METRICS_TOKEN` secret
3. Re-run workflow

### Want to Test Locally?

**Problem:** Want to preview before committing  
**Solution:**
Use the [web instance](https://metrics.lecoq.io/) to generate and preview metrics:
1. Go to https://metrics.lecoq.io/
2. Enter your username
3. Configure plugins
4. Click "Generate"
5. Copy the configuration to your workflow

## 📚 Advanced Features

### Multiple Profiles

You can create different metric views:

```yaml
# metrics-dark.svg - Dark theme
- name: Dark Theme Metrics
  uses: lowlighter/metrics@latest
  with:
    filename: metrics-dark.svg
    config_display: large
    config_twemoji: yes
    
# metrics-compact.svg - Compact view
- name: Compact Metrics
  uses: lowlighter/metrics@latest
  with:
    filename: metrics-compact.svg
    config_display: compact
```

Then in README.md:
```markdown
![Metrics](github-metrics.svg)
![Metrics Dark](metrics-dark.svg)
```

### Use Gists Instead

For faster loading, store SVGs in a gist:

```yaml
- uses: lowlighter/metrics@latest
  with:
    filename: metrics.svg
    token: ${{ secrets.METRICS_TOKEN }}
    committer_token: ${{ secrets.GITHUB_TOKEN }}
    committer_gist: YOUR_GIST_ID
```

Then update README:
```markdown
![Metrics](https://gist.githubusercontent.com/IamMichael23/YOUR_GIST_ID/raw/metrics.svg)
```

## 🎯 What You'll Get

After setup, your profile will auto-update with:

✅ **GitHub Stats** - Contributions, commits, PRs, issues  
✅ **Achievements** - Badges for milestones  
✅ **Languages** - Most used programming languages  
✅ **Coding Habits** - When you code, what you code  
✅ **Isometric Calendar** - 3D contribution graph  
✅ **Recent Activity** - Latest GitHub activity  

All updating automatically **every 24 hours**!

## 📖 Resources

- [Metrics Documentation](https://github.com/lowlighter/metrics)
- [All Available Plugins](https://github.com/lowlighter/metrics#-plugins)
- [Example Profiles](https://github.com/lowlighter/metrics#%EF%B8%8F-examples-and-notable-users)
- [Web Preview Tool](https://metrics.lecoq.io/)

## 💡 Tips

1. **Start simple** - Use the default config first, customize later
2. **Check Actions tab** - Monitor workflow runs for errors
3. **Rate limits** - Token can make 5,000 API calls/hour
4. **Private repos** - Need full `repo` scope in token
5. **Performance** - Fewer plugins = faster generation

---

**Ready to go?** Follow Steps 1-5 above and you'll have a professional auto-updating GitHub profile in 10 minutes! 🚀
