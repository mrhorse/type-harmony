# Type Harmony - Responsive Type Foundation

Type harmony exists (it really is a thing).

Type harmony is a responsive typography foundation that adheres to the following standards:

- Mobile first
- Font sizes on the root element are declared in px and then converted to %. This follows good accessibility practice as it allows users to apply their own text size in browser settings. Working in absolute values fixes the user default values and is not accessible.
- Similarly font sizes are declared in px and converted to rems, with optional px fallback to support older browsers.
- Line-heights are declared unitless, e.g. 1.4.




## Installation

This lib may well be subject to change, use at your own risk.

Type harmony lists sass-breakpoint as a requirement (it's worth it). You'll also need a relatively new version of libsass on your project. *Recommended* is to install a media query packer (e.g. css-mqpacker) into your process chain - in the wrong hands this lib can potentially produce some bloat that's ripe for packing.

Install via `npm install type-harmony --save`

Include in your scss via `@import "~type-harmony/scss/type-harmony";` Replace ~ with path to node_modules if not using webpack.


## Usage

We start by defining a font map. Take for example the default map:

```
$harmonise-font-map: (
  base: (
    null: 16px
  ),
  h1: (
    null: (
      size: 40px,
      leading: 1.4
    ),
    768px: (
      size: 46px,
    ),
  ),
);

```

The 'base' key of the map is to be applied to the root level element. In this example we can apply to our root (html) element as such, along with an example h1:
```
html {
	@include harmonise-roots();
}
h1 {
	@include harmonise-type(h1);
}
```

This will result in the following output:
```
html {
    font-size: 100%;
}
h1 {
  font-size: 40px;
  font-size: 2.5rem;
  line-height: 1.4; 
}
@media (min-width: 768px) {
  h1 {
    font-size: 46px;
    font-size: 2.70588rem;
  } 
}
```

Also available is a mixin: `@include harmonise-fixed(size)` - again size is declared in px. It is for one-off declarations that will output for each available breakpoint at a fixed px size in REM.



Points to note:
- Remove PX fallback from output by setting var `$harmonise-use-px-fallback` to false.
- Please use a MQ packer plugin in your scss pipeline to reduce superfluous css output.
- Missing a breakpoint for a key will result in inaccurate scaling at that breakpoint (this is because there's would be no REM base recalculation at new base font size for that item)
- Defining breakpoints in the base key will define the breakpoints which will be used throughout.


TODO
- Check this element's line-height before using the root line-height for vertical spacing.
- Spacing (margin-bottom) as a multiple of font-size and line height [may not implement in an effort to not overcomplicate this library.]
