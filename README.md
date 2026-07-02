# Magnum Estate — Financial Consolidation Dashboard

Multi-entity cash-flow consolidation dashboard (17 legal entities, April–June 2026), served as a
static page on Vercel and reading its data **live from Supabase**.

## How it works

- `Workspace.html` is the whole dashboard. On load it fetches the live figures from Supabase
  (`entities`, `line_items`, `entity_period_totals`, `loan_flows`, `highlights`, `transactions`)
  and renders them. The embedded data block is only an offline fallback snapshot.
- `vercel.json` serves `Workspace.html` at the root URL.
- Every push to `main` triggers a Vercel redeploy automatically.

## Data source

- Supabase project `nbnfsflcbueibcfvcwrh` (`https://nbnfsflcbueibcfvcwrh.supabase.co`).
- The page uses the **publishable** (anon) key only. All tables are read-only via RLS.
- To change the numbers, edit the data in Supabase — the dashboard updates on next load. No redeploy needed.

## Updating the dashboard UI

Edit `Workspace.html`, then:

```bash
git add Workspace.html && git commit -m "Update dashboard" && git push
```

Vercel redeploys in ~30s; the public URL stays the same.
