# Contributing

  - [Codeblocks and Details](#codeblocks-and-details)
  - [Table of contents](#table-of-contents)
  - [Article names](#article-names)

## Codeblocks and Details

When typing code longer than several lines and in order to prevent cluttering the article with commands/json wrap your code into an HTML `details` tag, that will result into previewing it like this:

<details markdown="1">
  <summary style="color: #e67e22; font-weight: bold;">See commands</summary>

```mcfunction
# Command blocks
say this is a command
```
</details>

This is acomplished by typing this

````html
<details markdown="1">
  <summary style="color: #e67e22; font-weight: bold;">See commands</summary>

```mcfunction
# Command blocks
say this is a command
```
</details>
````

## Table of contents

Below the title of each new article add a table of contents, like how it's done in every article for better navigation. For example:

```markdown
  - [Java](#java)
    - [Target selector](#target-selector)
    - [Predicate](#predicate)
  - [Bedrock](#bedrock)
    - [Commands](#commands)
    - [Behavior Packs](#behavior-packs)
```

## Article names

Keep the article names all lowercase without any separator between worlds, like how it's done in all existing articles.