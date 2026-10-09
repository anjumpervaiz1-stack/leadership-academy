LEADERSHIP ACADEMY: FREE HOSTING WITH ALMOST NO NETLIFY CREDITS
================================================================

THE IDEA
  A. The app (page + 422 audio files) goes on GitHub Pages: free, no credits, 100 GB of traffic a month.
     This is where almost all of the Netlify credits were going (audio downloads and re-deploys).
  B. Netlify keeps only the tiny sync service. You publish it ONCE. Each sync message is a few hundred bytes.
     Rough estimate for 30 principals using the app every day: about 30-45 of the 300 free credits a month.

FILES
  1_App_page.zip                 index.html, sync-config.js, .nojekyll
  2_... to 6_Audio_part...zip    the 422 recordings (folder "audio"), in 5 parts of up to 85 files
  7_Netlify_sync_service.zip     the sync service for Netlify


A. PUT THE APP ON GITHUB PAGES (about 20 minutes, all in the browser)
-------------------------------------------------------------------
1. Create a free account at https://github.com (remember your user name, e.g. anjumpervaiz).
2. Click "+" (top right) > "New repository".
   Repository name:  leadership-academy      Choose: Public      Click "Create repository".
3. On your computer, unzip each of the six zips into its own folder (right-click > Extract All).
   1_App_page gives you index.html, sync-config.js and .nojekyll.
   Each audio part gives you a folder named "audio" with about 85 MP3 files.
   (Windows may hide .nojekyll because it starts with a dot; that is fine.)
4. In the new repository click "uploading an existing file".
   Drag in index.html, sync-config.js and .nojekyll, then click "Commit changes".
5. Upload the audio in 5 rounds (GitHub accepts up to 100 files per upload):
   Click "Add file" > "Upload files", then drag the whole "audio" FOLDER from audio part 1 onto the page.
   Wait until all files are listed, then click "Commit changes". Repeat for parts 2, 3, 4 and 5.
   Check: the repository now shows a folder "audio" containing 422 files.
6. Turn on Pages: repository "Settings" > "Pages" > Source: "Deploy from a branch" >
   Branch: "main", folder "/ (root)" > Save. After 1-2 minutes your app is live at:
       https://YOUR-GITHUB-NAME.github.io/leadership-academy/
   Open it: everything works already (lessons, audio, practice, challenges, self-assessment).
   Only "Sync between devices" is missing until step B is done.


B. PUT THE SYNC SERVICE ON NETLIFY (once, about 15 minutes)
-----------------------------------------------------------
1. Install Node.js "LTS" from https://nodejs.org (default options).
2. Unzip 7_Netlify_sync_service.zip. Open the folder "leadership-academy-sync".
3. Open netlify.toml in Notepad and replace YOUR-GITHUB-NAME with your GitHub user name. Save.
   (This sends anyone who opens the old Netlify address to the app on GitHub.)
4. Open a command window in that folder
   (Windows: click the folder's address bar in File Explorer, type  cmd  and press Enter).
5. Type these one at a time, pressing Enter after each:
       npm install
       npx netlify-cli login
       npx netlify-cli link
   For "link", choose your existing Netlify site (its address stays the same), or create a new one.
       npx netlify-cli deploy --prod
   This is the only Netlify deploy you need (15 credits). Do not drag folders onto Netlify any more.
6. Check: open  https://YOUR-NETLIFY-SITE.netlify.app/api/sync?ping=1   You should see {"ok":true,"v":1}


C. CONNECT THE TWO (2 minutes)
------------------------------
1. On GitHub, open sync-config.js in your repository > pencil icon (Edit).
2. Replace YOUR-NETLIFY-SITE with your Netlify site name, e.g.
       window.ACADEMY_SYNC_URL = "https://leadership-academy-sync.netlify.app/api/sync";
3. "Commit changes". After a minute, open the app > Settings: "Sync between devices" appears.


UPDATING THE APP LATER (free, no Netlify credits)
--------------------------------------------------
On GitHub: open the repository > "Add file" > "Upload files" > drop the new index.html > "Commit changes".
GitHub Pages republishes it in a minute or two.


PRINCIPALS WHO ALREADY USED THE NETLIFY VERSION
------------------------------------------------
Browsers keep progress separately for each web address. Ask them once to press "Backup" on the old
Netlify address BEFORE you do step B (after step B that address only forwards to GitHub),
and then "Restore" on the GitHub address. Then they can turn on sync.


KEEPING NETLIFY CREDITS LOW
---------------------------
- Never re-deploy the sync service unless asked to (each production deploy = 15 credits).
- Check usage any time in Netlify: your team > Usage / Billing.
- On the Free plan, if the 300 credits ever ran out, Netlify pauses the site until next month:
  the app on GitHub keeps working; only sync pauses, and each device keeps its own progress meanwhile.
