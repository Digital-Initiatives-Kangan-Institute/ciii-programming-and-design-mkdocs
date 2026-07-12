# Deploy Your Project

## Take Your Project Live

!!! abstract "Instructions"
    Prepare your project for deployment, deploy it to a platform, and test the live site.

    Your task:

    - Run `npm run build` and fix any build errors
    - Set environment variables if your app uses them
    - Deploy to Vercel, Netlify, Cloudflare, or an FTP server
    - Test the live site — check every page and feature
    - Write a short release note describing what was deployed

    If deployment is not possible, document the steps you would take and any errors you encountered.

    Push your project files and release note to GitHub. Include the live link if available.

??? code "click to expand"

    ```bash
    # Check for build errors
    npm run build

    # If using Vercel CLI
    npm install -g vercel
    vercel

    # If using Netlify CLI
    npm install -g netlify-cli
    netlify deploy
    ```

    ```markdown
    ## Release Notes

    - What features are deployed
    - Known issues (if any)
    - Live URL
    ```

??? hint "Hint - Click to expand"
    Before deploying, make sure `npm run build` succeeds with no errors. Check that you have not committed any `.env` files with secrets. If build errors appear, read the error message carefully — usually it points to the exact file and line causing the problem. After deployment, test on a different device or browser to make sure everything loads correctly.
