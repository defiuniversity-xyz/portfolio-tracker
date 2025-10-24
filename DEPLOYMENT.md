# 🚀 Deployment Guide

This guide covers deploying the Portfolio Tracker to Firebase Hosting (Google Cloud Platform).

## Prerequisites

- Node.js and npm installed
- Firebase CLI installed
- Google account for Firebase
- Git installed

## Firebase Hosting Setup

### Step 1: Install Firebase CLI

If you haven't already installed the Firebase CLI:

```bash
npm install -g firebase-tools
```

Verify installation:
```bash
firebase --version
```

### Step 2: Login to Firebase

```bash
firebase login
```

This will:
1. Open your browser
2. Ask you to sign in with your Google account
3. Request permissions for Firebase CLI
4. Confirm successful authentication

### Step 3: Create or Select Firebase Project

You have two options:

#### Option A: Use Existing Project

```bash
firebase use --add
```

This will:
1. List all your Firebase projects
2. Let you select one
3. Create a `.firebaserc` file with the project ID

#### Option B: Create New Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project"
3. Enter project name (e.g., "portfolio-tracker")
4. Optional: Enable Google Analytics
5. Wait for project creation
6. Then run: `firebase use --add` and select your new project

### Step 4: Configure Firebase Project

The `firebase.json` file is already configured. It specifies:
- Public directory: `.` (current directory)
- Single-page app rewrites to `index.html`
- Files to ignore during deployment
- Cache control headers for optimization

If you need to modify settings:
```bash
firebase init hosting
```

**Important**: When asked "Do you want to overwrite index.html?", answer **NO**.

### Step 5: Test Locally

Before deploying, test your application locally:

```bash
firebase serve
```

This will:
- Start a local server (usually on port 5000)
- Serve your app at `http://localhost:5000`
- Show you exactly what will be deployed

**Testing checklist:**
- [ ] Page loads correctly
- [ ] Can add/edit assets
- [ ] Calculations work properly
- [ ] Save/load from localStorage works
- [ ] CSV export functions
- [ ] Ladder calculator works
- [ ] Risk analysis displays

### Step 6: Deploy to Firebase

Once local testing passes:

```bash
firebase deploy
```

Or deploy only hosting (if you have other Firebase services):
```bash
firebase deploy --only hosting
```

**Deployment output will show:**
- Upload progress
- Hosting URL: `https://<project-id>.web.app`
- Alternative URL: `https://<project-id>.firebaseapp.com`

### Step 7: Verify Deployment

1. Open the hosting URL in your browser
2. Test all functionality
3. Check browser console for errors
4. Verify localStorage persistence works

## Custom Domain Setup (Optional)

### Add Custom Domain

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select your project
3. Navigate to **Hosting** → **Add custom domain**
4. Enter your domain name
5. Follow verification steps

### DNS Configuration

Firebase will provide DNS records to add. Typically:

**For root domain (example.com):**
```
Type: A
Name: @
Value: (Firebase IP addresses provided)
```

**For subdomain (www.example.com):**
```
Type: CNAME
Name: www
Value: <project-id>.web.app
```

### SSL Certificate

- Automatically provisioned by Firebase
- Usually takes 24-48 hours after DNS propagation
- Free and auto-renewing

## GitHub Actions Auto-Deployment (Optional)

### Setup Automated Deployment

To automatically deploy on every push to main:

#### 1. Generate Firebase Token

```bash
firebase login:ci
```

Copy the token that's generated.

#### 2. Add Token to GitHub Secrets

1. Go to your GitHub repository
2. Settings → Secrets and variables → Actions
3. Click "New repository secret"
4. Name: `FIREBASE_TOKEN`
5. Value: (paste the token)
6. Click "Add secret"

#### 3. Get Firebase Service Account

```bash
firebase init hosting:github
```

Follow the prompts to:
- Link to GitHub repository
- Set up deploy workflow
- Choose deploy on merge to main

This creates `.github/workflows/firebase-hosting-pull-request.yml` and `.github/workflows/firebase-hosting-merge.yml`

#### 4. Commit and Push Workflow Files

```bash
git add .github/
git commit -m "Add GitHub Actions deployment workflow"
git push origin main
```

Now every push to `main` will automatically deploy!

## Environment Variables (If Needed)

If you add features requiring API keys:

### Local Development

Create `.env.local`:
```
VITE_API_KEY=your-api-key
VITE_API_URL=https://api.example.com
```

### Firebase Hosting

Use Firebase Environment Config:

```bash
firebase functions:config:set api.key="your-api-key"
firebase functions:config:set api.url="https://api.example.com"
```

Retrieve config:
```bash
firebase functions:config:get
```

## Rollback Deployment

### View Deployment History

```bash
firebase hosting:channel:list
```

### Rollback to Previous Version

1. Go to Firebase Console
2. Hosting → Release history
3. Click on previous version
4. Click "Rollback"

Or via CLI:
```bash
firebase hosting:rollback
```

## Monitoring & Analytics

### View Hosting Metrics

Firebase Console → Hosting → Usage tab shows:
- Total requests
- Data transferred
- Storage used

### Add Google Analytics (Optional)

In `index.html`, add before `</head>`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

## Troubleshooting

### Issue: "Permission denied" during deployment

**Solution:**
```bash
firebase logout
firebase login
```

### Issue: Wrong project being deployed to

**Solution:**
```bash
firebase use --add
# Select correct project
firebase projects:list  # Verify
```

### Issue: 404 errors after deployment

**Solution:** Check `firebase.json` rewrites are configured correctly:
```json
"rewrites": [
  {
    "source": "**",
    "destination": "/index.html"
  }
]
```

### Issue: Old version still showing

**Solution:**
```bash
# Hard refresh browser (Ctrl+Shift+R or Cmd+Shift+R)
# Or clear browser cache
# Or deploy with cache bust:
firebase deploy --force
```

### Issue: Deployment takes too long

**Solution:**
```bash
# Deploy only changed files
firebase deploy --only hosting

# Check .gitignore and firebase.json ignore patterns
```

## Cost Monitoring

### Firebase Free Tier (Spark Plan)

- **Storage:** 10 GB
- **Transfer:** 360 MB/day
- **Custom domain:** Yes
- **SSL certificates:** Yes

This application should stay well within free tier limits.

### Monitor Usage

1. Firebase Console → Usage and billing
2. Set up budget alerts
3. Monitor daily/monthly usage

### Upgrade if Needed

If you exceed free tier:
- **Blaze Plan:** Pay-as-you-go
- First 10 GB storage: Free
- First 360 MB/day transfer: Free
- Beyond that: Very low cost

## Best Practices

### Before Each Deployment

```bash
# 1. Test locally
firebase serve

# 2. Check git status
git status

# 3. Ensure all changes committed
git commit -am "Description of changes"

# 4. Deploy
firebase deploy

# 5. Test production
# Open hosting URL and verify
```

### Security Rules

Since this is a static site with no database, no security rules needed. All data is client-side only.

### Performance Optimization

Already configured in `firebase.json`:
- Cache-Control headers
- Single-page app optimization
- Gzip compression (automatic)

## Quick Reference Commands

```bash
# Login
firebase login

# Select project
firebase use <project-id>

# Test locally
firebase serve

# Deploy
firebase deploy

# View logs
firebase hosting:channel:list

# Open project in console
firebase open hosting

# Check current project
firebase projects:list
```

## Support

- [Firebase Documentation](https://firebase.google.com/docs/hosting)
- [Firebase Status](https://status.firebase.google.com/)
- [Firebase Support](https://firebase.google.com/support)
- [GitHub Issues](https://github.com/defiuniversity-xyz/portfolio-tracker/issues)

---

**Next Steps:**
1. Follow Step 2 to login to Firebase
2. Follow Step 3 to create/select a project
3. Follow Step 5 to test locally
4. Follow Step 6 to deploy!
