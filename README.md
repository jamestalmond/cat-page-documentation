# Documentation - Cat pages

## Contents

1. [Setup](#setup)
2. [Initial options](#initial-options)
3. [Layout](#layout)
	1. [Keys](#keys)
	1. [Modules](#modules)
		1. [`flex-container`](#-flex-container-)
		1. [`flex-item`](#-flex-item-)
		1. [`cat-page-hero`](#-cat-page-hero-)
		1. [`signpost`](#-signpost-)
		1. [`card`](#-card-)
		1. [`card-hero`](#-card-hero-)
		1. [`pods`](#-pods-)
		1. [`pod-item`](#-pod-item-)

# Dependences

- [node.js](https://nodejs.org/en/) v6.10.3 or greater
- [NPM](https://www.npmjs.com/) v5.3.0 or greater

# Setup

1. Navigate to directory with `package.json`
2. Run `npm i`
3. Navigate to `src/configs` and duplicate and rename `template.json`; this will be the config for the page you're creating, you can create multiple configs for multiple pages

These cat pages are built using config driven nunjucks templates, utilising modules to build your page to keep consistant layouts and styles across all future cat pages.

After you've run through the setup, you'll be presented with this:

```json
{
    "config": {
        "lang": "en-GB",
        "title": "Title",
        "metaDescription": "Description",
        "pageUrl": "http://ao.com/",
        "stylesheets": [
            "css/pages/page-specific-styles.css"
        ]
    },
    "layout": []
}
```

## Initial options

`lang` HTML lang attribute

`title` Page title

`metaDescription` Meta description

`pageUrl` URL of the page when on site

`stylesheets` An array of stylesheets specific to this page

# Layout

## Keys

A list of keys used to build the page.

`templateId` References the ID of a template within your nunjucks templates

`data` Outputs data within the parent template

`children` Defines the children of the parent template, always output within the parent template

`modifier` Adds a modifier to the parent template, modifiers are CSS classes

## Modules

_Array of objects_

A list of modules used to create cat pages.

### `flex-container`

Outputs a flexbox container, this is the main container for your flexbox items.

```json
{
    "templateId": "modules/flex-container",
    "data": {
        "modifier": "col-2 col-2-hero row",
        "children": [{}]
    }
}
```

### Modifiers

`row` Adds margin-top to the row

`col-2` Defines a 2 column row

![Col 2](https://raw.github.com/jamestalmond/cat-page-documentation/master/readme-assets/col-2.JPG)

`col-2-hero` Defines a 2 column row with the second flexbox item being a hero image that spans the height of 2 stacked cards

![Col 2 hero](https://raw.github.com/jamestalmond/cat-page-documentation/master/readme-assets/col-2-hero.JPG)

`col-3` Defines a 3 column row

![Col 3](https://raw.github.com/jamestalmond/cat-page-documentation/master/readme-assets/col-3.JPG)

`stacked` Stacks the child flexbox items on top of each other at tablet and above

![Stacked](https://raw.github.com/jamestalmond/cat-page-documentation/master/readme-assets/stacked.JPG)

### `flex-item`

Outputs a flexbox item module, you should only output the amount of flexbox items you've specified on the parent flexbox container. For example, if you've added a modifier of `col-2` to your parent flexbox container, only have 2 flexbox items as children.

```json
{
    "templateId": "flex-item",
    "data": {
        "children": [{}]
    }
}
```

### `cat-page-hero`

Outputs a cat page hero container, apply background-image via page specific stylesheets.

```json
{
    "templateId": "cat-page-hero",
    "data": {
        "children": [{}]
    }
}
```

### `signpost`

Outputs a signpost block, this is used to contain the category page signpost cards.

```json
{
    "templateId": "signpost",
    "data": {
        "children": [{}]
    }
}
```

### `card`

![Card](https://raw.github.com/jamestalmond/cat-page-documentation/master/readme-assets/card.JPG)

Outputs a card block, cards are the main focus point of the cat page hero

```json
{
    "templateId": "card",
    "data": {
        "modifier": "side-by-side",
        "srcSrcSet": "img/laptops.JPG 1x, img/laptops_2x.JPG 2x",
        "srcMediaQuery": "min-width: 768px",
        "imgSrcSet": "img/laptops.JPG 1x, img/accessories_2x.JPG 2x",
        "imgAltText": "Buy laptops now",
        "title": "Laptops",
        "text": "Complete your kit with our gaming laptops",
        "ctaHref": "/laptops/",
        "ctaModifier": "link-dark",
        "ctaText": "Buy now"
    }
}
```

### Modifiers

`side-by-side` Sets the card content to be image left, text content right on all devices from mobile to landscape, and tablet onwards

`img-pl` Allows the card's image to sit on the left hand side of the card when the image and content are side by side. Please note you do not need the `side-by-side` modifier to use this

### Data to output

All data is output per instance.

`srcSrcSet` Picture element `<source>` element `srcset` attribute

`srcMediaQuery` Picture element `<source>` element `srcMediaQuery` attribute. For example: `min-width: 768px`

`imgSrcSet` Picture element `<img>` element `srcset` attribute

`imgAltText` Picture element `<img>` element `alt` attribute

`title` Card title

`text` Card text

`ctaHref` CTA button URL

`ctaModifier` CTA button modifiers, refer to global styles for more information

`ctaText` CTA button inner text

### `card-hero`

![Card hero](https://raw.github.com/jamestalmond/cat-page-documentation/master/readme-assets/card--hero.JPG)

Outputs a card hero block, this is a card with a background image, behaves differently than a normal card. Only use in conjuction with a parent flexbox container with a `col-2-hero` modifier

```json
{
    "templateId": "card-hero",
    "data": {
        "modifier": "hero-bg",
        "title": "Become a gaming expert",
        "text": "Discover everything you need to know about the world of PC gaming",
        "ctaHref": "/help-and-advice/help-me-choose/pc-gaming-tech-explained/",
        "ctaModifier": "link-light",
        "ctaText": "Find out more",
        "ampHeroCardImg": "img/amp-background.JPG 1x"
    }
}
```

### Data to output

All data is output per instance.

`modifier` This module requires a modifier to be defined which can then be targetted with CSS to provide a background image

`title` Card title

`text` Card text

`ctaHref` CTA button URL

`ctaModifier` CTA button modifiers, refer to global styles for more information

`ctaText` CTA button inner text

`ampHeroCardImg` Outputs the specified image on the AMP version of this cat page

### `pods`

![Pods](https://raw.github.com/jamestalmond/cat-page-documentation/master/readme-assets/pods.JPG)

Outputs a merch pods block, includes a title

```json
{
    "templateId": "pods",
    "data": {
        "inner": true,
        "children": [{}]
    }
}
```

### Modifiers

`inner` Boolean that adds in an inner element as a child

### `pod-item`

![Pod item](https://raw.github.com/jamestalmond/cat-page-documentation/master/readme-assets/pod-item.JPG)

Outputs a merch pod item

```json
{
    "templateId": "pod-item",
    "data": {
        "podHref": "//google.co.uk/",
        "srcSrcSet": "/media.ao.com/uk/promotions/merch/backToSchool-100817_LP.JPG",
        "srcMediaQuery": "min-width: 544px",
        "imgSrcSet": "/media.ao.com/uk/promotions/merch/backToSchool-100817_LP.JPG",
        "imgAltText": "Test"
    }
}
```

### Data to output

All data is output per instance.

`podHref` Pod URL

`srcSrcSet` Picture element `<source>` element srcset attribute

`srcMediaQuery` Picture element `<source>` element srcMediaQuery attribute. For example: `min-width: 768px`

`imgSrcSet` Picture element `<img>` element srcset attribute

`imgAltText` Picture element `<img>` element alt attribute
