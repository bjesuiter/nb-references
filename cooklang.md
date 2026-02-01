---
title: Cooklang - Recipe Markup Language
anchor: Human-readable recipe format for both cooks and programs
tags: [recipes, cooking, markup-language, plain-text, food]
description: Cooklang is a simple text format for recipes readable by humans and machines
source_url: https://cooklang.org/
---

## Summary

**Cooklang** is a simple, human-readable text format for writing recipes that can be understood by both cooks and computers. Write recipes in plain text files using `@ingredient{amount}` and `~{time}` syntax.

## Syntax Example

```
@flour{2%cups}
@sugar{1%cup}
~{25%minutes}

Mix ingredients together.
Bake at 350°F for ~{25%minutes}.
```

## Key Features

- **Human-Readable:** Plain text format that cooks can read easily
- **Machine-Parseable:** Programs can extract ingredients, amounts, times
- **Recipe Scaling:** Auto-scale quantities while keeping fixed amounts (e.g., salt)
- **Shopping Lists:** Generate automatically from recipes
- **Timers:** Extract and track cooking times
- **Git Version Control:** Track changes, fork variations
- **Menu Planning:** Plan weeks, compile shopping lists from menus
- **Import:** Import from hundreds of websites automatically
- **No Account Required:** Works offline, self-hosted
- **Open Source:** Community-driven development

## Ecosystem

### CLI Tools
- Parse recipes, generate shopping lists
- Run local recipe server
- Automate cooking workflow

### Apps
- iOS & Android apps
- macOS (coming soon)
- Web interface (self-hostable)

### Editor Support
- VS Code, Sublime, Vim, Emacs
- Syntax highlighting

### Self-Hosting
- Raspberry Pi hosting
- Local network access
- No cloud dependencies

### AI Integration
- **Cookbot AI Assistant:** Meal plans, unit conversion, recipe discovery

## Use Cases

- Personal recipe management
- Family cookbook creation
- Menu planning & shopping lists
- Batch cooking tracking
- Recipe versioning with Git
- Publishing recipes

## Related

- Git-based recipe workflows
- Meal planning systems
- Raspberry Pi self-hosting

## Links

- Docs: https://cooklang.org/docs/
- GitHub: https://github.com/cooklang
- Apps: https://cooklang.org/app/
