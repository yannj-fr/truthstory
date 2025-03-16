# Liberation.fr Article Page Structure

This document details the HTML structure and data extraction methods for Liberation.fr article pages.

## Article URL Pattern
Articles follow this URL pattern:
```
https://www.liberation.fr/[section]/[article-title]-[date]_[article-id]/
```
Example:
```
https://www.liberation.fr/politique/service-national-universel-macron-annoncera-une-grande-refonte-dans-les-prochaines-semaines-20250315_P5JY6GPYOFBCVBMWXVFWIHWJNQ/
```

## Article Structure

### 1. Article Header
The header section contains essential metadata about the article:

#### Title
```html
<h1 class="article-headline">
  Service national universel : Macron annoncera «une grande refonte» dans «les prochaines semaines»
</h1>
```

#### Subtitle/Description
Located in a paragraph element immediately after the title:
```html
<div class="article-description">
  Dans un entretien accordé à plusieurs quotidiens régionaux ce samedi 15 mars, le Président a déclaré qu'il allait réformer le SNU en fonction des «besoins de la nation et aux priorités identifiées».
</div>
```

#### Publication Info
```html
<!-- Authors -->
<div class="article-authors">
  <span>par</span>
  <a href="/auteur/[...]">LIBERATION</a>
  <span>et</span>
  <a href="/auteur/[...]">AFP</a>
</div>

<!-- Publication Date -->
<div class="article-date">
  <time>publié le 15 mars 2025 à 19h58</time>
</div>
```

### 2. Article Image
```html
<figure class="article-main-image">
  <div class="image-container">
    <img src="[image-url]" alt="[image-description]" />
  </div>
  <figcaption>
    <div class="caption-text">Le 11 novembre 2024 à Perpignan.</div>
    <div class="credit">(JC Milhet/Hans Lucas. AFP)</div>
  </figcaption>
</figure>
```

### 3. Article Content

#### Main Content Container
```html
<article class="article-content">
  <!-- Article paragraphs -->
  <div class="article-body">
    <p>Emmanuel Macron a affirmé dans un entretien publié ce samedi 15 mars...</p>
    <!-- Additional paragraphs -->
  </div>
</article>
```

#### Quotes
Quotes are marked with special formatting:
```html
<span class="article-quote">«dans les prochaines semaines une grande refonte»</span>
```

#### Internal Links
```html
<a href="/[section]/[article-path]" class="article-link">
  Service national universel
</a>
```

### 4. Related Content

#### Tags Section
```html
<div class="article-tags">
  <h2>Pour aller plus loin :</h2>
  <div class="tags-list">
    <a href="/tag/[tag-url]">Service national universel (SNU)</a>
    <a href="/tag/[tag-url]">Emmanuel Macron</a>
    <!-- Additional tags -->
  </div>
</div>
```

#### Related Articles
```html
<section class="related-articles">
  <h2>Dans la même rubrique</h2>
  <div class="articles-grid">
    <article class="related-article">
      <div class="article-type">Court-circuit</div>
      <h3><a href="[article-url]">[Article Title]</a></h3>
      <div class="article-date">16 mars 2025</div>
    </article>
    <!-- Additional related articles -->
  </div>
</section>
```

### 5. Sharing Options
```html
<div class="sharing-buttons">
  <button type="button" title="Offrir un article">
    <img alt="gift" src="[icon-url]" />
  </button>
  <button type="button" title="Partagez par email">
    <img alt="email" src="[icon-url]" />
  </button>
  <button type="button" title="Copier le lien">
    <img alt="link" src="[icon-url]" />
  </button>
  <!-- Additional share buttons -->
</div>
```

## Data Extraction Guidelines

### 1. Article Metadata
- **Title**: Extract from the h1.article-headline element
- **Description**: Get text from div.article-description
- **Authors**: 
  - Parse the article-authors div
  - Handle multiple authors separated by "et"
  - Remove "par" prefix
- **Publication Date**: 
  - Extract from time element
  - Parse French date format "publié le [day] [month] [year] à [time]"
  - Convert to ISO format

### 2. Article Content
- **Main Text**:
  - Extract paragraphs from article-body
  - Preserve quotes with their special formatting
  - Maintain paragraph structure
  - Keep internal links with their href attributes

### 3. Images
- **Main Image**:
  - URL from img src attribute
  - Caption from caption-text div
  - Credits from credit div
- **Additional Images**: Follow same pattern throughout article body

### 4. Related Content
- **Tags**: Extract all links from tags-list
- **Related Articles**: 
  - Title
  - URL
  - Publication date
  - Article type (if present)

## Special Cases

### 1. Premium Content
Some articles may be marked as premium/subscriber-only content. Look for:
```html
<div class="subscriber-only">
  <!-- Premium content indicator -->
</div>
```

### 2. Multi-page Articles
For articles split across multiple pages:
- Look for pagination elements
- Follow "next page" links
- Combine content from all pages

### 3. Live Updates
For live coverage articles:
- Each update has its own timestamp
- Updates are in reverse chronological order
- May have embedded tweets or media

## Error Handling

1. **Missing Elements**:
- Title and main content are required
- Other elements (images, authors, etc.) are optional
- Log missing required elements as errors

2. **Invalid Dates**:
- Handle various date formats (absolute/relative)
- Validate dates are within reasonable range
- Fall back to article URL date if needed

3. **Broken Links**:
- Verify internal links are valid
- Log broken links as warnings
- Preserve link text even if URL is invalid