# Orion Web Core Style Sheets

The core front-end framework for building experiences with the Orion Design System.

Orion Web Core Style sheets is a responsive, mobile-first collection of styles and tools designed to make it quick and simple for developers to create web experiences using the Orion Design Language.

## What's included

This repository is a library of core level styles, functions, and mixins that can be used for consistent front-end UI development.

## Current support

The current version of Orion Web Core Style Sheets supports:

1. `AS Circular` web font, font file resources and `@font-face` Sass -- [Install Instructions](https://itsals.visualstudio.com/DefaultCollection/Orion%20Design%20System/_git/OWCSS?path=%2Fdocs%howToUseFonts.md&version=GBmaster)
1. Orion defined breakpoint mixins
1. CSS Normalize
1. Orion baseline styles

## Dependencies

Orion Web Core Style Sheets has a direct project dependency on [Orion Design Tokens](https://itsals.visualstudio.com/DefaultCollection/Orion%20Design%20System/_git/designTokens). Orion Web Core Style Sheets is not a stand alone project, but is part of a specific dependency chain when building Orion based applications.

## Getting started

All resources within this repository are to be distributed via npm and used as individual dependencies. Each resource can be called into your Sass pipeline within a `global.scss` file or individually referenced within UI components.

## Sass support

The Orion Web Core Style Sheets consists of resources to be ingested a la carte. For example, you wish to use `breakpoints.scss` on an individual component or bring into a global Sass catch-all file, you would use the following example.

```
@import "@alaskaair/orion-web-core-style-sheets/breakpoints";
```

## CSS writing conventions

The implementation of Orion Web Code Style Sheets uses a naming convention model that will be strictly adhered to throughout this library and compliance is expected for any contributed updates.

To learn more, please reference [this document](https://itsals.visualstudio.com/DefaultCollection/Orion%20Design%20System/_git/OWCSS?path=%2Fdocs%2FcssConventions.md&version=GBmaster).
