<div align="center">

```
 ██████╗██╗      █████╗ ██╗   ██╗██████╗ ███████╗    ███████╗███████╗ ██████╗     ███████╗██╗  ██╗██╗██╗     ██╗     ███████╗
██╔════╝██║     ██╔══██╗██║   ██║██╔══██╗██╔════╝    ██╔════╝██╔════╝██╔═══██╗    ██╔════╝██║ ██╔╝██║██║     ██║     ██╔════╝
██║     ██║     ███████║██║   ██║██║  ██║█████╗      ███████╗█████╗  ██║   ██║    ███████╗█████╔╝ ██║██║     ██║     ███████╗
██║     ██║     ██╔══██║██║   ██║██║  ██║██╔══╝      ╚════██║██╔══╝  ██║   ██║    ╚════██║██╔═██╗ ██║██║     ██║     ╚════██║
╚██████╗███████╗██║  ██║╚██████╔╝██████╔╝███████╗    ███████║███████╗╚██████╔╝    ███████║██║  ██╗██║███████╗███████╗███████║
 ╚═════╝╚══════╝╚═╝  ╚═╝ ╚═════╝ ╚═════╝ ╚══════╝    ╚══════╝╚══════╝ ╚═════╝     ╚══════╝╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚══════╝
```

**[ CLAUDE SKILLS FOR GOOGLE'S SEARCH ENGINE ]**

[![Claude Skill](https://img.shields.io/badge/Claude-Skill-00FF41?style=flat-square&labelColor=0D0D0D)](https://docs.claude.com)
[![Domain Agnostic](https://img.shields.io/badge/domain-agnostic-00FF41?style=flat-square&labelColor=0D0D0D)](.)
[![Skills](https://img.shields.io/badge/skills-SEO-00FF41?style=flat-square&labelColor=0D0D0D)](.)
[![License](https://img.shields.io/badge/license-MIT-00FF41?style=flat-square&labelColor=0D0D0D)](./LICENSE)

</div>

---

## > SYSTEM_OVERVIEW

<div align="center">

Portable [Claude Skills](https://docs.claude.com) for anyone who publishes web content and wants Google to actually notice it. Domain-agnostic, drop them into a gaming blog, a finance newsletter, a recipe site, whatever. Each skill detects the niche on its own; no configuration required.

</div>

```
[+] seo-content-editor        — scores an article, logs every change, returns a rewritten version
[+] seo-indexing-diagnosis    — diagnoses why a "crawled but not indexed" page isn't showing up
[+] Both auto-detect the content domain — no fixed niche list, no manual setup
```

---

## > DIRECTORY_LISTING

```
seo-skills/
├── README.md
├── LICENSE
├── SEO Content Editor/
│   └── SKILL.md
├── SEO Indexing Diagnosis/
│   └── SKILL.md
├── SEO Rank Gap Analysis/
│   └── SKILL.md
└── Keyword Topic Research/
    └── SKILL.md
```

---

## > INSTALL.sh

```
# Claude.ai / Claude Desktop / Claude Code
1. Download the SKILL.md for the skill you want (or clone the whole repo)
2. Upload it via "Save skill" in Claude
3. Claude auto-triggers it when your request matches — no need to name it explicitly

# Any other tool
Paste the SKILL.md contents as a system/instruction prompt.
Both files are self-contained — zero external dependencies.
```

---

## > USAGE_EXAMPLES

<div align="center">

A couple of ways these skills get triggered automatically once installed:

</div>

```
$ "Review this article for SEO and rewrite it"
  -> triggers seo-content-editor

$ "This page is live and crawled but won't show up in Google, here's the link"
  -> triggers seo-indexing-diagnosis

$ "Here's our homepage link — what keyword and topic should we write about today?"
  -> triggers keyword-topic-research

$ "Here's our page and a competitor's page for the same keyword — why do they outrank us?"
  -> triggers seo-rank-gap-analysis
```

---

## > CONTRIBUTING

<div align="center">

Pull requests are welcome, as long as they hold to these three rules:

</div>

```
[1] Keep skills domain-agnostic - no fixed niche lists
[2] Let the model detect the domain, don't hardcode one
[3] Cite the Google policy behind any check you add
```

---

<table align="center">
<tr>
<td>
 
```
[ FOLLOW THE WHITE RABBIT. ]
```

</td>
</tr>
</table>

<div align="center">
 
**License:** MIT — see [`LICENSE`](./LICENSE)

</div>
