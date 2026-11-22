# Contributing to Awesome Privacy Adtech

Thank you for helping maintain a practical reference for engineers working on privacy in advertising. Contributions can include open-source tools, technical specifications, reference implementations, and other substantive technical resources.

By participating, you agree to follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## Submission Guidelines

- **Relevance:** The resource should help readers implement, measure, audit, or understand privacy in advertising. General-purpose privacy technologies are welcome when their connection to ad tech is clear.
- **Technical substance:** Prefer inspectable open-source code, specifications, official technical guidance, and reference implementations. Do not submit purely commercial SaaS marketing pages, gated whitepapers, or vendor comparison posts.
- **Maintenance and status:** Prefer maintained projects and current documents. An archived, deprecated, or superseded resource may be included when it has clear historical or technical value; label its status in the description.
- **Direct links:** Link to the primary repository, official site, or original document. No affiliate, referral, tracking, search-engine, or redirect links.
- **No duplicates:** Search the README before submitting. If a resource is already listed, propose an improvement to its existing entry instead.

## Description Standards

Write one concise, objective sentence about the resource's actual function or mechanism. Avoid promotional language, superlatives, pricing, and unsupported compliance claims. Distinguish a draft from a deployed feature and a UI component from a complete consent-management system.

- **Do:** “Parses GPP strings for server-side privacy signal handling.”
- **Don't:** “The best tool for effortless privacy compliance.”

## Step-by-Step Submission Process

1. Find the most specific relevant section in [README.md](README.md), or open an issue if a new section is needed.
2. Verify the resource, its current status, and its direct URL against the primary source. If it is software, check its license and maintenance status.
3. Add the entry using the format below. Use the GitHub icon when the primary link points to GitHub, including a file or specification hosted there; use the web icon for other sites and documents. Put a blank line between entries.

   ```markdown
   ![github](image/alg_R.png) [Project Name](https://github.com/org/repo) - Short, objective description of what it does.

   ![web](image/alg_I.png) [Resource Name](https://example.com) - Short, objective description of what it does.
   ```

4. Perform the checks below, then submit a pull request with a descriptive title such as `Add [Resource Name]`. Related entries in the same section may be submitted together.

## Checks Before Submitting

There are currently no automated checks configured. Please check manually that:

- Links work, point to primary sources, and do not contain tracking parameters.
- The entry is not a duplicate, is in the right section, and uses the correct icon and Markdown format.
- The description is factual, concise, and labels archived, deprecated, or superseded resources when relevant.
- The Markdown preview renders the links, icons, and headings correctly.
