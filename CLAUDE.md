# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a personal meal planning system organized around **weekly meal plans**. The repository contains:

- **Master recipes** with flexible ingredient variations and cooking methods
- **Weekly meal plans** (specific adaptations of master recipes for each week)
- **Shopping lists** (aggregated ingredient lists for all meals in a given week)

## Directory Structure

```
meal-planning/
├── recipes/             # Master recipe library
│   ├── mains/           # Main course recipes (primarily dinners)
│   ├── sides/           # Side dish recipes
│   ├── snacks/          # Snack recipes
│   └── treats/          # Dessert recipes
├── meal-plans/          # Weekly meal plans organized by year
│   └── YYYY/
│       └── week-XX/     # Individual weeks (typically 6-7 dinners per week)
├── shopping-lists/      # Weekly shopping lists
├── prompts/             # AI prompts for meal plan generation
└── scripts/             # Automation scripts
```

## Cooking Philosophy & Preferences

**Nutritional Priorities:**

- Nutritious, lower calorie, whole food meals with minimal ultra-processed ingredients
- Lower calories but higher volume/bulk to feel full (emphasize vegetables, broths, healthy proteins)
- Minimize large servings of pasta, rice, starch, simple carbs, and simple sugars
- Lower salt and lower saturated fats preferred
- Higher vitamins, phytonutrients, antioxidants, and omega-3
- Vegetarian meals a few days per week; fish once per week
- **Important:** Practice moderation over the week - not every meal needs to hit all guidelines. Some days allow for pasta, more sodium, or saturated fats. No foods are off limits.

**Cooking Style:**

- Located in Minnesota (consider ingredient availability)
- Lower interoception means preference for more seasoning and varied spice combinations
- Wide variety of spices on hand; not afraid to buy more
- Mix of effort levels: some complex, detailed meals and some quick-prep meals throughout the week
- Detail-oriented approach; cooking is a hobby
- Enjoys trying new things and experimenting with recipes

**Formatting Preferences:**

- Use decimal notation for measurements: `0.5 tbsp` not `1/2 tbsp`, `0.75 cup` not `3/4 cup`
- In meal plans, include prep notes inline with ingredients: `1 chicken breast, cooked and cubed`, `2 carrots, sliced into rounds`

## Core Workflow

The meal planning workflow follows this pattern:

1. **Master Recipes** (`recipes/mains/`) contain flexible base recipes with:
   - Multiple ingredient variations and substitutions
   - Different seasoning profiles (Traditional, Asian, Mediterranean, etc.)
   - Multiple cooking method variations (slow cooker, oven, air fryer, stovetop, etc.)
   - Detailed cooking instructions and prep notes
   - Effort estimates

2. **Meal Plans** (`meal-plans/YYYY/week-XX/`) are specific meal instances:
   - Usually adapted from master recipes with pre-selected ingredients and methods
   - Sometimes standalone recipes with no master recipe equivalent
   - May contain variations not present in the master recipe
   - Use specific ingredients (e.g., "2 boneless chicken breasts, cooked and cubed" instead of "1 lb protein")
   - Include inline prep notes with ingredients

3. **Shopping Lists** (`shopping-lists/YYYY-MM-DD.md`) aggregate ingredients for the week:
   - Dated for the shopping day (typically Friday or Saturday, but varies)
   - Organized by grocery store department/aisle for efficient shopping
   - Each recipe ingredient references which meal(s) use it
   - May include staples and breakfast/lunch items not tied to specific dinner recipes
   - Cross-ingredient tracking (e.g., "1 head garlic - Pork Chops (2), Stew (4), Curry (3)")

## File Naming Conventions

**Recipes and Meal Plans:**

- Format: `lowercase-hyphenated-name.md`
- Examples: `shepherds-pie.md`, `black-bean-sweet-potato-tacos.md`
- Keep names descriptive but concise

**Shopping Lists:**

- Format: `YYYY-MM-DD.md` (ISO date format)
- Date represents the actual shopping day (typically Friday or Saturday, but varies by week)

## Recipe File Format

Master recipes use YAML frontmatter followed by structured markdown sections:

```markdown
---
title: Recipe Name
tags:
  - category tags
  - preparation type
  - meal characteristics
effort: XX minutes
---

# Recipe Title

Brief description of the dish

## Ingredients

### Section Name (e.g., Mashed Topping, Filling, Sauce)

- Ingredient lists with measurements
- [Optional] markers for optional ingredients

**Prep Notes:**
Preparation tips and techniques

**Variations:**
Alternative ingredients and substitutions

## Seasoning Variations

Different flavor profiles (Traditional Herb, Asian, Mediterranean, etc.)

## Cooking Method Variations

Alternative cooking methods (slow cooker, oven, air fryer, stovetop, etc.)

## Cooking Instructions

Numbered steps with timing and temperature details

## Notes

Nutritional info, serving suggestions, tips, etc.
```

**Key Recipe Patterns:**

- Use `[Optional]` prefix for optional ingredients
- Use decimal notation for measurements: `0.5 tbsp`, `0.75 cup`, etc.
- Include specific measurement ranges (e.g., "1-3 tbsp butter")
- Provide multiple seasoning variations for diversity
- Include cooking method variations (slow cooker, oven, air fryer, etc.)
- Include prep notes for technique guidance
- List substitutions and variations for flexibility

## Shopping List Format

Shopping lists are organized by grocery store department/aisle for efficient shopping:

1. **Proteins**
2. **Canned & Dry Goods**
3. **Produce - Fresh Vegetables**
4. **Produce - Fresh Fruit**
5. **Frozen**
6. **Dairy & Refrigerated**
7. **Oils, Vinegars & Condiments**
8. **Spices & Seasonings**
9. **Beverages**

**Item Format:**

```markdown
- **Quantity + Item** - _Recipe Name(s) with optional (count)_
```

Example:

```markdown
- **4 medium sweet potatoes** - _Baked Breaded Salmon (2), Black Bean Tacos (2)_
```

**Notes:**

- Shopping lists may include staples and breakfast/lunch items not linked to specific dinner recipes
- Items show which recipes use them for context when making shopping decisions

## Meal Plan File Format

Meal plan files are specific meal instances:

- Include specific ingredients with inline prep notes (e.g., "2 boneless chicken breasts, cooked and cubed" not "1 lb protein")
- Use decimal notation for measurements (0.5 tbsp, 0.75 cup)
- Omit the YAML frontmatter
- Omit variation sections
- Keep only the chosen seasoning profile and cooking method
- Streamline instructions for the specific week's preparation
- May be adaptations of master recipes or standalone recipes

## Working with This Repository

**When creating new recipes:**

- Start with the master recipe in `recipes/mains/`
- Follow the established format with all sections
- Include multiple variations (seasoning and cooking method)
- Provide detailed prep notes for complex techniques
- Use decimal notation for measurements

**When planning a new week (COLLABORATIVE PROCESS):**

- The user will specify how many meals to plan (typically 6-7 dinners, but varies)
- The user may select specific recipes they want to cook
- The user may ask for suggestions from master recipes or new recipe ideas
- Work iteratively - the user may request changes after initial meal plans are created
- Create a new `week-XX/` directory under the current year
- Each meal plan should specify ingredients with inline prep notes
- Consider nutritional balance: include vegetarian meals, fish once/week, variety in proteins and cuisines
- Mix effort levels: some complex meals, some quick-prep meals

**When generating shopping lists:**

- Aggregate all ingredients from the week's meal plans
- Include staples and breakfast/lunch items as needed (not tied to dinner recipes)
- Organize by grocery store department (see Shopping List Format above)
- Cross-reference ingredients used in multiple recipes
- Include quantities that account for all meals using that ingredient
- Format: **Quantity + Item** - _Recipe Names with (count per recipe)_

**Common cross-references:**

- Garlic, onions, and common vegetables often appear in multiple meals
- Track spice usage to avoid duplicate purchases

## Repository Context

This is a personal meal planning system for weekly meal preparation. All markdown files are created collaboratively through Claude prompts and manual editing. There are no build tools, tests, or deployment processes. The repository uses version control to track meal planning history and recipe evolution over time.
