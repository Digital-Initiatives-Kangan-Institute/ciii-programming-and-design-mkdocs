# Deploying Your Project

Deployment is the process of putting your web application on the internet so others can access it. This page covers preparing your project, choosing a platform, and releasing it.

---

## Preparing for Deployment

Before deploying, verify your project is ready:

1. Run the build command to check for errors:

```bash
npm run build
```

2. Fix any build errors that appear
3. Test your app locally one final time
4. Check that all pages and features work

---

## Environment Variables

If your app uses API keys or secrets, set them as environment variables:

```bash
# .env.local (local development)
NEXT_PUBLIC_API_URL=https://api.example.com
```

On your deployment platform, add these same variables in the project settings. Never commit `.env` files to GitHub.

---

## Deployment Platforms

### Vercel

The company behind Next.js. Offers the simplest Next.js deployment:

1. Connect your GitHub repository
2. Vercel detects Next.js automatically
3. Every push to your main branch triggers a new deployment
4. Provides a live URL like `https://my-app.vercel.app`

### Netlify

A popular alternative with similar features:

1. Connect your GitHub repository
2. Set the build command: `npm run build`
3. Set the publish directory: `.next`
4. Deploys on every push

### Cloudflare Pages

Works well with static exports and edge functions:

1. Connect your Git repository
2. Configure the build settings
3. Deploys globally on Cloudflare's network

### FTP Server

For static sites, you can upload files directly via FTP. This is less common for Next.js apps but works for simple HTML/CSS/JS projects.

---

## Testing the Live Site

After deployment:

1. Visit the live URL
2. Test every page and feature
3. Check that images and assets load correctly
4. Test on mobile and different browsers
5. Verify that API calls work on the live domain

---

## Release Notes

When you deploy, document what changed. A short release note includes:

- What features are included
- Any known issues
- The live link to the deployed site

---

## Summary

- Run `npm run build` to verify your project before deploying
- Set environment variables on your deployment platform, not in your code
- Vercel provides the simplest Next.js deployment
- Test thoroughly on the live URL after deploying
- Document your release with a short note and live link
