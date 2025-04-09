# SnipBit-Token-Extension

Design Token System

Folder Structure

├── tokens/ │ ├── colors.json │ ├── typography.json │ ├── spacing.json │ └── effects.json ├── config.json └── build/ ├── web/ ├── ios/ ├── android/ └── docs/


---

Token Categories

### 1. Typography (`tokens/typography.json`)
```json
{
  "font": {
    "family": {
      "primary": { "value": "Inter, sans-serif" },
      "secondary": { "value": "Merriweather, serif" }
    },
    "size": {
      "small": { "value": "12px" },
      "body": { "value": "16px" },
      "large": { "value": "24px" },
      "title": { "value": "32px" }
    },
    "weight": {
      "regular": { "value": "400" },
      "bold": { "value": "700" }
    },
    "lineHeight": {
      "small": { "value": "16px" },
      "body": { "value": "24px" },
      "large": { "value": "32px" }
    }
  }
}
2. Spacing (tokens/spacing.json)
{
  "spacing": {
    "xs": { "value": "4px" },
    "sm": { "value": "8px" },
    "md": { "value": "16px" },
    "lg": { "value": "24px" },
    "xl": { "value": "32px" }
  }
}
3. Effects – Border Radius & Shadows (tokens/effects.json)
{
  "borderRadius": {
    "small": { "value": "4px" },
    "medium": { "value": "8px" },
    "large": { "value": "16px" }
  },
  "shadow": {
    "small": { "value": "0px 2px 4px rgba(0,0,0,0.1)" },
    "medium": { "value": "0px 4px 8px rgba(0,0,0,0.15)" },
    "large": { "value": "0px 8px 16px rgba(0,0,0,0.2)" }
  }
}
Style Dictionary Config (config.json)

{
  "source": ["tokens/**/*.json"],
  "platforms": {
    "web": {
      "transformGroup": "css",
      "buildPath": "build/web/",
      "files": [
        {
          "destination": "variables.css",
          "format": "css/variables"
        }
      ]
    },
    "ios": {
      "transformGroup": "ios",
      "buildPath": "build/ios/",
      "files": [
        {
          "destination": "StyleDictionaryFont.swift",
          "format": "ios/font-swift"
        }
      ]
    },
    "android": {
      "transformGroup": "android",
      "buildPath": "build/android/",
      "files": [
        {
          "destination": "dimens.xml",
          "format": "android/dimens"
        }
      ]
    },
    "html": {
      "transformGroup": "web",
      "buildPath": "build/docs/",
      "files": [
        {
          "destination": "styleguide.html",
          "format": "html"
        }
      ]
    }
  }
}
How to Build

Install and build the tokens with:

npm install --save-dev style-dictionary
npx style-dictionary build

Output Samples

Web – build/web/variables.css
:root {
  --font-size-body: 16px;
  --spacing-md: 16px;
  --border-radius-medium: 8px;
}
iOS – build/ios/StyleDictionaryFont.swift
struct StyleDictionaryFont {
    static let fontSizeBody = 16
    static let fontFamilyPrimary = "Inter, sans-serif"
}
Android – build/android/dimens.xml
<resources>
  <dimen name="font_size_body">16sp</dimen>
  <dimen name="spacing_md">16dp</dimen>
</resources>
Docs – build/docs/styleguide.html
A web-friendly style guide page is generated using the HTML format (optional).
