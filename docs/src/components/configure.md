---
title: Configure
mainTitle: Components
layout: main.pug
category: Components
withHeadings: true
navWeight: 10
editable: true
githubSource: docs/src/components/configure.md
---

A component which renders nothing, but allows you to pass extra search parameters that will apply to this search.

Note that other widgets may override certain parameters. For example, using `facetFilters` will be overriden, but `filters` won't be.

<a class="btn btn-static-theme" href="stories/?selectedKind=ais-configure">🕹 try out live</a>

## Usage

Basic usage:

```html
<ais-configure></ais-configure>
```

Setting 5 hits per page:

```html
<ais-configure :hitsPerPage="5"></ais-configure>
```

Disable query rules:

```html
<ais-configure :enableRules="false"></ais-configure>
```

## Props

Any prop given to this widget will be applied as a [search parameter](https://www.algolia.com/doc/api-reference/search-api-parameters/).

## Slots

Name | Scope | Description
---|---|---
default | `{ searchParameters: SearchParameters, refine: (searchParameters: SearchParameters) => void }` | Slot to override the DOM output

Note: The `refine` function will fully override the data given via props. If you want to shallowly merge it, use something like:

```html
<ais-configure :enableRules="false" :hitsPerPage="5">
  <template slot-scope="{ searchParameters, refine }">
    <button
      @click="refine(
        Object.assign(
          {},
          searchParameters,
          { enableRules: !searchParameters.enableRules }
        )
      )"
    >
      toggle only query rules
    </button>
    currently applied filters: <pre>{{searchParameters}}</pre>
  </template>
</ais-configure>
```

It's also possible to use multiple Configures for this use case.

## CSS Classes

Here's a list of CSS classes exposed by this widget. To better understand the underlying
DOM structure, have a look at the generated DOM in your browser.

Note that you can pass the prop `class-names`, with an object of class names and their replacement to override this.

Class name | Description
---|---
`ais-Configure` | The container of the Configure widget
