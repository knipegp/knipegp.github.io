+++
title = "Ox-hugo"
author = ["Griffin Knipe"]
publishDate = 2024-02-24
lastmod = 2024-02-24T23:51:01-05:00
tags = ["workstation"]
draft = false
+++

**Basic export**

```elisp
(setq org-hugo-auto-set-lastmod t)
(setq org-hugo-base-dir "~/knipegp.github.io/")
```

```org
:PROPERTIES:
:ID:       50bbee18-66fd-40db-b611-150118a19009
:EXPORT_FILE_NAME: personal_website
:EXPORT_OPTIONS: p:t
:EXPORT_HUGO_DRAFT: false
:EXPORT_HUGO_PUBLISHDATE: 2024-02-24
:END:
```

Add this property to exportable headings to include planning data in export (i.e. `DEADLINE`, `SCHEDULED`)

```org
:PROPERTIES:
:EXPORT_OPTIONS: p:t
:END:
```

Note that this data overwrites the publish date of the post which I want to avoid.

**How can I add top level heading `TODO` data?**

:/ I appears to be parsed as front-matter data which is unfortunate. The quick solution seems to be moving any headlines for which I want to include `TODO` data, up a level.

**ID references**

```org
:PROPERTIES:
:ID:       50bbee18-66fd-40db-b611-150118a19009
:END:
```

Links between posts work.

Links to sub-headings automatically work.

**Export from all files in org directory**

```elisp
(setq org-files (directory-files "~/Org" nil ".*\.org$"))
(setq initial-file buffer-file-name)
(dolist (org-file org-files)
  (find-file org-file)
  (org-hugo-export-wim-to-md :all-subtrees))
(find-file initial-file)
```

Requires `:noexport:` to be added to `#+hugo_tags` in any files that don't contain Org Hugo headings. Otherwise, those files will be exported as a per-file post. See [link](https://ox-hugo.scripter.co/doc/tags-and-categories/#marking-files-to-not-be-exported).
