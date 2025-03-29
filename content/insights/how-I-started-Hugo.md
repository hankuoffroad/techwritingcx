---
title: "How I Started Developing My Hugo Site"
date: 2025-03-29
author: "Hanku"
description: "A personal journey through building a Hugo site from scratch, with insights on customization, design, and technical challenges."
tags:
  - Hugo
  - Web Development
  - Personal Blog
  - Website Development
categories:
  - Development Journey
  - Personal Projects
draft: false
---

## Why I Chose Hugo (Even Though I Didn't Want To)

When I first started looking for a theme, I thought that just installing it would make a beautiful website. But it turned out to be just a skeleton site. After testing it for about five days, I realized that learning step by step, like building with Legos, is actually a good approach.

Problem-solving is such an important part of being a tech writer, and I'm really enjoying the process.

Connecting goals with current activities

- How can learning to build websites be applied to technical writing/translation processes?

- How can I differentiate myself as a freelancer by applying automation?

- If I increase my collaboration with AI, what kind of role can I take on in the industry?  

## Switching Hugo Themes: Challenges & Solutions

- Problem: Changing the Hugo theme turned out to be more challenging than expected

- Solution: Tried a couple of themes and selected the Paige them

- Helpful Resources: Hugo and Paige theme Official documentation

- Result: Successfully applied the Paige theme and was satisfied with the outcome

## Preparing the Test Environment and Uploading a Simple Test Page

- Hugo Installation Environment: Ubuntu 24.04.2 LTS

- Hugo Version: extended/stable 0.145.0

- Hugo theme: Paige

Keeping Ubuntu 24.04 LTS (supported until 2029) while maintaining the latest Hugo via Snap is the most stable choice. Stability means operating predictably over a long period.

If you're working on Hugo-based web development and localization automation, the best approach is to stick with Ubuntu LTS and install the latest Hugo via Snap.

Run hugo server --debug to check for deprecated warnings.
(There might be changes to the structure of layouts, partials, and config.toml.)

For beginners in web development (I didn't even know what I was developing at first), the hardest part is website configuration. If the environment setup is difficult, it becomes a barrier. Installing through App Center was easy (as intuitive as the Microsoft/Apple App Store) – this helped me understand why developers are careful when choosing a distribution.

Development Environment: Git, Go, and Dart Sass

hugo new site <sitename>: Site skeleton → literally, nothing is there.

It's important to understand the directory structure before moving forward.

The documentation varies greatly from theme to theme.

The Paige theme is installed using Hugo's module system, not a Git submodule. This method is used starting from Hugo v0.60.0 and later.

Be careful if the [params.paige] section is duplicated or declared incorrectly.

## Content management

Multi-format support: Regardless of content format, all content must have front matter, preferably including both title and date. Hugo selects the content renderer based on the markup identifier in front matter, falling back to the file extension.

There are three ways to define menu entries: Automatically, In front matter, and In site configuration

Define in front matter

---
title: "How I Started Developing My Hugo Site"
date: 2025-03-29
author: "Hanku"
description: "A personal journey through building a Hugo site from scratch, with insights on customization, design, and technical challenges."
tags:
  - Hugo
  - Web Development
  - Personal Blog
  - Website Development
categories:
  - Development Journey
  - Personal Projects
draft: false
---

## How to Use grep to Navigate Your Hugo Configuration

grep is one of the most essential tools for developers. At first, you might wonder, "Why do I need this?" But once you get used to it, it becomes incredibly useful for searching files or modifying specific code/configurations.

To find where a specific text is defined in hugo.toml:

```sh
grep "New Hank Hugo Site" hugo.toml
```

To search the entire project:

```sh
grep -r "New Hank Hugo Site" .
```

To search within the content/ directory:

```sh
grep -r "Yourpost" content/
```

To search inside the themes/paige/ directory:

```sh
grep -r "New Hank Hugo Site" themes/paige/
```

## Information Architecture and Design Strategy

Structuring Content and Navigation

- The website is divided into three main sections: Profile, Tech & Tools, and Notes, with content displayed in a tile-based layout.

- Instead of using deep subsections, utilize tags and filters to organize content efficiently.

- Keep the category structure minimal until there is enough content, and expand it flexibly when needed.

- Avoid anti-patterns seen in websites with too many menu items and empty categories, which make navigation difficult.


## Building a Scalable Hugo Site: Design, Git Workflow, and Clean Code Practices

Commit Strategy

- Commit by feature → Each small change should be committed separately.

- Plan major changes in a modular way and complete them systematically.

- Work locally first and only push to remote when the code is stable.

Branching Strategy

- main → Stable, production-ready code

- dev → Development and experimental branch

- feature/custom-header → A feature-specific branch for modifications

Using .gitignore for Clean Project Management

- Add public/, resources/, and .hugo_build.lock to .gitignore

- A well-maintained .gitignore file:

    -- Prevents unnecessary files from being committed

    -- Keeps the project clean and manageable

    -- Allows flexibility in deployment strategies

    -- Makes it easier to manage accidentally committed files

Modular Commit Strategy & Commit Message Guidelines

- Follow a structured commit message format:

```sh
git commit -m "feat: add custom homepage layout"
git commit -m "fix: resolve menu alignment issue"
git commit -m "refactor: restructure partials for better readability"
```

## SCSS File Path Issues & Transpilation

If you installed Hugo via Snap, it already includes Dart Sass, so it's best to remove any separately installed dart-sass to avoid conflicts.
Detecting SCSS Build Failures

To visually detect SCSS build failures, you can add the following fallback code:

```sh
<style>
    /* Change background to red if SCSS fails to compile */
    body { background: red !important; }
</style>
```


