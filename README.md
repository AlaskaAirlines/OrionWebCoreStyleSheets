# WC Style Sheets

WC Style Sheets(WCSS) is a responsive, mobile-first collection of styles and tools designed to make it quick and simple for developers to create web experiences using the Auro Design Language.

## What's included

This repository is a library of core level styles, functions, and mixins that can be used for consistent front-end UI development. This will include full descriptions of CSS selectors, mixins and any other supporting functions or tools.

## Documentation

Please see the [documentation site](https://alaskaairlines.github.io/WebCoreStyleSheets/) for all information related to WC Style Sheets.

## Install

[![Build Status](https://img.shields.io/travis/AlaskaAirlines/WebCoreStyleSheets?branch=master&style=for-the-badge)](https://travis-ci.org/github/AlaskaAirlines/WebCoreStyleSheets)
[![See it on NPM!](https://img.shields.io/npm/v/@alaskaairux/orion-web-core-style-sheets.svg?style=for-the-badge&color=orange)](https://www.npmjs.com/package/@alaskaairux/WebCoreStyleSheets)
[![License](https://img.shields.io/npm/l/@alaskaairux/orion-web-core-style-sheets.svg?color=blue&style=for-the-badge)](https://www.apache.org/licenses/LICENSE-2.0)
[![issues](https://img.shields.io/github/issues-raw/AlaskaAirlines/WebCoreStyleSheets?style=for-the-badge)](https://github.com/AlaskaAirlines/WebCoreStyleSheets/issues)

There are no core files to import, rather WCSS is an à la carte solution allowing for users to import what they want and when they want it. In most cases you can simply import the Sass file as illustrated below:

```scss
@import "~@alaskaairux/orion-web-core-style-sheets/dist/ ... "
```

### Tokens Dependency

WCSS uses Sass and has a dependency on the `SCSSVariables.scss` file from [Design Tokens](https://github.com/AlaskaAirlines/OrionDesignTokens) package. This reference needs to be imported before any reference of a WCSS partial. 

```scss
@import "~@alaskaairux/orion-design-tokens/dist/tokens/SCSSVariables";
@import "~@alaskaairux/orion-web-core-style-sheets/dist/ ... ";
```

### Install the essentials 

While WCSS is an à la carte solution, there are things that should be considered when adding WCSS to your project. For example, if the project has little or no legacy CSS, it is suggested to set the following foundation:

```scss
// baseline design tokens as Sass variables
@import "~@alaskaairux/orion-design-tokens/dist/tokens/SCSSVariables";

// globally add the mixins so that any future reference will be addressed 
@import '~@alaskaairux/orion-design-tokens/dist/tokens/breakpoints';

// it's typically best practice to load the @font-face rules prior to any reference of the custom web fonts
@import '~@alaskaairux/orion-design-tokens/dist/tokens/fonts';

// set a baseline browser normalize
@import '~@alaskaairux/orion-design-tokens/dist/tokens/normalize';

// essentials setup baseline primitive selectors for any UI development 
@import '~@alaskaairux/orion-design-tokens/dist/tokens/essentials';
```

For an example of setting up a master file that imports all of WCSS's resources, see the [styleTest.scss](https://github.com/AlaskaAirlines/OrionWebCoreStyleSheets/blob/master/tests/styleTest.scss) in the project.


## Pre-processed bundled resources

At a limited scale, some files have been pre-processed to CSS so that it can be delivered via CDN and used in environments where this rendered resource is required. 

**API Note**: First supporting version `v2.9.0`

```
unpkg.com/:package@:version/:file
```

| resource | supports | CDN URL |
|---|---|---|
| essentials.scss<br>fonts.scss|Auro WCs|https://unpkg.com/@alaskaairux/orion-web-core-style-sheets@:version/dist/bundled/essentials.css|
| baseline.scss<br>fonts.scss|ODS WCs|https://unpkg.com/@alaskaairux/orion-web-core-style-sheets@:version/dist/bundled/baseline.css|

## †Deprecated

With each release of WC Style Sheets please be sure to pay attention to the †DEPRECATED section of the doc site. All styles that are designated as deprecated will be listed in this section and will be deleted with the next major release. Each deprecated item may list an alternative option. If there is not an alternative option, please consult with your team designer for an alternate solution.

#### Deprecated files

| deprecated file | new file | description |
|---|---|---|
| baselineLTE.scss | core.scss | File deprecation to support new features |
| baseline.scss | essentials.scss | `essentials.scss` does not import headings by default. For new Auro heading sselectors import `headings.scss`. These new selectors support scoping and prefixing.
| inputTypeText.scss | n/a | n/a |
| _layoutProperties.scss | see `_insetUtility.scss` `_layoutPropertiesGenerator.scss` and `_spacingUtility.scss` | The legacy layoutProperties file was broken up into separate concerns |

## Dependencies

When using WCSS, there is a direct dependency on the `focus-visible` library. When using Web Components, the inclusion of the `focus-visible` library is accounted for within the scope fo the component(s). With components, `focus-visible` is defined as a peer dependency.

If the use of WCSS is not specifically with a component, including the `focus-visible.min.js` file will be required within the scope of the project. For example, the JS may be added to the head of a project:

```html
<script src="/node_modules/focus-visible/dist/focus-visible.min.js"></script>
```

or to the scope of any Node.js component architecture:

```javascript
import 'focus-visible/dist/focus-visible.min.js';
```

The `focus-visible` library is required for use with experimental a11y UI features

## Accessibility

The use of the `focus-visible` library brings in the capability to be selective with the UI between clicking/tapping into a control versus tabbing to a control. In most cases, the a11y halo will only appear when a control is tabbed to. But in cases where there is a `<input />` element that supports text and/or triggers a virtual keyboard if a physical keyboard is not present, the `focus-visible` state will be triggered.

For more information, please be sure to review the Selectors Level 4 draft 9.4, the Focus-Indicated Pseudo-class: [:focus-visible](https://drafts.csswg.org/selectors-4/#the-focus-visible-pseudo)

## Development

To develop against WCSS run both `npm run watch` and `npm run serve` in separate terminals.

The `watch` command will run a Sass linter, process a test file from Sass to CSS and run a post CSS linter. This will ensure the quality of all new Sass added to the repo.

If additional selectors or scenarios are needed, please update the `./scripts/testBuild.scss` file to test your code.

Running the `serve` command will open the Sassdoc view. Please review all changes as Sassdoc produces all documentation.

### Linters

Sass-Lint tests to ensure that any new code is compliant with the set-forward standard. Sass-Lint is run as a pre-commit hook in this project. No commits will be allowed unless all linter tests are passed.

If there is an error, this will generate a `.html` file at the root of the project. To view this generated file, run the following command:

```
$ open sass-lint.html
```

This should open the file in your default browser.

This file is ignored and will not be added to version control.
