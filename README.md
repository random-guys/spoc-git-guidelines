# SPOC Git dev Guidelines

# Overview

The product org engineering team tries to follow the *conventional commits guideline.* You can find out more about the conventional commits specification here: [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.2/#summary)

**Note**: we do differ from the convention in some areas, namely in the use of a footer in commit messages and in some of the keywords 

# Commit Messages

A commit message should typically consist of a header and an optional body separated by a blank line. This should give a simple and succinct description of what's been changed. Avoid commit message lines longer than 100 characters. 

## Header

---

The message header is a single line that contains a concise description of the change containing a type, an optional scope, and a subject. This would typically tend to look like the sample syntax below: 

```jsx
<type>[optional scope]:<description>
<BLANK LINE>
[optional body]
```

### Types

This is typically a noun that describes the kind of change that the commit makes. Valid types are: 

- **feat (feature):**
a change that introduces a new feature to the codebase that an end user will impact from

- **fix (bug fix):**
patches a bug or any otherwise unintended behaviour in your codebase

- **style (formatting):**
any change that runs a linter or only adds formatting changes in the code's appearance. e.g. fixing indentation, white-space, adding/removing semicolons, removing commented out code etc.

- **docs (documentation):**
a change to the documentation of a codebase e.g. changes to READMEs, adding code comments/documentation etc.
- **ref (refactor):**
Updating an already existing method of doing things. Either to simplify the code logic or improve code readability without affecting a codebase's externally perceived behaviour. *[The formal definition of a refactor](https://refactoring.com/)*.
- **test (when messing with tests):**
changes to tests, either adding tests or updating them
- **deploy (deployment):**
changes to CI or deployment configuration files and scripts (example scopes: Circle, Docker/Docker compose, Netlify, Heroku, Surge) etc.
- **chore (general maintenance):**
the chore tag can be used for changes that involve general maintenance (e.g. updating content text) or simply as a general type for anything that doesn't quite fit into the other types on this list

### Scope - [optional]

The scope can be anything specifying what area of the project the commit changes. For example [authorisation], [authentication], [dashboard], [login], [referrals]

### Description

This is a very short description of the change. There aren't many hard rules to follow here other than general suggestions.:

- try to point out the problem being solved
- no full stop/dot (.) at the end
- no need  to capitalise the first letter

## Body - [optional]

---

There are sometimes cases where a header description does not fully describe all the changes introduced by a commit. In times like these, consider adding ****a **message body**! 

The header and body both need to be separated by one black line and is entirely optional.

```bash
<header>
<BLANK LINE>
<Body>
```

Message bodies can take any form such as bullet points, links to relevant websites, your thoughts... There is no real convention here and is yours to make your own.

[A Note About Git Commit Messages](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)

For a more detailed description on what can possibly be in a message body

## Example commit messages

---

```bash
feat: info route is too slow

Added a cache to reduce query times by 80%. Note that this cache means the 
production system would need multiple redis server instances
```

```bash
feat:[questions] there's no endpoint for deleting security questions
```

```bash
chore[vendor page]: 

- updates with new names from product owner
```

```bash
docs: add code documention to user controller

- add code comments to /login flow
- add documentation comments to methods
```

```bash
docs[README]: about section is out of date
```

# Workflow - Adding features

1. Create a feature branch

    ```bash
    # checkout to the local version of staging
    git checkout develop
    git checkout -b type/feature # where types is one of fix/feat/ref(actor)/chore
    ```

2. Solve a problem and write a test for that solution

    ```bash
    feat: What you did, better still what problem you're trying to solve
    ```

3. Push code

    ```bash
    git push origin type/problem-topic
    ```

4. From Github, create a new pull request to the staging branch one of @Kunle Arewa, @Raymond Tukpe, @Chudi Oranu or @Kolapo Oni as reviewer.

5. To integrate first:

    ```bash
    git checkout develop
    git pull # get the latest merged code
    ```

# Pull Requests (PR) Guidelines

Be contextual and descriptive: What does this pull request do?

Examples:

```
This sends an email when...
```

```
This refactors how and when we generate request ids...
```

```
This fixes a CSS issue where...
```

## Provide some context on why work is happening

Examples:

```
Right now we have to manually send an email to (me@example.com), this automates that process...
```
```
On Firefox, buttons would not always look consistent with designs and other browser implementations...
```

```
The current codebase file structure is difficult to understand and makes changes risky...
```
