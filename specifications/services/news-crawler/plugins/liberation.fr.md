Plugin specification for Liberation.fr (https://www.liberation.fr)

## Website Structure
- Homepage: https://www.liberation.fr
- Article URL pattern: https://www.liberation.fr/[section]/[article-name]
- Search URL pattern: https://www.liberation.fr/recherche/?query=[search-term]

## Crawling Rules
- Ignore robots.txt restrictions
- Rate limiting: 1 request per 2 seconds
- Cookie consent handling required
- Paywall detection and handling

## Content Extraction
- Article title: h1.article__title
- Publication date: meta[property="article:published_time"]
- Author: span.author__name
- Content: div.article-body
- Categories: meta[property="article:section"]
- Tags: meta[property="article:tag"]

## Search Capabilities
- Search by keyword
- Search by date range
- Search by category
- Results pagination handling

## Authentication
- Handle subscriber-only content
- Paywall detection
- Cookie management

## Popup Handling
- Advertisement popup appears on first visit
  - Appears with text "Offre spéciale: 3 mois pour 5€" 
  - Close button available as a cross (×) icon in the top-right corner (element bid="e13")
  - Also has "Je m'abonne" (Subscribe) button
- Close popup by clicking the cross icon button
- After closing, the main content of the page becomes accessible