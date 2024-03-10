+++
title = "Personal website"
author = ["Griffin Knipe"]
publishDate = 2024-02-24
lastmod = 2024-02-24T23:51:02-05:00
tags = ["workstation"]
draft = false
+++

## <span class="org-todo todo TODO">TODO</span> Create a personal website <span class="tag"><span class="task">task</span><span class="hobby">hobby</span></span> {#create-a-personal-website}

<p><span class="timestamp-wrapper"><span class="timestamp-kwd">SCHEDULED:</span> <span class="timestamp">&lt;2024-02-24 Sat&gt;</span></span></p>

-   Write posts in my orgmode notes
-   Generate with [Ox-hugo]({{< relref "ox-hugo" >}})
-   Publish with [Hugo]({{< relref "hugo" >}})
-   Host on GitHub pages
    -   Seems like the simplest solution for now
    -   AWS hosting could be &lt;$1 per month
-   [Indie web]({{< relref "indie_web" >}}) seems interesting
-   Don't forget to [license](https://chooser-beta.creativecommons.org/) it


### Inspiration {#inspiration}

-   [link](https://doubleloop.net/2020/08/21/how-publish-org-roam-wiki-org-publish/)
-   [link](https://systemcrafters.net/publishing-websites-with-org-mode/building-the-site/)
-   [link](https://ox-hugo.scripter.co/doc/quick-start/)


### Building from my personal notes {#building-from-my-personal-notes}

The command `org-export-dispatch` exports my buffer or subtree to other formats. Headings can be selected or excluded from export by attaching the `:export:` or `:noexport:` tags, respectively.

```elisp
(setq org-publish-project-alist
      '((org-notes
         :base-directory 'org-directory
         :base-extension: org
         :publishing-directory /tmp/project_export
         :recursive t
         :publishing-function 'org-html-export-to-html)))
```

```elisp
(setq org-publish-project-alist
      (list
       (list
        "my-org-site"
        :recursive t
        :base-directory "~/Org"
        :publishing-directory "/tmp/project_export"
        :publishing-function 'org-org-publish-to-org
        :exclude ".stversions")))
```
