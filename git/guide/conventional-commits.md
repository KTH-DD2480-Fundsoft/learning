# Conventional Commits

The Conventional Commits specification is a much better way to create commit messages and is standard in many projects (*e.g., the Angular framework*). To summarise, the specification specifies that commit messages should look like this:

```
<type>(<optional scope>)<!>: <description>
<BLANK LINE>
<optional body>
<BLANK LINE>
<optional footer(s)>
```

Let's break this down:

## Type
The `<type>` part describes what type of commit it is. Strongly related to the branch prefix. The specification specifies that the types `feat` and `fix` must be used when a new feature is introduced (*corresponds to minor version in semantic versioning*) and when a bug is patched (*corresponds to patch version in semantic versioning*), respectively. Other types can be introduced by the project. Popular types other than `feat` and `fix` are the following:
- `docs` - Documentation only changes.
- `style` - Changes that don't affect the meaning of the code (e.g. formatting).
- `refactor` - Refactoring only changes.
- `perf` - Performance improvement changes.
- `test` - Test-related contributions.
- `build` - Changes that affect the build system.
- `ci` - Changes to the CI configuration

## Scope

The `<optional scope>` part describes what area in the project the commit is related to, and is optional. The specification doesn't specify any reserved scopes so it is up to the project to establish possible scopes.

## Breaking-change indicator

The `<!>` part denotes an exclamation mark (!) that is included if the commit contains a breaking change (*corresponds to major version in semantic versioning*), and if so, then the exclamation mark (!) must be included right before the colon (:).

## Description

The `<description>` part is a concise description of the commit. There are some important points regarding this, which are not included in the specification but which are pretty much standard:
- Imperative, present tense is used: "add" not "added".
- No capitalisation of the first letter.
- No dot (.) at the end of the description

## Body

The `<optional body>` part is a more elaborate explanation on the motivation for the changes and then what changes were made, and is optional to include. There might be multiple paragraphs in the body each separated with blank lines. If the body is included, there must be a blank line before the body. In addition to the specification, some important standards are:
- Motivation for change
- Changes are written in imperative, present tense: "change" not "changed".
- May include explanations where different ticket/issue are mentioned and their relations explained.

## Footer
The  `(<optional footer(s)>)` part is a set of lines that points out specific data about the commit. The lines have one of the following formats:
    
1. `<footer-token>: <text>`
2. `<footer-token> #<string>`
3. `BREAKING CHANGE: <description`
    
A format of a `<footer-token>` are words separated with hyphens (-) instead of whitespace characters "Reviewed-by" not "Reviewed by".

The first format can be used to describe miscellaneous things about the commit, such as who reviewed it or what tickets are related to the commit. The second format can be used to for example say that a ticket is fixed, closed etc. The third format should be included when the commit includes a breaking change. However, if the breaking-change indicator `<!>` was included in the first line, then this footer may be omitted but then the commit description should describe the breaking change. Still, including this footer is highly recommended even if the breaking-change indicator was included.

## Example

A complete example of a commit change would be the following:

```
feat(database)!: add new indexing functionality to improve query performance

Motivation:
The introduction of a new indexing feature in the database module is driven by the need to enhance performance for large-scale data queries. This change is particularly aimed at addressing inefficiencies in data retrieval and processing, which have been significant hurdles in handling large datasets.

Introduce a new indexing feature for the database module. Significantly improve the performance of query operations, especially for large datasets. The indexing algorithm optimizes data retrieval and is adaptive based on query patterns.

BREAKING CHANGE: The database schema has been updated for the new indexing system, which is incompatible with previous versions. This means that databases will need to be migrated to the new schema format.

Resolves #1234
See-also: #1235, #1236
Co-authored-by: Jane Doe <jane.doe@example.com>

```