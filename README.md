# Client Approval Page

Interactive design preview for the **Creator OS client approval flow** — the page a client sees when Lunar Strategy shares a creator shortlist via `/lists/<token>`.

🔗 **Live preview:** see GitHub Pages link in the repo's About / Settings → Pages.

## What's in here

A single `index.html` that renders a fully self-contained design preview, including:

- **Clean co-branded header** (Lunar Strategy × client logo)
- **KPI cards** — Reviewed · Approved value · Budget remaining · Avg Lunar score (with trend badges)
- **Filter tabs + search + sort + bulk approve**
- **Aligned data table** — Avatar · Name · Followers · Score · Engagement · 30d Δ · Price · Status · Expand
- **Inline status dropdown** per row (Pending / Approved / Declined) — shadcn `Select`-style
- **Per-creator detail panel** with bio, niche/country/format chips, price pills, and a 30-day Lunar score trend chart (shadcn `ChartAreaGradient` pattern)
- **Four states** to flip between via the top bar: **Loaded · Loading · Empty · Mobile**
- Mobile layout (cards instead of list) viewable in the **Mobile** state

## Stack

- Plain HTML
- [Tailwind CSS](https://tailwindcss.com/) via CDN (with shadcn/ui design tokens)
- [shadcn/ui](https://ui.shadcn.com/) component patterns (Card, Badge, Table, Tabs, Select, DropdownMenu, ChartAreaGradient)
- Inline SVG charts (catmull-rom smoothed area chart matching shadcn's Recharts gradient)

## How to use

Open `index.html` in any browser, or visit the GitHub Pages URL.

To switch between states (Loaded / Loading / Empty / Mobile) use the dark switcher at the top of the page.

To interact:
- Click a row to expand its detail panel + chart
- Click the status dropdown to set Pending / Approve / Decline
- Filter tabs (All / Pending / Approved / Declined) filter the list live
- Sort dropdown reorders by Followers / Score / Engagement / Price

## Hand-off

For Codex to ship this in production, see the audit folder's `MIGRATION.sql` (server-side fix for the data leak), `vercel.json` (security headers), and `AUDIT.md` (security + perf review). The implementation path is `npx shadcn@latest init` then 1:1 translation of `index.html` JSX-equivalent components.
