# legalize-pk

The Constitution of Pakistan - one article per file, one amendment per commit.

---

## The idea

Most people encounter the constitution as a single long document or scattered PDFs. That makes it difficult to see what changed, when, and in which part of the text.

This repository splits the 1973 Constitution into individual Markdown files - one per article - and records each enacted amendment as a backdated Git commit that updates only the articles it actually changed. The result is a history you can navigate with standard Git tools:

```bash
# See every amendment that touched Article 239
git log -- federal-constitution/article-239.md

# Compare the article's text before and after the 18th Amendment
git diff <commit-before> <commit-after> -- federal-constitution/article-239.md

# Read the full article as it stood on a given date
git show <commit>:federal-constitution/article-239.md

# See all amendments by a specific president
git log --author="Fazal Ilahi Chaudhry"

# See what files changed in a specific amendment
git show --stat <commit>

# List all amendments in order with dates
git log --oneline --format="%ad %s" --date=short

```

Each commit is backdated to the amendment's actual date of assent, so the repository's history mirrors constitutional time rather than the order files were created.

---

## Repository structure

```
legalize-pk/
├── federal-constitution/
│   ├── preamble.md
│   ├── article-001.md
│   ├── article-002.md
│   └── ...
└── federal-amendments-summaries/
    ├── 1974-01-first-amendment.md
    ├── 1974-02-second-amendment.md
    └── ...
```

`**constitution/**` — one file per article, named with zero-padded numbers so they sort correctly. Omitted articles are kept as files with a single `[Omitted]` line so their history remains intact.

`**amendments/**` — one plain-English summary per enacted amendment, created in the same commit as the amendment itself. Each file includes the date of assent, the articles affected, and a link to the source text.

---

## Why it matters

The constitution is the foundation of rights, institutions, and the balance of power. When that text is structured and version-controlled, it stops being a static document and becomes something you can reason about - article by article, amendment by amendment, across more than five decades.

This work is shared openly in the hope that it proves useful: to students and researchers tracing how a particular right or institution evolved, to journalists covering constitutional change, to civic organizations that want to explain the law to a broader public.

It is also intended as a clean data source for software and AI. A language model given structured constitutional text - where each article is discrete, each amendment is a diff, and the history is intact - can answer questions like *"what did Article 63 say before the 18th Amendment?"* or *"which articles have been amended more than twice?"* with far more precision than one working from a monolithic PDF. *Structured law is more useful law.*

---
This repository is inspired by [legalize-es](https://github.com/legalize-dev/legalize-es) which did similar work for the Spanish Constitution.

## License

The legislative texts are in the public domain. The structure and format are under the [MIT License](https://opensource.org/licenses/MIT).