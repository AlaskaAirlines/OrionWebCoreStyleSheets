# WC Style Sheets

[![Build Status](https://travis-ci.org/AlaskaAirlines/OrionWebCoreStyleSheets.svg?branch=master)](https://travis-ci.org/AlaskaAirlines/OrionWebCoreStyleSheets)
![npm (scoped)](https://img.shields.io/npm/v/@alaskaairux/orion-web-core-style-sheets.svg?color=orange)
![NPM](https://img.shields.io/npm/l/@alaskaairux/orion-web-core-style-sheets.svg?color=blue)

**We are in transition between Orion and Auro. With the next MAJOR release of WCSS, the repo and npm will be renamed.**

WC Style Sheets(WCSS) is a responsive, mobile-first collection of styles and tools designed to make it quick and simple for developers to create web experiences using the Auro Design Language.

## What's included

This repository is a library of core level styles, functions, and mixins that can be used for consistent front-end UI development. This will include full descriptions of CSS selectors, mixins and any other supporting functions or tools.

## All styles documented

Please see the [documentation site](https://alaskaairlines.github.io/OrionWebCoreStyleSheets/) for all information related to WC Style Sheets.

## Install

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


### Scoping

Be sure to see the [prefixing and scoping API](http://alaskaairlines.github.io/OrionWebCoreStyleSheets/#scope-prefix) in the documentation site.

When supporting legacy UIs there may be issues with importing a Sass file and its selectors. To enable scoping simply set the `$scope` variable to be `true` before importing any selectors that support this setting.

```scss
$scope: true;
@import "~@alaskaairux/orion-web-core-style-sheets/dist/ ... "
```

This setting will result in the following CSS selectors

```css
html.auro { ... }

.auro body,
.auro .baseType { ... }
```

### Prefixing

To enable prefixing simply set the `$prefix` variable to be `true` before importing any selectors that support this setting.

```scss
$prefix: true;
@import "~@alaskaairux/orion-web-core-style-sheets/dist/ ... "
```

This setting will result in the following CSS selectors

```css
html { ... }

body,
.auro_baseType { ... }
```

### Scoping and prefixing

If needed, both `$scope` and `prefix` can work in tandem. To enable, simply set both the `scope` and `prefix` variables as `true` before importing any selectors that support these settings.

```scss
$scope: true;
$prefix: true;
@import "~@alaskaairux/orion-web-core-style-sheets/dist/ ... "
```

This setting will result in the following CSS selectors

```css
html.auro { ... }

.auro body,
.auro .auro_baseType { ... }
```

### Importing utility classes and using the !important flag

When importing utility selectors developers have the option to invoke the `!important` CSS flag. Within WCSS the global `$important` variable is `null` by default. To change, simply change the value of the variable before importing any utility partials. 

```scss
$important: true; 
```

The output of default selector

```css
.util_is-lgOnly {
  display: none;
}
```

The output with `$important: true`

```css
.util_is-lgOnly {
  display: none !important;
}
```

See !important [spec](http://alaskaairlines.github.io/OrionWebCoreStyleSheets/#utility-variable-important)


### layoutPropertiesGenerator

Importing this file will auto-generates all available utility selectors. Output can be configured by redefining default values before import. See the default value examples below.

```sass
none, xs, md, lg, xl
```

See [API](http://alaskaairlines.github.io/OrionWebCoreStyleSheets/#utility-layout-mixin-auro_layoutPropertiesGenerator)

### insetUtility selector generator

Importing this file will return a series of pre-defined inset (_the padding around an element where all sides are equal_) selectors based on the inset spacing design spec.

```sass
none, xxxs, xxs, xs, sm, md, lg, xl, xxl, xxxl
```

See [API](http://alaskaairlines.github.io/OrionWebCoreStyleSheets/#utility-layout-mixin-auro_inset)

### spacingUtility selector generator

Importing this file will return a series of pre-defined selectors based on the stack or inline spacing design specs

```sass
[inline, stack] inline - L/R, stack - top/bottom

none, xxxs, xxs, xs, sm, md, lg, xl, xxl, xxxl
```

See [API](http://alaskaairlines.github.io/OrionWebCoreStyleSheets/#utility-layout-mixin-auro_spacing)


## †Deprecated

With each release of WC Style Sheets please be sure to pay attention to the †DEPRECATED section of the doc site. All styles that are designated as deprecated will be listed in this section and will be deleted with the next major release. Each deprecated item may list an alternative option. If there is not an alternative option, please consult with your team designer for an alternate solution.

#### Deprecated files

| deprecated file | new file | description |
|---|---|---|
| baselineLTE.scss | core.scss | File deprecation to support new features |
| baseline.scss | essentials.scss | `essentials.scss` does not import headings by default. For new Auro heading sselectors import `headings.scss`. These new selectors support scoping and prefixing.
| inputTypeText.scss | n/a | n/a |
| _layoutProperties.scss | see `_insetUtility.scss` `_layoutPropertiesGenerator.scss` and `_spacingUtility.scss` | The legacy layoutProperties file was broken up into separate concerns |

## Troubleshooting

The following are frequently asked questions.

#### I updated my version and am now getting a missing variable error?

When you update to v2.8, if you get an error that there are missing Sass variables with the Auro namespace, e.g. `$auro- ...` simply import the new Auro Sass variables generated from the tokens.

```scss
@import "~@alaskaairux/orion-design-tokens/dist/tokens/SCSSVariables";
```

#### I updated my version, now some utility selectors are no longer there?

If you have been using selectors from the now deprecated `_layoutProperties.scss` file, you may be missing the following selectors from your CSS output

```css
.util_[margin/padding][Top/Right/Bottom/Left]--[none/xs/md/lg/xl]
```

The easy fix is to import the new layout properties generator file that will fill this gap.

```scss
@import "./node_modules/@alaskaairux/orion-web-core-style-sheets/dist/utilityMixins/layoutPropertiesGenerator";
```

For full details on this generator, please see the [generator documentation](https://alaskaairlines.github.io/OrionWebCoreStyleSheets/#utility-layout-mixin-auro_layoutPropertiesGenerator).


## Support

If at any time there is an issue discovered by either the document site or the core library itself, please submit an [issue](https://github.com/AlaskaAirlines/OrionWebCoreStyleSheets/issues/new/choose) as to alert the core team of the situation. We appreciate all your support!


## CSS writing conventions

The implementation of WCSS uses a naming convention model that will be strictly adhered to throughout this library and compliance is expected for any contributed updates.

### Utility

Universally applicable selectors in cases where applying this style is not an appropriate responsibility of another selector. These selectors are typically considered UI trump cards as they may use the `!important` flag.

To learn more about how the `!important` flag can be used with WCSS, please [see the API spec](https://alaskaairlines.github.io/OrionWebCoreStyleSheets/#variable-important).

(may define shape or layout without direct context to any element, component or object)

```css
.util_hidden {
  display: none;
}

.util_hiddenVisually {
  border: 0;
  clip: rect(1px, 1px, 1px, 1px);
  height: 1px;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
}
```

### Auro supporting styles

Auro web component styles are a special class of utility selectors where common UIs that are mainly addressed in Auro web components are needed in situations where web components cannot be used.

These selectors will be visible by the `.auro_` prefix in the selector name, for example;


```css
.auro_roleButton { ... }

.auro_hyperlink { ... }
```

**NOTE:** The `auro_` prefix will be appended to an Auro supporting selector regardless of the `$prefix` flag setting. Also, the `auro_` prefix will not be duplicated if the `$prefix` flag is set `true`.

### Additional documentation

To learn more about Auro standards in CSS selector conventions, please see [this document](https://github.com/AlaskaAirlines/OrionWebCoreStyleSheets/blob/master/staticDocs/cssConventions.md).


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

[Selectors Level 4 draft: 9.4. The Focus-Indicated Pseudo-class: :focus-visible](https://drafts.csswg.org/selectors-4/#the-focus-visible-pseudo)

## Getting started

All resources within this repository are distributed via npm and used as individual dependencies. Each resource can be called into your Sass pipeline within a `global.scss` file or individually referenced within UI components.

## Linters

Sass-Lint tests to ensure that any new code is compliant with the set-forward standard. Sass-Lint is run as a pre-commit hook in this project. No commits will be allowed unless all linter tests are passed.

If there is an error, this will generate a `.html` file at the root of the project. To view this generated file, run the following command:

```
$ open sass-lint.html
```

This should open the file in your default browser.

This file is ignored and will not be added to version control.

## Tests

Unit testing is done with [Sass True](https://github.com/oddbird/true) and supported by Jest. Unit tests for mixins or functions are required before any pull request will be approved.

Tests are maintained in the `./tests` directory. All test names must follow this convention, `*.spec.scss`.

#### Functions

Functions are to include an `_` in the name. For example, `_myFunction.spec.scss`.

The basic construct of a function unit test is to include the test-module and the test. This is done using the `@include describe()` and the `@include it()` methods.

The assertion has [multiple methods](https://www.oddbird.net/true/docs/api-assert-values.html) to choose from. This example is using the `@include assert-equal()` method.

```scss
@import 'true';
@import '[path to function]';

@include describe('[name of function]') {
  @include it('should return [description of function]') {
    @include assert-equal([function]([argument(s)]), '[expected return]');
  }
}
```

#### Mixins

The basic construct of a mixin unit test is to include the test-module and the test. This is done using the `@include describe()` and the `@include it()` methods.

The [assertion model](https://www.oddbird.net/true/docs/api-assert-output.html) for comparing outputs uses the `@include assert()` method that requires the `@include output` and `@include expect` methods.

```scss
@import 'true';
@import '[path to mixin]';

@include describe('[name of mixin]') {
  @include it('should return [description of mixin]') {
    @include assert {
      @include output {
        @include [mixin]([argument(s)];
      }

      @include expect {
        [expected CSS output];
      }
    }
  }
}
```



## Development

To develop against WCSS run both `npm run watch` and `npm run serve` in separate terminals.

The `watch` command will run a Sass linter, process a test file from Sass to CSS and run a post CSS linter. This will ensure the quality of all new Sass added to the repo.

If additional selectors or scenarios are needed, please update the `./scripts/testBuild.scss` file to test your code.

Running the `serve` command will open the Sassdoc view. Please review all changes as Sassdoc produces all documentation.


##

<footer>
Alaska Airlines Orion Design System<br>
Copyright 2019 Alaska Airlines, Inc. or its affiliates. All Rights Reserved.
</footer>
