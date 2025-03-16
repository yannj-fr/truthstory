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

### Search URL Structure
- Base search URL: https://www.liberation.fr/recherche/
- Query parameters:
  * query={search_term} - Required, the search keyword
  * sortby=date - Optional, sorts by date (default is relevance)
  * page={number} - Optional, for pagination

### Search Results Structure

#### Results Container
- Main container: main[role="main"] section
- Search info header: Shows "Affichage de X résultats pour 'search_term'"
- Results list: Located within main section after filters

#### Article Elements
Each article in the results list contains:
```html
<generic>
  <link>
    <!-- Article title and link -->
    <generic>
      <generic>
        <StaticText>ARTICLE_TITLE</StaticText>
      </generic>
    </generic>
    <!-- Date and author info -->
    <generic>
      <generic>
        <StaticText>DATE / par AUTHOR</StaticText>
      </generic>
      <StaticText>PREVIEW_TEXT</StaticText>
    </generic>
  </link>
</generic>
```

#### Data Extraction
1. Title: 
   - Found in first StaticText node within article link
   - Full title without truncation
   - Example: "Service national universel : Macron annoncera «une grande refonte» dans «les prochaines semaines»"

2. Date:
   - Located in second StaticText block before " / par "
   - Two possible formats:
     * Absolute: "DD mars YYYY" (e.g., "15 mars 2025")
     * Relative: "il y a X min/heures"

3. Author:
   - Follows " / par " in the date line
   - Can be multiple authors separated by "|"
   - Common formats:
     * Single: "par LIBERATION"
     * Multiple: "par LIBERATION|AFP"
     * Named authors: "par Jean-Baptiste Daoulas|Laure Equy"

4. Preview text:
   - Follows date/author line
   - Usually first 1-2 sentences of article
   - Ends with "..."

5. URL:
   - href attribute of the main article link
   - Format: https://www.liberation.fr/section/subsection/title-YYYYMMDD_ID/

#### Results Per Page
- Approximately 20 articles displayed per page
- Articles sorted by date (when sortby=date)
- Each article maintains consistent structure throughout pages

### Filtering Options
- Date filters (bid="806"):
  * Today: "Aujourd'hui (X)" - shows count in parentheses
  * One week: "Une semaine (X)"
  * One month: "Un mois (X)"
  * One year: "Un an (X)"
  * Custom range: date pickers for start and end dates
- Section filters (bid="823"):
  * Shows sections with article counts in parentheses
  * Examples: Politique (8235), Société (5084), International (2915)
- Author filters (bid="865"):
  * Lists authors with article counts
  * Examples: LIBERATION (5235), AFP (3464)

### Sort Options
- Dropdown menu with:
  * "Pertinent" (Relevance) - default
  * "Récent" (Recent)

### Pagination
- "Suivante" (Next) link at bottom of results (bid="1059")
- Current page indicator in URL parameter: page=X

## Authentication
- Authentication endpoint: https://authentification.liberation.fr/
- Handle subscriber-only content
- Paywall detection
- Cookie management
- Login form fields:
  * Email field: bid="43"
  * Password field: bid="53"
  * Submit button: bid="62"
- After successful login, user is redirected to homepage https://www.liberation.fr/

## Popup Handling
- Advertisement popup appears on first visit
  - Appears with text "Offre spéciale: 3 mois pour 5€" 
  - Close button available as a cross (×) icon in the top-right corner (element bid="e13")
  - Also has "Je m'abonne" (Subscribe) button
- Close popup by clicking the cross icon button
- After closing, the main content of the page becomes accessible