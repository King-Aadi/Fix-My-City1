# Deployment Guide for FixMyCity

Your "Fix My City" application is built with **Vite + React + TypeScript**. It is fully static-site compatible, meaning you can host it for free on platforms like Vercel, Netlify, or GitHub Pages.

## Prerequisites

1.  **Google Maps API Key**: Ensure you have a valid key in your `.env` file or environment variables settings on the host.
    ```env
    VITE_GOOGLE_MAPS_API_KEY=your_key_here
    ```

## Option 1: Vercel (Recommended - Easiest)

1.  Push your code to a **GitHub Repository**.
2.  Go to [Vercel.com](https://vercel.com) and sign up/login.
3.  Click **"Add New..."** -> **"Project"**.
4.  Import your GitHub repository.
5.  **Environment Variables**:
    *   Expand the "Environment Variables" section.
    *   Add Key: `VITE_GOOGLE_MAPS_API_KEY`
    *   Add Value: `your_actual_google_maps_key`
6.  Click **Deploy**.
7.  Vercel will detect Vite automatically and build your site. You will get a live URL (e.g., `fix-my-city.vercel.app`) in under a minute.

## Option 2: Netlify

1.  Push code to GitHub.
2.  Go to [Netlify.com](https://netlify.com).
3.  **"Add new site"** -> **"Import from Git"**.
4.  Connect GitHub and select your repo.
5.  **Build Settings**:
    *   Build Command: `npm run build`
    *   Publish directory: `dist`
6.  **Advanced** -> **Environment Variables**:
    *   Key: `VITE_GOOGLE_MAPS_API_KEY`
    *   Value: `your_key`
7.  Click **Deploy Site**.

## Option 3: Manual Build (For standard hosting)

1.  Run the build command locally:
    ```bash
    npm run build
    ```
2.  This creates a `dist` folder in your project root.
3.  Upload the **contents** of the `dist` folder to any web server (Apache, Nginx, HostGator, GoDaddy, etc.) via FTP/SFTP.
4.  **Note**: For client-side routing (React Router) to work on Apache/Nginx, you may need to configure a rewrite rule to redirect all 404s to `index.html`.

    *   **Netlify**: Create a `_redirects` file in `public/` with content: `/* /index.html 200`
    *   **Vercel**: Handled automatically.
