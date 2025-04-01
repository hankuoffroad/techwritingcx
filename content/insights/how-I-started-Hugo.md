---
title: "How I Started Developing My Hugo Site"
date: 2025-04-01
author: "Hanku"
description: "A personal journey through building a Hugo site from scratch, with insights on customization, design, and technical challenges."
tags:
  - Hugo
  - Web Development
  - Personal Blog
categories:
  - Development Journey
  - Personal Projects
draft: false
---

# How I Started Developing My Hugo Site

## Background & Motivation

In 2002, I began my career in software deployments across SCM, ERP, CRM, and Big Data projects at Samsung Electronics Europe, focusing on enhancing user experience and ensuring long-term usability. This hands-on involvement with the entire software lifecycle made me acutely aware of the critical role that documentation and localization play in the success of any project. My fascination with tech writing began when I discovered how to make documentation more developer-friendly, bridging the gap between developers and users through participation in open-source projects.

As a technical writer, I've realized that hands-on experience is essential for solving problems better and thinking like a developer. The portfolio website I built from scratch provides me with problem-solving skills and broadens my understanding of development practices.

## Why I chose Hugo for my portfolio website

When building my portfolio website, I needed a solution that was fast, flexible, and easy to maintain. After exploring various options, I decided to go with Hugo, a powerful static site generator written in Go. Here’s why it stood out:

- Flexible Content Management: Hugo’s file-based structure makes content management straightforward. Instead of dealing with complex databases, I can organize my content using simple Markdown files. This fits perfectly with my workflow as a technical writer and localization expert, allowing me to focus on creating content rather than managing a backend system.

- Multi-Format Content Support in Hugo: One key reason I chose Hugo is its ability to generate multiple output formats. Unlike traditional static site generators that focus solely on a format, Hugo supports:

    -- Markdown (.md) - The default format for content in Hugo. It’s widely used because of its simplicity and readability.

    -- reStructuredText (reST) (.rst) - An alternative markup language for content, commonly used in Python-related projects.

    -- AsciiDoc (.adoc or .asciidoc) - A lightweight markup language that’s often used in technical documentation.

    -- XML (.xml) - Although not as common for content creation, Hugo can handle XML files (such as RSS feeds or other structured data). This flexibility allows me to extend my website beyond a traditional blog—potentially generating custom feeds or integrating with other services.

- Hugo includes Hugo Pipes, which allows for asset optimization without needing external tools. I can process CSS with Dart-Sass within Hugo’s ecosystem. This simplifies my workflow and reduces the need for additional build tools.

- Version control and ease of deployment: Since Hugo is a static site generator, all content and configurations are stored in a Git repository. This makes it easy to version control my site, collaborate with others, and deploy changes seamlessly using services like GitHub Pages, Vercel, or Netlify.

## Preparing the test environment and uploading a test page

- System Environment: Ubuntu 24.04.2 LTS

- Hugo Version: extended/stable 0.145.0

- Hugo theme: Paige

- Key Development Tools: Git, Visual Studio Code, and Dart Sass (CSS Preprocessor)

Keeping Ubuntu 24.04 LTS (supported until 2029) while maintaining the latest Hugo via Snap is the most stable choice in the long run. Stability means operating predictably over a long period.

If you're working on Hugo-based web development and localization automation, the reliable approach is to stick with Ubuntu LTS and install the latest Hugo via Snap.

For beginners in web development, the hardest part is website configuration. If the environment setup in the beginning is difficult, it becomes a barrier. Installing Hugo through App Center of Ubuntu was effortless (as intuitive as the Microsoft/Apple App Store) – this helped me understand why developers are careful when choosing a distribution.

I've installed The Paige theme using Hugo's module system, not a Git submodule. This method is used starting from Hugo v0.60.0 and later.

To preview a simple test page in dev environment, run the command in terminal;

```sh
$ hugo new site <sitename>
```

This command creates a site skeleton, outlining its fundamental components without detailed content or styling.

## Content management

Regardless of content format, all content must have front matter, preferably including both title and date. Hugo selects the content renderer based on the markup identifier in front matter, falling back to the file extension.

There are three ways to define menu entries: Automatically, In front matter, and In site configuration

In this blog, I’ve used front matter to define key metadata for each post. For example, I specify the title, date, and taxonomy at the beginning of my markdown files using YAML. This ensures that Hugo processes and displays the content correctly. Below is an example of how I define front matter in my blog posts:

```yaml
---
title: "How I Started Developing My Hugo Site"
date: 2025-03-29
author: "Hanku"
description: "A personal journey through building a Hugo site from scratch, with insights on customization, design, and technical challenges."
tags:
  - Hugo
  - Web Development
  - Personal Blog
categories:
  - Development Journey
  - Personal Projects
draft: false
```

## Information architecture

When designing the website’s structure, the focus is on clarity, usability, and scalability. The goal is an intuitive navigation system that allows visitors to easily access relevant content while keeping the organization flexible for future expansion.

- Three Core Sections: The website is divided into three main sections: Profile, Insights, and Projects.

    -- Profile: Introduces who I am, my ongoing projects, and key highlights of my contributions to open-source initiatives

    -- Insights: Focuses on reflections rather than straightforward how-to guides, covering topics such as lessons learned from projects, event participation experiences, reviews of developer tools, automation insights, and IT certification preparation

    -- Projects: Showcases my involvement in open-source projects, including key milestones, event participation plans, long-term vision, and integration with GitLab/GitHub APIs

- Tag-Based Organization: When designing my website, I intentionally avoided using nested sections and a typical tile layout, which are often seen in free blog platforms. In my opinion, these approaches can make the design feel cluttered and overwhelming. While this may be a matter of personal taste, I believe it's important to have full control over how the site looks and functions—the way I want it. I prefer a more minimalist and straightforward design that gives a clear, clean structure, and allows me to present content in a way that feels organized and intentional. By avoiding overly complex layouts, I maintain the flexibility to adjust and optimize the site exactly how I envision it, without being limited by pre-defined templates.

- Minimalist Category Structure for Scalability: Categories are kept intentionally minimal at the start to avoid unnecessary complexity. As more content is added over time, the structure can be expanded naturally to accommodate growth.

## Building a scalable Hugo site using Git Workflow

When developing a Hugo site, establishing a solid workflow is essential for scalability, maintainability, and efficiency. Whether you're working solo or as part of a team, having a clean, modular, and consistent approach to managing your codebase will save time and reduce errors in the long run. This guide outlines key strategies for Git commits, branching, and project management practices to help you build a scalable Hugo site while keeping your development process streamlined and your codebase clean.

- Modular Commit and Commit Message Guidelines: A well-organized commit strategy is crucial for maintaining a clean history of your project and enabling efficient collaboration. Here's how you can manage your commits effectively:

    -- Commit by feature: Each small change should be committed separately. This ensures that each feature or fix is self-contained and easy to track, making it simple to revert or modify specific changes in the future.

    -- Plan major changes modularly: For larger features or refactorings, break them into smaller, manageable tasks. Complete these tasks systematically, which will make it easier to debug and test each part before moving on to the next.

    -- Work locally first: Always develop locally and test your changes before pushing to remote repositories. Only push your code to the remote repository when you are confident it is stable. This minimizes the risk of introducing bugs.

    -- Write clear and concise commit messages: Each commit message should explain what was done and why it was necessary. Avoid vague messages like "fixed stuff"; instead, use precise language, such as "Fixed header alignment on mobile devices." Here are some examples of well-written commit messages:

    ```sh
    git commit -m "feat: add custom homepage layout"
    git commit -m "fix: resolve menu alignment issue"
    git commit -m "refactor: restructure partials for better readability"
    ```

- Branching Strategy: A well-structured branching strategy is essential for maintaining an organized codebase, enabling efficient development and  deployment.

    -- main: This branch should always contain stable, production-ready code.

    -- dev: This branch is dedicated to ongoing development work and experiments. You can merge features or fixes into dev before they are considered stable enough to move to main.

    -- feature/custom-header: For specific changes like adding a custom header or new functionality, create feature branches. This keeps the codebase clean and allows you to work on individual features without disrupting the main development flow.

- Using .gitignore for Clean Project Management: One of the simplest yet most effective ways to manage a project is through proper use of .gitignore. This file ensures that unnecessary or generated files are not committed to your repository, helping maintain a lean and efficient workflow.

Add public/, resources/, and .hugo_build.lock to .gitignore: These are typically generated files that don’t need to be tracked in version control. By ignoring these files, you avoid cluttering your repository with files that can be easily regenerated.

## Another reason why documentation is important

Reflecting on the process, I’ve come to realize just how crucial documentation is in development. It’s not just about writing code but ensuring that everything is clear, understandable, and easy to maintain. This understanding has made me appreciate the importance of documenting every step in the development journey. Additionally, collaborating with the theme author has made this journey even more rewarding. The challenges have been enjoyable, and it has truly been a learning experience as we work together to improve and refine the theme. This collaboration has made the entire process not only productive but also deeply fulfilling.

## Reflecting on the journey with Hugo

As I look back on my journey with Hugo, it's clear that building a site isn't just about the final product—it's about the entire process and the ecosystem that supports it. From designing the architecture of my site to diving deep into the code and customizing themes, each step has been a learning experience. What truly made this journey fulfilling was the support and collaboration from the wider Hugo community.

The open-source ecosystem around Hugo has provided a wealth of resources, from theme authors to contributors, who generously share their knowledge and expertise. Through this collaboration, I’ve been able to overcome challenges, implement new features, and continuously improve the site. The community’s contributions have made the development process not only easier but also more enjoyable.

In the end, it's not just the technical skills I gained but the sense of belonging to a larger, thriving ecosystem that makes the journey worthwhile. The support I received has reinforced my belief in the power of community-driven development. As I continue to work with Hugo, I’m excited for what’s to come and deeply grateful for the support that has made this all possible.