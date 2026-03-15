# Recipe Conversion Project - Agent Settings

## Project Overview
Converting recipe content directly to JSON (schema.org/Recipe format) for web deployment.

**Accepted Input Formats:**
- Plain text (copy-paste from websites, documents, etc.)
- DOCX files (copy text content)
- Word documents (copy text content)
- Any structured text with identifiable recipe sections (ingredients, instructions, etc.)
- Unstructured paragraph-style recipes

**Output Format:**
- JSON files using schema.org/Recipe standard

## Directory Structure

**Default Output:** Current directory (where the agent is running)

```
./
├── Recipe 1.json
├── Recipe 2.json
└── ...
```

**Alternative:** Specify a custom output directory
```
C:\path\to\Recipes/
```


## Schema.org/Recipe Format

### Required/Common Fields
```json
{
  "@context": "https://schema.org",
  "@type": "Recipe",
  "name": "Recipe Name",
  "recipeYield": "X servings",
  "recipeCategory": "Main Course|Side Dish|Dessert|Appetizer|Beverage|Condiment",
  "recipeCuisine": "Italian|Mexican|Asian|Thai|Japanese|Cajun|Southern|etc",
  "recipeIngredient": [
    "ingredient 1",
    "ingredient 2"
  ],
  "recipeInstructions": [
    {
      "@type": "HowToStep",
      "text": "Step description"
    }
  ]
}
```

### Optional Fields (use when available)
- `"author"`: `{ "@type": "Person", "name": "Author Name" }`
- `"description"`: Brief description or notes about the recipe
- `"prepTime"`: ISO 8601 duration format (e.g., `"PT15M"` for 15 minutes)
- `"cookTime"`: ISO 8601 duration format (e.g., `"PT2H"` for 2 hours)
- `"totalTime"`: ISO 8601 duration format
- `"cookingMethod"`: "Baking", "Grilling", "Slow cooking", "Stir-frying", etc.
- `"alternateName"`: Alternative recipe name
- `"nutrition"`: Nutritional information object
  ```json
  "nutrition": {
    "@type": "NutritionInformation",
    "calories": "600 calories",
    "proteinContent": "45g",
    "carbohydrateContent": "58g",
    "fatContent": "20g"
  }
  ```

### ISO 8601 Duration Format Examples
- `"PT15M"` = 15 minutes
- `"PT1H"` = 1 hour
- `"PT2H30M"` = 2 hours 30 minutes
- `"PT45M"` = 45 minutes
- `"PT3H"` = 3 hours

## Text Parsing Guidelines

### Identifying Recipe Sections
When parsing recipe text in any format, look for common section markers:
- **Recipe Name**: Usually the first line or heading
- **Ingredients**: Keywords like "Ingredients", "What You Need", ingredient lists with measurements
- **Instructions**: Keywords like "Instructions", "Directions", "Steps", "Method", "Preparation"
- **Metadata**: Servings, yield, prep time, cook time, calories, author
- **Notes**: Keywords like "Notes", "Tips", "Variations", "Storage"

### Handling Different Text Formats
- **Structured text** (clear sections): Parse each section into appropriate JSON fields
- **Unstructured text** (paragraph format): Extract ingredients and steps intelligently
- **Mixed formatting**: Adapt to whatever structure is provided
- **Missing information**: Include only available fields, omit optional fields

## Conversion Guidelines

### Ingredients
- Keep original measurements and formatting
- Preserve all ingredient details (brand names, optional ingredients, etc.)
- Include parenthetical notes: `"1 tablespoon chili powder (optional)"`

### Instructions
- Each step is a separate `HowToStep` object
- Combine related sub-steps if they're part of the same action
- Preserve cooking temperatures, times, and specific techniques
- Optional: Use `"name"` field in HowToStep for section headers (e.g., "Skillet", "For the Sauce")

### Notes and Variations
- Include recipe notes, tips, and variations in the `"description"` field
- Preservation/storage instructions can go in the last instruction step or description

### Recipe Categories
Common categories used:
- Main Course
- Side Dish
- Dessert
- Appetizer
- Beverage
- Condiment
- Seasoning
- Preparation (for brines, etc.)

### Cooking Methods
Common methods used:
- Baking
- Grilling
- Slow cooking
- Stir-frying
- Pan-frying
- Pan-searing
- Roasting
- Broiling
- Simmering
- Steaming
- No-cook
- One-pot cooking

## PowerShell Conversion Pattern

When creating JSON files in PowerShell, use this pattern:

**Default (current directory):**
```powershell
@'
{
  "@context": "https://schema.org",
  "@type": "Recipe",
  "name": "Recipe Name"
  // ... rest of JSON
}
'@ | Out-File -FilePath "Recipe Name.json" -Encoding UTF8
```

**Custom directory (if specified by user):**
```powershell
$outputDir = "C:\path\to\recipes\json-converted"  # Use path provided by user

@'
{
  "@context": "https://schema.org",
  "@type": "Recipe",
  "name": "Recipe Name"
  // ... rest of JSON
}
'@ | Out-File -FilePath "$outputDir\Recipe Name.json" -Encoding UTF8
```

## Current Recipe Count
- Total recipes: 38+ (as of last update)
- Stored in current directory by default (or custom directory if specified)

## Batch Processing
When processing multiple recipes:
- Process 10 recipes at a time in PowerShell for better management
- Use Write-Host to track progress
- Verify files created with `ls` command after batches

## Special Cases Handled
1. **Empty/minimal recipe text**: Create basic JSON with just name field
2. **Recipe variations/notes**: Include in `description` field
3. **Multiple cooking methods**: List primary method in `cookingMethod` field
4. **Ingredient lists with sub-headers**: Keep all items as flat array in `recipeIngredient`
5. **Special characters in filenames**: Preserved as-is (e.g., `Chili_s`, apostrophes, ampersands)

## Files Updated After Initial Creation
- Umbra's Chili.json - Updated with full recipe
- Chorizo Queso Mac n' Cheese.json - Updated with full recipe
- Papa's Cranberry Relish.json - Updated with full recipe
- Baked Ziti.json - Added as new recipe
- Crockpot Venison Stew.json - Added as new recipe

## Best Practices
1. Always read/analyze the recipe text first to understand the structure
2. Parse text to identify recipe sections (ingredients, instructions, metadata)
3. Preserve all original details (measurements, temperatures, times)
4. Use appropriate recipe categories and cuisines when evident
5. Include nutritional information when provided in source
6. Maintain consistent formatting across all JSON files
7. Use UTF8 encoding for all files to preserve special characters
