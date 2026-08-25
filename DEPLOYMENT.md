# Mixpanel Master Dashboard - Deployment Guide

## Quick Start - Deploy to Vercel in 5 Minutes

### Step 1: Download the Files
1. Download all files from this folder
2. Create a new folder on your computer: `mixpanel-dashboard`
3. Copy all files into that folder (keep the folder structure)

### Step 2: Push to GitHub
1. Go to GitHub.com (create account if needed)
2. Click "New" → Create a new repository
   - Name: `mixpanel-dashboard`
   - Description: "Live Mixpanel Analytics Dashboard"
   - Public or Private (your choice)
   - Click "Create repository"

3. Open Terminal/Command Prompt
4. Navigate to your `mixpanel-dashboard` folder:
   ```
   cd path/to/mixpanel-dashboard
   ```

5. Run these commands:
   ```
   git init
   git add .
   git commit -m "Initial commit: Mixpanel Dashboard"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/mixpanel-dashboard.git
   git push -u origin main
   ```
   (Replace YOUR_USERNAME with your GitHub username)

### Step 3: Deploy to Vercel
1. Go to Vercel.com
2. Click "New Project"
3. Click "Import Git Repository"
4. Paste your GitHub repository URL:
   ```
   https://github.com/YOUR_USERNAME/mixpanel-dashboard.git
   ```
5. Click "Import"
6. Click "Deploy"
   - No environment variables needed (API secrets are in code)
7. Wait 2-3 minutes for deployment
8. Click "Visit" to see your live dashboard!

### Step 4: Share the Link
Your dashboard URL will look like:
```
https://mixpanel-dashboard.vercel.app
```

Share this link with stakeholders - anyone can access it!

---

## What's Included

### Frontend (public/index.html)
- ✅ Bright white design (no dark background)
- ✅ Sidebar navigation for all 9 projects
- ✅ Overview dashboard
- ✅ Detailed drill-down per project
- ✅ Date range filters (7/30/90 days)
- ✅ Live indicator (green dot)
- ✅ Real-time charts

### Backend (api/data.js)
- ✅ Connects to Mixpanel API
- ✅ Uses your 9 API secrets
- ✅ Fetches real data:
  - DAU, MAU, WAU
  - New signups (Football Mania: Traditional only)
  - Stickiness (DAU/MAU %)
  - Churn Rate
  - Retention cohorts (D0, D1, D7, D30)

### Configuration
- ✅ vercel.json - Tells Vercel how to run the app
- ✅ package.json - Dependencies (axios, cors, dotenv, express)
- ✅ .gitignore - Protects sensitive files

---

## API Secrets Used

Each project uses its Scoped API Secret:

1. Football Mania Web: `f776707e8355be817ac1e68235f9671d`
2. Football Mania App: `029db48c8f29d57c1a521a50d44edfcc`
3. 2CanPlay Web: `417eccf672844be8690f9562ed1e2b05`
4. 2CanPlay Mobile: `ec53c13460046e4d052f03ff32712684`
5. Spin-N-Win: `07633715564037569f193e6f6826a8b8`
6. Wheel of Fortune: `321d691ec2ad503bfda3c9bb8744e366`
7. Edumillionaire: `4cd840e26dbf1e54e861f95284eda27c`
8. Fifty-Fifty: `a746055c086050d409bd837a21e887f1`
9. Football Frenzy: `66bd49b335376a3e7cae8a536e0d7134`

---

## Event Mapping

Each project uses its correct event for WAU calculation:

- **Football Mania Web/App**: Quiz Initiated
- **2CanPlay Web**: Game Initiated
- **2CanPlay Mobile**: start_game
- **Spin-N-Win**: Game Initiated
- **Wheel of Fortune**: Game Initiated
- **Edumillionaire**: start_game
- **Fifty-Fifty**: start_game
- **Football Frenzy**: Quiz Initiated

---

## How It Works

1. **User Opens Dashboard**
   - Loads `public/index.html` in browser
   
2. **Dashboard Requests Data**
   - Calls `/api/data?daysBack=30`
   
3. **Backend Fetches from Mixpanel**
   - Uses your API secrets
   - Queries last 7/30/90 days
   - Calculates all metrics
   
4. **Data Displayed in Real-Time**
   - Charts render
   - Users can click projects
   - Date filters work
   - Auto-refreshes every 30 seconds

---

## Customization

### Change Colors
Edit `public/index.html` - search for `#2a78d6` (blue):
```html
border-color: #2a78d6;  /* Change this hex code */
```

### Change Refresh Rate
Edit `public/index.html` - search for `setInterval`:
```javascript
setInterval(refreshData, 30000); // 30 seconds - change to 60000 for 1 minute
```

### Add More Metrics
Edit `api/data.js` - add new fields to the return object:
```javascript
return {
    dau: baseDAU,
    mau: baseMAU,
    // Add new metric here:
    myNewMetric: someValue,
}
```

---

## Troubleshooting

### "Loading data..." stuck
- Check browser console (F12 → Console)
- Check if `/api/data` is responding
- Verify all API secrets are correct

### Data seems wrong
- Verify signup event names match Mixpanel exactly
- Check date range is correct
- Mixpanel has ~5-10 min data delay

### Deployment fails
- Make sure all files are in GitHub
- Check `package.json` has all dependencies
- Verify no special characters in file names

---

## Next Steps

1. ✅ Deploy to Vercel
2. ✅ Get live URL
3. ✅ Share with stakeholders
4. ✅ Set bookmark/remind team
5. ✅ Monitor dashboarddaily

---

## Support

For issues:
1. Check browser console (F12)
2. Check Vercel deployment logs
3. Verify Mixpanel tokens are correct
4. Ensure date range has data

---

**Your dashboard is now live and shareable!** 🎉
