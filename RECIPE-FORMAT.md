# Custom Recipe Format

## Overview
You can load custom recipes into the Sourdough Bread Guide app using a JSON file.

## How to Load a Custom Recipe

### Method 1: Using the UI
1. Go to the bread list screen (click "← כל הלחמים")
2. Scroll to the bottom to find "📖 טען מתכון מותאם אישית"
3. Enter the URL of your recipe JSON file
4. Click "טען מתכון"

### Method 2: Using URL Parameter
Add `?recipe=URL` to the page URL:
```
http://localhost:8000?recipe=http://example.com/my-recipe.json
```

### Method 3: Local File
For testing locally, you can use the sample recipe:
```
http://localhost:8000?recipe=http://localhost:8000/sample-recipe.json
```

## Recipe JSON Format

A recipe is a JSON array of step objects. Each step has the following structure:

```json
[
    {
        "title": "Step Title",
        "content": "Detailed instructions for this step",
        "ingredients": ["ingredient 1", "ingredient 2"],  // Optional
        "timer": {                                         // Optional
            "duration": 30,                                // Minutes
            "label": "Timer label"
        },
        "temperature": "Temperature info",                 // Optional
        "tips": "Helpful tips for this step"              // Optional
    }
]
```

### Required Fields
- `title` (string): The name of the step
- `content` (string): Detailed instructions

### Optional Fields
- `ingredients` (array of strings): List of ingredients needed for this step
- `timer` (object): Timer configuration
  - `duration` (number): Timer duration in **minutes**
  - `label` (string): Label shown on the timer
- `temperature` (string): Temperature guidance
- `tips` (string): Additional tips or notes

## Example Recipe

See `sample-recipe.json` for a complete example of a simple bread recipe.

## Validation

The app validates:
- Recipe must be a valid JSON array
- Recipe must have at least one step
- Each step must have `title` and `content` fields

If validation fails, the app will show an error and keep the current recipe.

## Notes

- When you load a new recipe, all existing breads are reset to step 0
- All timers are cleared
- The new recipe applies to all breads
- Recipe is not saved - reload the page to return to the default sourdough recipe

