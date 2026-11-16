# Connect the Six Degrees shared score board

The finish screen can save anonymous results to Supabase and show a score distribution against other players. This static website has no database until you connect one.

## 1. Create the Supabase table and comparison function

1. Create a Supabase project at [supabase.com](https://supabase.com/).
2. In the project, open **SQL Editor** and create a query.
3. Copy all of `supabase-setup.sql` into the query and run it.

The setup enables Row Level Security. The website can submit score, hops, time, mode, and the two article titles. It cannot read individual score rows; the database function returns only anonymous aggregate counts for the graph.

## 2. Add the public project settings

In Supabase, open **Project Settings → API Keys** (or the project's Connect dialog) and copy the **Project URL** and **Publishable key**. In `outputs/index.html`, replace these two placeholders near the start of the script:

```js
const SCORE_SUPABASE_URL='YOUR_SUPABASE_PROJECT_URL';
const SCORE_SUPABASE_PUBLISHABLE_KEY='YOUR_SUPABASE_PUBLISHABLE_KEY';
```

Use the `sb_publishable_...` key. Do not put a Supabase secret or service-role key in the website.

## 3. Publish the update

Upload the updated `outputs/index.html` and `render.yaml` to the GitHub repository, then let Render redeploy. After the Supabase setup and deploy, completed games will add a score and show how it compares with earlier players.

Scores are anonymous; the site does not ask players to sign in or submit names. Since visitors can submit without accounts, this is a casual comparison rather than a cheat-proof leaderboard.
