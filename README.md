# Zendesk Anchorfixer & TOC Generator

**Zendesk Anchorfixer** and **TOC Generator** are web-based tools that enhance the HTML of Zendesk Help Center articles by:

- Inserting named anchors directly inside each heading (`<h1>`–`<h4>`) using clean, human-readable slugs.
- Updating Table of Contents (TOC) links to use those readable slugs.
- Preserving Zendesk’s article link structure (`/hc/en-us/articles/{articleID}#slug`) when rewriting links.

---

## Why use these tools?

Zendesk automatically generates cryptic heading IDs (like `#h_01JWS7ABCDEF`) which makes section links unreadable.  
These tools rewrite them to friendly anchors like `#create-a-list`, making your articles easier to navigate and link to.

They also fix outdated or manually created TOCs by rewriting them with the correct slugs and URL format.

---

## Recommended Workflow

1. **Create your Zendesk article** in the Zendesk editor.
2. **Click the "HTML" button** (in the editor toolbar) to open the source view.
3. **Copy the full HTML.**
4. **Use the [TOC Generator](https://ronradzai.github.io/zendesk-tools/toc-generator.html)**  
   This tool will:
   - Insert named anchors inside headings.
   - Rewrite internal TOC links to use the correct format.
   - Automatically insert a flat TOC if one doesn’t already exist.
5. **Paste the updated HTML back into the Zendesk source editor.**
6. For later edits, you can use **[Anchorfixer](https://ronradzai.github.io/zendesk-tools/anchor-fixer.html)**  
   It updates anchors and links without changing your existing TOC.

---

## Features

### Anchorfixer
- Adds `name` and `id` attributes based on cleaned-up heading text.
- Avoids adding anchors to headings that already have valid `name` or `id` attributes.
- Updates **internal TOC links** to point to the correct slugs.
- Only rewrites links that point to the **current article**.
- Leaves external and cross-article links unchanged.
- Ignores blank headings or headings that contain only links.
- Works entirely in your browser — no data is sent anywhere.

---

### TOC Generator
- Includes all Anchorfixer functionality.
- Creates a **hierarchical Table of Contents** based on heading tag and order.
- Uses Zendesk-style TOC formatting:  
  `<p><a href="#slug">Heading Text</a></p>`
- Skips TOC creation if one already exists (detected by `<!-- TOC START -->`).
- Also rewrites existing TOC links if they point to the current article.
- Fully compatible with Zendesk’s required anchor formats in the new editor.

---

## Example

**Before:**

```html
<a href="/hc/en-us/articles/1234567890#h_01ABCDEF1234567">Create a List</a>
<h2 id="h_01ABCDEF1234567">Create a List</h2>
```

**After:**

```html
<a href="/hc/en-us/articles/1234567890#create-a-list">Create a List</a>
<h2 id="h_01ABCDEF1234567">
  <a name="create-a-list" id="create-a-list"></a>Create a List
</h2>
```

---

## Example Generated TOC

```html
<!-- TOC START -->
<p><a href="#create-a-list">Create a List</a></p>
<p><a href="#manage-your-list">Manage Your List</a></p>
<!-- TOC END -->
```

---

## Live Tools
- **Anchorfixer:** https://ronradzai.github.io/zendesk-tools/anchor-fixer.html
- **TOC Generator:** https://ronradzai.github.io/zendesk-tools/toc-generator.html

## **License**
MIT License - free to use and modify.

