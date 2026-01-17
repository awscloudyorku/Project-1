# Project 1: Host a Static Website on AWS Amplify

Deploy a static website in minutes using AWS Amplify with GitHub-powered CI/CD. This tutorial guides you from creating a simple site to publishing it on a global CDN with HTTPS.

## What You Will Build
- A static HTML/CSS/JS landing page for the AWS Cloud Club
- Automatic deployments on every push to GitHub
- A public URL served via AWS Amplify (CloudFront + S3)

## Services Used
- AWS Amplify (hosting + CI/CD)
- GitHub (source control)

## Skills You Will Learn
- Static website hosting
- CI/CD basics
- DNS and HTTPS concepts

## Prerequisites
- An AWS account
- A GitHub account
- Git installed
- Node.js and npm installed (optional if you use plain HTML)

## Step 1: Create Your Website
Choose one of these options:

### Option A: Simple HTML Site (fastest)
Create a folder with these files:

`index.html`
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>AWS Cloud Club</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <main class="hero">
      <h1>AWS Cloud Club</h1>
      <p>Learn, build, and deploy in the cloud.</p>
      <a class="cta" href="#">Join the club</a>
    </main>
    <script src="app.js"></script>
  </body>
</html>
```

`style.css`
```css
body {
  margin: 0;
  font-family: system-ui, sans-serif;
  background: #0b1020;
  color: #f5f7ff;
}
.hero {
  min-height: 100vh;
  display: grid;
  place-content: center;
  text-align: center;
  gap: 12px;
}
.cta {
  display: inline-block;
  padding: 10px 18px;
  border-radius: 999px;
  background: #ffb347;
  color: #111;
  text-decoration: none;
  font-weight: 600;
}
```

`app.js`
```js
console.log("AWS Cloud Club site loaded");
```

### Option B: React + Vite (optional)
```bash
npm create vite@latest staticwebsite -- --template react
cd staticwebsite
npm install
npm run dev
```

## Step 2: Create a GitHub Repository
1) Go to https://github.com and create a new public repository named `staticwebsite`.
2) In your project folder, run:

```bash
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:<your-username>/staticwebsite.git
git branch -M main
git push -u origin main
```

## Step 3: Deploy with AWS Amplify
1) Open the AWS Amplify console: https://console.aws.amazon.com/amplify/apps
2) Choose **Create new app**.
3) Select **GitHub** as your repository provider.
4) Authorize GitHub and pick your `staticwebsite` repo and `main` branch.
5) Keep the default build settings and choose **Save and deploy**.

After 2-5 minutes, Amplify will provide a live URL like:
`https://<app-id>.amplifyapp.com`

## Step 4: Update and Redeploy
Edit your site, commit, and push:
```bash
git add .
git commit -m "update landing page"
git push
```
Amplify automatically rebuilds and redeploys.

## Clean Up (Avoid Charges)
1) In the Amplify console, open your app.
2) Go to **App settings** -> **General settings**.
3) Choose **Delete app**.

## Troubleshooting
- **Build fails:** Check build logs in Amplify for missing dependencies.
- **Wrong branch:** Confirm the selected branch in Amplify.
- **No updates:** Make sure you pushed to the connected branch.

## Next Steps
- Add a custom domain with HTTPS
- Create a members-only page
- Add an events section

## Research Report
At the end of the project, submit a short research report about AWS Amplify that is written for people who are brand new to AWS. Keep it very simple: explain what the service is, what it does, and one or two real-world use cases in plain language.
