# R-type - Responsive Type Foundation

R-type exists (it really is a thing).

R-type is a responsive typography foundation that adheres to the following standards:

- Font sizes on the root element are declared in px and converted to % - this adheres to good accessibility practice as it works with native browser zoom
- Otherwise font sizes are declared in px and converted rem's, with px fallback to support older browsers
- Line-heights are declared unitless, e.g. 1.4.



## Installation

R-type lists sass-breakpoint as a requirement. You'll also need a relatively new version of libsass on your project.

Install via `npm install r-type --save`

Include in your scss via `@import "r-type/scss/r-type;`.

## Usage

We start by defining a font map. Take for example the default map:

```
$r-type-font-map: (
  base: (
    null: 16px
  )
);

```

The 'base' key of the map is to be applied to the root level element. In this example we can apply to our root (html) element as such:
```
html {
	@include r-type-font-roots();
}
```

This will result in the following output:
```
html {
    font-size: 100%;
}
```

