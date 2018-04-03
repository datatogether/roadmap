# Project Guidelines

Here are our guidelines that all project repositories for Data Together should 
follow, if setting up new repositories we have [templates](./templates/). In 
addition, command line tools like [hub](https://github.com/github/hub) and 
[ghi](https://github.com/stephencelis/ghi) can help with multi-repository label
and issue management

- [Repository Contents](#repository-contents)
  - [Readme](#readme)
  - [License](#license)
  - [Contributing Guidelines](#contributing-guidelines)
  - [Issue Template](#issue-template)
- [Style Guidelines](#style-guidelines)

## Repository Contents

Each project repository **requires**, at a minimum:

1. Readme — `README.md`
1. License — `LICENSE`
1. Contributing Guidelines — `.github/CONTRIBUTING.md`
1. Issue Template — `.github/ISSUE_TEMPLATE.md`

### Readme

Each [**README**](https://en.wikipedia.org/wiki/README) file follows a 
[`README.md` template](./templates/README.md) and serves to introduce people 
to the repository contents and provide getting started instructions, as well 
as link to Data Together-wide communication channels.

### License

[GPLv3](http://gplv3.fsf.org/)—or
[AGPLv3](http://www.gnu.org/licenses/agpl-3.0.html) ([_why Affero?_
](http://www.gnu.org/licenses/why-affero-gpl.html))—is our _preferred_
**license** for code, and [Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/)
for creative works and documentation.

We also use a [License and Copyright block](#license--copyright-readme-block),
added to our READMEs.  We also add a [LICENSE](/LICENSE) file to the repo, and 
occasionally include a [Code Header License block](#code-header-license-block).

#### License & Copyright block for READMEs

```markdown
## License & Copyright

Copyright (C) <year> Data Together

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation, version 3.0.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

See the [`LICENSE`](./LICENSE) file for details.
```

#### Code Header License block

```
/**
 * Copyright (C) <year(s)> Data Together
 *
 * This program is free software: you can redistribute it and/or modify it
 * under the terms of the GNU General Public License as published by the Free
 * Software Foundation, version 3.0.
 *
 * This program is distributed in the hope that it will be useful, but WITHOUT
 * ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
 * FITNESS FOR A PARTICULAR PURPOSE. See LICENSE file for details.
 */
```

### Contributing Guidelines

We use a [`CONTRIBUTING.md` template](./templates/CONTRIBUTING.md) that points
to our main **Contributing Guidelines** located in
[`datatogether/datatogether`](https://github.com/datatogether/datatogether/blob/master/CONDUCT.md).
The template can be extended to cover project- or repo- specific requirements.

### Issue Template

Our [`ISSUE_TEMPLATE.md` template](./templates/ISSUE_TEMPLATE.md) is intended
to help triage issues opened for service and package repositories. Additional
documentation, frequently asked questions, and supports can be added.

## Style Guidelines

We have a minimal set of style guidelines we follow to prevent confusion and 
maintain a consistend pattern to aid outreach and onboarding newcomers!

- Our project name is "Data Together" with a space between the words
- Golang repository names, folders, and code should be lowercase snakecase 
(`like_this`)
- Readme, license, and "github files" should be UPPERCASE (e.g., `CONDUCT.md`, 
`README.md`, `CONTRIBUTING.md`, `ISSUE_TEMPLATE.md`, `LICENSE`)
- We hide GitHub stuff (`CONTRIBUTING.md`, `ISSUE_TEMPLATE.md`) in a `.github` 
folder within every repository
- Aside from code, en-dashes "-" are fine for many things including GitHub labels, 
tags, and more!
