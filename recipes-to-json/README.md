# Recipe Conversion Agent - README

## Overview
This agent assists with converting recipe content from any text format directly to structured JSON files using the schema.org/Recipe standard, suitable for web deployment and SEO optimization.

## What This Agent Does
1. Converts recipe content from **any common text format** directly to schema.org/Recipe JSON format
2. Generates URL-encoded file lists for web deployment
3. Maintains consistent formatting across all recipe files

## Supported Input Formats
The agent can process recipes from:
- **Plain text** - Copy-paste from websites, emails, documents
- **DOCX files** - Copy text from Word documents
- **Structured text** - Any text with clear ingredients and instructions sections
- **Unstructured text** - Even paragraph-style recipes can be parsed

## Prerequisites

### Software Requirements
- **PowerShell**: Built-in on Windows (or PowerShell Core for cross-platform)

### Knowledge Requirements
- Basic understanding of JSON format
- Familiarity with PowerShell commands (helpful but not required)
- Understanding of recipe structure (ingredients, instructions, etc.)

## Quick Start Guide

### Text to JSON Workflow
The fastest way to convert recipes:

1. **Copy the recipe text** from any source (website, Word document, email, etc.)
2. **Paste it to the agent** with this prompt:
   ```
   Convert this recipe to schema.org JSON format:
   [paste recipe content here]
   ```
3. **Agent creates JSON file** in the current directory

That's it! No intermediate steps needed.

**To use a different output directory:**
```
Convert this recipe to JSON and save it in C:\Recipes\output:
[paste recipe content here]
```

### Generate URL Lists
To get a list of web URLs for your files:
```
Generate a URL list for files in [folder path] with base URL: https://example.com/recipes/
```

## How to Use the Agent.md File

### Before Starting a Session
1. **Mention the agent.md file** in your conversation:
   ```
   Please refer to @agent.md for recipe conversion standards
   ```

2. **Or upload/reference it** when starting:
   ```
   I'm continuing work on the recipe conversion project. See agent.md for context.
   ```

### During a Session
The agent.md file contains:
- **Schema format reference** - Copy-paste examples for consistent JSON structure
- **Field definitions** - What to include in each recipe field
- **Conversion patterns** - PowerShell templates for batch processing
- **Special cases** - How to handle edge cases (empty files, variations, etc.)

### Key Sections to Reference

#### Converting a New Recipe
1. Look at **Schema.org/Recipe Format** section for structure
2. Check **Conversion Guidelines** for how to format ingredients/instructions
3. Use **Recipe Categories** and **Cooking Methods** lists for consistent terminology

#### Batch Processing
1. Reference **PowerShell Conversion Pattern** section
2. Follow **Batch Processing** guidelines (10 at a time recommended)

#### Handling Special Cases
Check **Special Cases Handled** section for:
- Empty or minimal recipe files
- Recipe notes and variations
- Multiple cooking methods
- Unusual characters in filenames

## Common Workflows

### Workflow 1: Single Recipe Conversion (Most Common)
```
User: Convert this recipe to JSON:
[pastes recipe text from any source]

Agent: [Parses text to identify sections]
        [Reads agent.md for schema format]
        [Creates properly formatted JSON]
        [Saves to current directory or specified path]
```

**Example Input Formats:**
- Website copy-paste with clear sections
- Plain text with "Ingredients:" and "Instructions:" headers
- Unstructured paragraph format
- Recipe card text
- Word document text

### Workflow 2: Batch Recipe Conversion
```
User: I have multiple recipes to convert
  OR: I have text files with recipes, convert them all

Agent: [Reads all recipes provided]
        [Processes 10 at a time]
        [Creates JSON for each using schema.org format]
        [Reports progress]
```

### Workflow 3: Update Existing Recipe
```
User: Update [recipe name] with this new information:
[pastes updated recipe content]

Agent: [Reads existing JSON]
        [Updates with new information]
        [Maintains schema.org format]
        [Overwrites file with -Force flag]
```

### Workflow 4: Generate URL Lists
```
User: Give me a URL list for all JSON files with spaces encoded

Agent: [Lists all files in directory]
        [Generates URLs with %20 for spaces]
        [Provides complete list]
```

## Tips for Best Results

### 1. Be Specific About What You Need
✅ **Good**: "Convert this recipe to JSON: [paste recipe text]"
✅ **Better**: "Convert this recipe to JSON and save to C:\Recipes: [paste recipe text]"

❌ **Vague**: "Convert my recipes"

### 2. Provide Complete Information
When sharing a recipe to convert, include all available information:
- Recipe title/name
- Full ingredient list (with measurements)
- Complete instructions/directions
- Any notes, variations, or tips
- Serving size/yield
- Cooking/prep times
- Nutritional information
- Author name
- Recipe source/URL

**The agent will work with whatever you provide** - don't worry about perfect formatting!

### 3. Use Batch Processing for Large Sets
- Process 10 recipes at a time for better tracking
- Review output between batches
- Easier to catch errors early

### 4. Maintain Consistency
- Reference agent.md for terminology (recipe categories, cooking methods)
- Follow established patterns for similar recipes
- Use ISO 8601 format for durations (PT15M, PT2H, etc.)

### 5. Verify Output
After batch conversions, ask:
```
List all JSON files in the current directory to verify everything was created
```

## File Structure Reference

```
Project Root/
├── agent.md                          # Agent configuration and standards
├── README.md                         # This file
├── Recipe 1.json                     # Output JSON files (current directory by default)
├── Recipe 2.json
└── ...
```

**Or with custom output directory:**
```
Project Root/
├── agent.md
├── README.md
└── output/                           # Custom output directory if specified
    ├── Recipe 1.json
    ├── Recipe 2.json
    └── ...
```

## Schema.org/Recipe Quick Reference

### Minimal Recipe
```json
{
  "@context": "https://schema.org",
  "@type": "Recipe",
  "name": "Recipe Name",
  "recipeIngredient": ["ingredient 1", "ingredient 2"],
  "recipeInstructions": [
    {
      "@type": "HowToStep",
      "text": "Step 1 instructions"
    }
  ]
}
```

### Complete Recipe (All Optional Fields)
See the **Schema.org/Recipe Format** section in agent.md for complete field reference.

## Common Questions

### Q: Can I modify the JSON files manually?
**A:** Yes, but be sure to:
- Maintain valid JSON syntax
- Keep the @context and @type fields
- Use proper escaping for quotes and special characters

### Q: What if a recipe has missing information?
**A:** No problem! The agent will:
- Work with whatever information is available
- Include only the fields that have data
- Create minimal JSON (just name) for very incomplete recipes
- Parse even poorly formatted text to extract what it can
- Use the description field for notes about variations or missing info

### Q: What text formats work best?
**A:** Almost any format works:
- ✅ **Best**: Clear sections with "Ingredients" and "Instructions" headers
- ✅ **Good**: Structured text with measurements and steps
- ✅ **Okay**: Paragraph format - agent will parse it
- ⚠️ **Harder**: Images of recipes (need to OCR first, or type out)

### Q: Do I need to format the text before pasting?
**A:** No! Just paste it as-is. The agent will:
- Identify recipe sections automatically
- Parse ingredients from instructions
- Extract metadata (servings, times, etc.)
- Handle various formatting styles

### Q: How do I handle recipe variations?
**A:** Put variations in the `description` field, like:
```json
"description": "Classic chili recipe. For spicier version, add extra cayenne pepper. For vegetarian, substitute beans for meat."
```

### Q: Can I use this for non-recipe content?
**A:** This agent is optimized for recipes. For other content types, you'd need to:
- Define a different schema
- Update agent.md with new conversion rules
- Adjust the PowerShell patterns

### Q: What about images?
**A:** The current schema supports image URLs via the `"image"` field:
```json
"image": "https://example.com/images/recipe.jpg"
```

## Troubleshooting

### Issue: PowerShell execution policy error
**Solution**: Run PowerShell as Administrator and execute:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Issue: File encoding problems (special characters)
**Solution**: All files are created with UTF8 encoding. Use `-Encoding UTF8` flag in Out-File commands

### Issue: JSON syntax errors
**Solution**: 
- Use a JSON validator (https://jsonlint.com/)
- Check for unescaped quotes or special characters
- Verify all brackets and braces are matched

### Issue: Agent not following format
**Solution**: Explicitly reference the agent.md file:
```
Please use the schema format defined in agent.md
```

## Updating This Project

### Adding New Recipes
1. Convert to JSON using established format
2. Save in current directory (or specified output directory)
3. Update recipe count in agent.md
4. Regenerate URL list if needed

### Modifying Existing Recipes
1. Ask agent to update specific recipe
2. Provide new/corrected information
3. Agent will use -Force flag to overwrite

### Adding New Fields
1. Update agent.md with new field definition
2. Document when/how to use the field
3. Update existing recipes if the new field is important

### Batch Updates
If you need to update all recipes with a new field:
```
Add [field name] to all JSON recipe files in current directory based on [criteria]
```

## Best Practices Summary

✅ **DO:**
- Reference agent.md at the start of sessions
- Paste recipe text from any source - no special formatting needed
- Include as much information as available (don't worry if incomplete)
- Process recipes in batches of 10 for large sets
- Verify output after each batch
- Use consistent terminology from agent.md
- Keep UTF8 encoding for all files

❌ **DON'T:**
- Worry about text formatting - paste as-is
- Skip sharing recipe if it's not perfectly formatted
- Use non-standard category/cuisine names in final JSON
- Forget to encode spaces in URLs (%20)
- Mix different duration formats (always use ISO 8601 in JSON)
- Overwrite files without verification

## Additional Resources

- **Schema.org Recipe Documentation**: https://schema.org/Recipe
- **ISO 8601 Duration Format**: https://en.wikipedia.org/wiki/ISO_8601#Durations
- **JSON Validator**: https://jsonlint.com/
- **URL Encoder**: https://www.urlencoder.org/

## Support and Feedback

When requesting help from the agent:
1. Be specific about what's not working
2. Provide example input/output
3. Reference the section of agent.md that's relevant
4. Include any error messages

---

**Version**: 1.0  
**Last Updated**: Current session  
**Project**: Recipe Conversion to schema.org/Recipe JSON
