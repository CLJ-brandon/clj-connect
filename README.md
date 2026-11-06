# CLJ connector sign-in page

Static sign-in and consent page for the CLJ Meta connector (`supabase/functions/meta-mcp`). Supabase Auth's OAuth 2.1 server sends people here during "Connect" in Claude. They sign in with their @chrislovesjulia.com Google account and approve read-only access.

Published to GitHub Pages from its own small repo, because Supabase Edge Functions can't serve HTML.

**No secrets here.** The Supabase project URL and publishable key are meant to be public. Access is enforced on the server:
- Every pipeline table has RLS with no policies, and views and functions are revoked from `anon`/`authenticated` (`supabase/migrations/202611061200_lock_down_public_api.sql`)
- The Google OAuth client is Internal (CLJ Workspace accounts only)
- The connector rejects any token whose email isn't @chrislovesjulia.com
- The Meta token stays in Supabase Vault
