# code-standards

**This is a living document and subject to change.**
Please Note: On Acquia we will not be using their feature "Live Development" which would allow you to directly edit code on dev or stage.

##Code Review & Standards
For Drupal 8 we will generally refer to [Drupal 8 coding standards](https://www.drupal.org/docs/develop/standards)  and [Acquia has a nice general list](https://docs.acquia.com/blt/developer/code-review/).

In rare cases where blocks of text constructed dynamically in code utilize HEREDOC. PHP should not be used as a templating language.  Utilize Twig.

Search for and remove all dead code.
Dead code is defined as:
- Commented Methods
- Uncalled(Unused) Methods
- Unused Includes
- Unused Variables (Local, Properties, Fields, etc.)
- Unused References (plugins, Packages, libraries, etc.)
- Unused Files (Classes, Resource Files, Style Sheets, JavaScript, etc.)

Ternary operations should be limited to 80 characters. Do not stack ternary operations.  If it is suitably complex, use a full if statement for clarity.

## Git Best practices
New to Git? [Read chapters](https://git-scm.com/book/en/v2) [2](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository), [3](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell), [7.3](https://git-scm.com/book/en/v2/Git-Tools-Stashing-and-Cleaning)
Between every step it is advised to get in the habit of typing `git status`. This handy bit lets you know where and when you are in your repo. If you have files that are not committing correctly, or caching incorrectly `git status` will make it clear.

The best practices for git should be followed from the [Aquia documentation on Git](https://docs.acquia.com/acquia-cloud/develop/repository/git/). 

### Line Endings and Whitespace
Windows likes to be helpful, sometimes too helpful.  Please refer to [formatting whitespace](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration#_formatting_and_whitespace) and run the global git command:
`git config --global core.autocrlf true` 
If using a windows machine to program, the command will auto change carriage return line endings to linefeed on commit. Fairly certain this command only need be run once per windows developer machine.

### Committing branch changes suggestions
Whenever you want to commit your changes back to the code repository for the branch you’re working on, run the following commands to commit the change locally:

Stage all files using your preferred commands:
- `git add -A`  add all changed files
- Or `git add <file path>`  repeat for each file to be added

Use `git status` here to confirm nothing went awry in adding files.

After all files are staged for commit run `git commit` and do not use the `-m` tag unless it is truly a one line change.  Running the commit command without the '-m' flag will open your text editor, usually vi or vim default on Unix.

###A note about commit messages

In most cases one line commit messages are not comprehensive enough for what a peer must be reviewing. Good commit messages are part information part art.

A message might have this kind of format
```
[SHORT SUBJECT - Ideally less than 80 char.]
[SKIP A LINE]
[Longer paragraph style explanation of the commit.]
[If other developers need credit, skip a line and recognize their hard work]
```
Using words like "add", "fix", "Change", "update" in the summary can tell your code reviewer lots about what they should be reviewing. A list can be nice.

[This article](https://chris.beams.io/posts/git-commit/) has some nice information about commit messages. Please give it a read.

tldr: rules from above article:
1. Separate subject from body with a blank line
1. Limit the subject line to 50 characters Maximum 80 characters
1. Capitalize the subject line
1. Do not end the subject line with a period
1. Use the imperative mood in the subject line
1. Wrap the body at 72 characters
1. Use the body to explain what and why vs. how

This recommendation on commit messages not hard and fast rules; No more than 1 paragraph in a commit. If a commit message becomes to large, it may be a sign that work needs to be committed more often to the repo. Large commit messages should be reserved for a squashed feature commit.

Writing a good commit message makes reviewing code better for peers and in the event that commits are ever 'squashed' into a finalized feature the clear subjects can optionally become the new feature commit message. 

##SASS over CSS
One of the main problems with css is it can become messy and unmanageable over time. Solution? SASS.  In a SASS we can write CSS in a hierarchical way. We can also create variables and mix-ins.  No more having to hunt down 30 instances of `color: #cf0f12;` to change them all to `color: 336aaf;`. We can have a variable named `$gutter`, set it to 5px and ensure that every box has the right sized gutters on it.

###Installing  [Sass](https://sass-lang.com/install)
You can install Sass on Windows, Mac, or Linux by downloading the package for your operating system [from GitHub](https://github.com/sass/dart-sass/releases/tag/1.22.10) and adding it to your PATH. That’s all—there are no external dependencies and nothing else you need to install.

PhpStorm can set up file watchers while you are making edits to your theme.

##Composer

Composer is the PHP package manager these days. Arguably one of the best things that has happened to PHP. Drupal 8 and some Acquia products depend upon it. Composer is the NuGet of the php world.

###Install composer 
Acquia Dev desktop ships with composer and php.  If you want to run Composer locally, install php 7.2+ and add php to your widnows PATH. Go to the composer page and download the windows exe and install. https://getcomposer.org/doc/00-intro.md#installation-windows




