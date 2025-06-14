# Zendesk Anchorfixer

**Zendesk Anchorfixer** is a simple web-based tool that enhances the HTML of Zendesk Help Center articles by:

- Inserting named anchors directly inside each heading (`<h1>`–`<h6>`) using clean, human-readable slugs.
- Updating all Table of Contents (TOC) links to point to those new slugs instead of Zendesk’s autogenerated hash IDs (like `#h_01JWS7ABCDEF`).

## Why use this?

Zendesk generates cryptic heading IDs, making URLs long and unreadable when linking to a section. This tool gives you anchor links like `#create-a-list` instead of `#h_01JWS73ND8SYFD6WJRHRQ8DXQV`, improving readability and usability.

## How to Use

1. Create your Zendesk article normally in the Zendesk UI.
2. (Optional) Use the built-in TOC generator.
3. Click the `</>` (source code) button and copy the full HTML.
4. Open `index.html` (Zendesk Anchorfixer) in your browser.
5. Paste the HTML into the input box.
6. Click **Fix Anchors**.
7. Copy the updated output and paste it back into the Zendesk source editor.

## Features

### Anchorfixer
- Adds `name` and `id` attributes using slugified heading text.
- Avoids duplicate anchors if one already exists.
- Updates internal TOC links to match the new slugs.
- **Only rewrites links that point to the current article.**
- Leaves external and cross-article links unchanged.
- Works entirely client-side—no data is sent anywhere.

### TOC Generator
- Adds named anchors just like Anchorfixer.
- Creates a flat Table of Contents using the same slug logic.
- **Skips TOC creation if one already exists (`<!-- TOC START -->`).**
- **Also rewrites existing TOC links (if they point to the same article).**


## Example

**Before:**

```html
<a href="/hc/en-us/articles/1234567890#h_01ABCDEF1234567">Create a List</a>
<h2 id="h_01ABCDEF1234567">Create a List</h2>
```

**After (using Anchorfixer):**

```html
<a href="/hc/en-us/articles/1234567890#create-a-list">Create a List</a>
<h2 id="h_01ABCDEF1234567"><a name="create-a-list" id="create-a-list"></a>Create a List</h2>
```



## TOC Generator (Bonus Tool)

We also offer a second tool that creates a flat Table of Contents based on your article’s headings. It:

- Follows the same anchor-slug rules as Anchorfixer.
- Preserves heading order.
- Outputs Zendesk-style flat TOC using `<p><a href="#...">...</a></p>` format.

To use:

1. Paste your article HTML into `toc-generator.html`.
2. Click **Generate TOC**.
3. Copy and paste the TOC into the top of your Zendesk article.

**Example Output:**

```html
<p><a href="#create-a-list">Create a List</a></p>
<p><a href="#manage-your-list">Manage Your List</a></p>
```

## Live Demo

Use the tool directly in your browser:

- [Anchorfixer](https://ronradzai.github.io/zendesk-tools/anchor-fixer.html)
- [TOC Generator](https://ronradzai.github.io/zendesk-tools/toc-generator.html)


## **License**
MIT License - free to use and modify.

