---
title: "Created Date of the Note"
tags:
  - date
  - time
---

# How to explicitly set the date and time displayed for notes in the Notes List

This solution is prompted by an Android API limitation:

> Creation date is not possible for all notes as android system does not provide an api for creation date of a file. More so, it would be impossible to get creation date for notes that are synchronized.
> 
> https://github.com/damionx7/Zettel-Notes-Documentation/issues/392#issuecomment-2844946465

There are two ways to set the note creation time:

## Method 1: Set the note filename in the `yyyyMMddHHmmss.md` format

To automatically generate a filename in the `yyyyMMddHHmmss.md` format (you might have chosen a different file extension for notes), use the repository settings.

In the repository settings: **Repositories** --> **Edit Repository** --> in the **Date Format** field, enter `yyyyMMddHHmmss`.

**IMPORTANT:**
After making changes in the repository settings window, be sure to click **Save** in the lower right corner.

New note files will display your current system date and time at the moment of note creation in the **Notes List**.

## Method 2: Set the `date: $$yyyyMMddHHmmss$$` parameter in the YAML frontmatter

There are two options for automatically generating the note creation date and time.

### Option 1. In the repository settings

**Repositories** --> **Edit Repository** --> in the **Default Text** field, create a YAML frontmatter block like this:

```
---
date: $$yyyyMMddHHmmss$$
---
```

If a YAML frontmatter already exists, then add or edit the `date: $$yyyyMMddHHmmss$$` parameter within it.

**IMPORTANT:**
After making changes in the repository settings window, be sure to click **Save** in the lower right corner.

New note files will display your current system date and time at the moment of note creation in the **Notes List**.

### Option 2. In a template

**Templates** --> **Edit Template** create a new template, or edit an existing one, so that its YAML frontmatter contains the parameter `date: $$yyyyMMddHHmmss$$`. For example:

```
---
title: "$title$"
date: $$yyyyMMddHHmmss$$
tags:
---

# $title$

```

**IMPORTANT:**
After making changes in the template settings window, be sure to click **Save** in the lower right corner.

Templates can use the `DEFAULT_TEXT` variable. This variable might already contain the `date: $$yyyyMMddHHmmss$$` parameter set in the repository settings. Avoid duplication.

The new note file will display your current system date and time at the moment of note creation in the **Notes List**.

## The **Notes List** will show the **Last Modified** date and time (from the "Info" window) if:

1. The filename does not start with `yyyyMMddHHmmss`;
2. The note's YAML frontmatter lacks the `date: $$yyyyMMddHHmmss$$` parameter.

## How to configure the date and time display format

You can configure your own date and time display format for the **Notes List**, **Gallery**, and **Recycle Bin** views via **Settings** --> **Theme** --> **Misc** --> **App-Wide Date Format**.