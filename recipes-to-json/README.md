# Recipe Conversion Agent

## What It Does
Converts recipe content from any text format directly to structured JSON files using the schema.org/Recipe standard.

**Accepts:** Plain text, DOCX content, structured or unstructured recipe text  
**Outputs:** schema.org/Recipe compliant JSON files  
**Use Cases:** Web deployment, SEO optimization, recipe databases

## How to Use

### Basic Conversion

1. **Start the agent** by referencing the configuration:
   ```
   @agent.md - I need to convert recipes to JSON
   ```

2. **Paste your recipe** with this prompt:
   ```
   Convert this recipe to schema.org JSON format:
   [paste recipe text here]
   ```

3. **Done!** JSON file is created in the current directory.

### Custom Output Directory
```
Convert this recipe to JSON and save it in C:\Recipes\output:
[paste recipe text]
```

### Batch Conversion
```
I have 10 recipes to convert:

Recipe 1:
[text]

Recipe 2:
[text]
...
```

## What You Can Provide

**Any text format works:**
- Copy-paste from websites
- Word document text
- Plain text with clear sections
- Even unstructured paragraph format

**The agent will extract:**
- Recipe name
- Ingredients with measurements
- Instructions/steps
- Prep/cook times
- Servings, categories, nutrition info
- Author, notes, variations

## Example Output

```json
{
  "@context": "https://schema.org",
  "@type": "Recipe",
  "name": "Chocolate Chip Cookies",
  "recipeYield": "24 cookies",
  "prepTime": "PT15M",
  "cookTime": "PT12M",
  "recipeIngredient": [
    "2 cups all-purpose flour",
    "1 cup butter, softened",
    "..."
  ],
  "recipeInstructions": [
    {
      "@type": "HowToStep",
      "text": "Preheat oven to 350°F..."
    }
  ]
}
```

## Tips

- Include as much detail as possible (times, servings, author, etc.)
- Don't worry about formatting - paste as-is
- For batches, process 10 recipes at a time
- Specify output directory if you don't want current directory

## Additional Features

- Generate URL-encoded file lists for web deployment
- Update existing recipes with new information
- Batch process multiple recipes at once

## Resources

- **Full Documentation**: See `agent.md` for complete schema reference
- **Schema.org Recipe**: https://schema.org/Recipe
- **JSON Validator**: https://jsonlint.com/
