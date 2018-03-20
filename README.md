# Type Harmony - Responsive Type Foundation

Type harmony exists (it really is a thing).

Type harmony is a responsive typography foundation that adheres to the following standards:

- Font sizes on the root element are declared in px and converted to %. This is good accessibility practice, it works with native browser zoom.
- Otherwise font sizes are declared in px and converted to rems, with px fallback to support older browsers.
- Line-heights are declared unitless, e.g. 1.4.
- Vertical spacing may be added using the 'spacing' key.



## Installation

This lib may well be subject to change, use at your own risk.

Type harmony lists sass-breakpoint as a requirement (it's worth it). You'll also need a relatively new version of libsass on your project. *Recommended* is to install a media query packer (e.g. css-mqpacker) into your process chain - in the wrong hands this lib can potentially produce some bloat that's ripe for packing.

Install via `npm install type-harmony --save`

Include in your scss via `@import "~type-harmony/scss/type-harmony";`.


## Usage

We start by defining a font map. Take for example the default map:

```
$harmonise-font-map: (
  base: (
    null: 16px
  )
);

```

The 'base' key of the map is to be applied to the root level element. In this example we can apply to our root (html) element as such:
```
html {
	@include $harmonise-roots();
}
```

This will result in the following output:
```
html {
    font-size: 100%;
}
```

More TBC.


Mention...
- Base breakpoints defining the breakpoints which will be used throughout.
- Missing a breakpoint will result in inaccurate scaling at that breakpoint (no recalculation at new base font size)
- Spacing as a multiple of font-size and line height


TODO
- Check this element's line-height before using the root line-height for vertical spacing.
