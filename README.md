# conservationportal.org

The published site for **[Conservation Portal](https://conservationportal.org)**, a curated
directory of resources for wildlife conservationists, built and maintained by
[The Biodiversity Group](https://biodiversitygroup.org).

## Every file here is generated. Do not edit them.

This repository is build output, served by GitHub Pages from the root of `main`. The HTML,
`sitemap.xml` and `robots.txt` are produced from two CSV files by a build script, and the
next build overwrites anything edited here by hand.

To change what the site says, change the data or the builder, not these files.

## How a change reaches this repo

1. Edit `data/resources.csv` or `data/categories.csv` in the source project.
2. `py scripts/06_build_site.py` renders the landing page, one page per category,
   the sitemap, `robots.txt`, `CNAME` and a 404.
3. `py scripts/07_check_site.py` gates the deploy. It checks tag balance, that each
   page's canonical matches its own path, that every declared category has a page, that
   no internal link points at a directory that does not exist, and that the landing
   page's inline search script parses.
4. `py scripts/10_check_tbg_first.py` and `py scripts/11_check_one_link_per_site.py`
   enforce the two standing presentation rules described below.
5. `py scripts/08_sync_pages_repo.py` mirrors the build into this checkout, then prints
   the git commands. It never commits or pushes on its own.

## Two standing rules, enforced by checks rather than by memory

**The Biodiversity Group's own resources sort first** in every category they appear in.
Applied at build time with a stable sort, so it holds however the underlying data is
ordered, and it applies to search results too.

**One link per site per category.** Deep links into the same site collapse to the single
page that reaches the others, with whatever the dropped entry offered folded into the
surviving description. Shared *hosts* are exempt, because a package repository or a podcast
host carries unrelated things, and those exemptions are listed with written reasons inside
the checker.

## Reporting a problem

Found a dead link, or know a resource that belongs here?
Email <business@biodiversitygroup.org>.

Entries the site marks **dead link** are kept deliberately, so nobody spends an afternoon
searching for something that no longer exists.
