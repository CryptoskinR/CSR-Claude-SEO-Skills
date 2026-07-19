<div align="center">

```
 ██████╗██╗      █████╗ ██╗   ██╗██████╗ ███████╗
██╔════╝██║     ██╔══██╗██║   ██║██╔══██╗██╔════╝
██║     ██║     ███████║██║   ██║██║  ██║█████╗
██║     ██║     ██╔══██║██║   ██║██║  ██║██╔══╝
╚██████╗███████╗██║  ██║╚██████╔╝██████╔╝███████╗
 ╚═════╝╚══════╝╚═╝  ╚═╝ ╚═════╝ ╚═════╝ ╚══════╝

 ███████╗███████╗ ██████╗     ███████╗██╗  ██╗██╗██╗     ██╗     ███████╗
 ██╔════╝██╔════╝██╔═══██╗    ██╔════╝██║ ██╔╝██║██║     ██║     ██╔════╝
 ███████╗█████╗  ██║   ██║    ███████╗█████╔╝ ██║██║     ██║     ███████╗
 ╚════██║██╔══╝  ██║   ██║    ╚════██║██╔═██╗ ██║██║     ██║     ╚════██║
 ███████║███████╗╚██████╔╝    ███████║██║  ██╗██║███████╗███████╗███████║
 ╚══════╝╚══════╝ ╚═════╝     ╚══════╝╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚══════╝
```

**[ TWO CLAUDE SKILLS FOR GOOGLE'S INDEX ]**

[![Claude Skill](https://img.shields.io/badge/Claude-Skill-00FF41?style=flat-square&labelColor=0D0D0D)](https://docs.claude.com)
[![Domain Agnostic](https://img.shields.io/badge/domain-agnostic-00FF41?style=flat-square&labelColor=0D0D0D)](.)
[![Skills](https://img.shields.io/badge/skills-2-00FF41?style=flat-square&labelColor=0D0D0D)](.)
[![License](https://img.shields.io/badge/license-MIT-00FF41?style=flat-square&labelColor=0D0D0D)](./LICENSE)

</div>

---

## > SYSTEM_OVERVIEW

<div align="center">

Two portable [Claude Skills](https://docs.claude.com) for anyone who publishes web content and wants Google to actually notice it. Domain-agnostic — drop them into a gaming blog, a finance newsletter, a recipe site, whatever. Each skill detects the niche on its own; no configuration required.

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
├── seo-content-editor/
│   └── SKILL.md
└── seo-indexing-diagnosis/
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

<div align="center">

```
[ FOLLOW THE WHITE RABBIT ]
```

**License:** MIT — see [`LICENSE`](./LICENSE)

</div>
