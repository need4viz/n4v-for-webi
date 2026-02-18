# Schema.org Structured Data Templates for need4viz.com

These JSON-LD files are ready to be inserted into the `<head>` section of your website pages.

## Files

| File | Schema Type | Where to use |
|------|-------------|--------------|
| `organization.jsonld` | `Organization` | Homepage (need4viz.com) and About page |
| `software-application.jsonld` | `SoftwareApplication` | Solution page and Pricing page |
| `faq-page.jsonld` | `FAQPage` | FAQ page or SAP Web Intelligence Extensions page |

## How to integrate

### Option 1: Direct embed (recommended)

Copy the content of each `.jsonld` file and wrap it in a `<script>` tag in your page's `<head>`:

```html
<script type="application/ld+json">
{
    "@context": "https://schema.org",
    "@type": "Organization",
    ...paste content here...
}
</script>
```

### Option 2: WordPress plugin

If using a WordPress SEO plugin (Yoast, Rank Math, etc.), you can paste the JSON-LD content into the plugin's structured data section.

## Testing

Validate your structured data using:
- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Schema.org Validator](https://validator.schema.org/)

## What this enables

- **Organization Knowledge Panel**: Google may display a knowledge panel for "Need4Viz" in search results
- **Software Rich Snippets**: Product info, pricing, reviews displayed in search results
- **FAQ Rich Results**: FAQ questions appear directly in Google search results, increasing click-through rates
- **Enhanced SERP presence**: More real estate in search results = more visibility
