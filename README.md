## Table of contents

*   [Foxgrid](#foxgrid)
    *   [Columns](#columns)
    *   [Breakpoints](#breakpoints)
    *   [Gutter per breakpoint](#gutter-per-breakpoint)
*   [Grid system](#grid-system)
    *   [Fluid](#fluid)
    *   [Nesting columns](#nesting-columns)
    *   [Offseting column](#offseting-columns)
*   [Columns direction](#columns-direction)
    *   [Reverse](#reverse)
    *   [Vertical](#vertical)
    *   [Vertical reverse](#vertical-reverse)
*   [Reorder columns](#reorder-columns)
    *   [First](#first)
    *   [Last](#last)
*   [Items alignment](#items-alignment)
    *   [Start](#start)
    *   [Center](#center)
    *   [End](#end)
    *   [Top](#top)
    *   [Middle](#middle)
    *   [Bottom](#bottom)
*   [Self alignment and stretch](#self-alignment-and-stretch)
*   [Distribution](#distribution)
    *   [Space around](#space-around)
    *   [Space between](#space-between)

# Foxgrid

Grids are used for creating page layouts, and Foxgrid works very similarly to the standard float grid, but takes advantage of some feature only possible with flexbox ([Flexbox support](http://caniuse.com/#feat=flexbox)).
Foxgrid was built in SCSS and the grid follows some rules to work properly:

*   Rows must be placed within a `.container` for proper alignment, or just add the class `.no-gutter-row` to remove the negative margin
*   Use rows to wrap columns (they're the ones with `display: flex`)

And has the following options fully customizable:

## Columns

12 columns by default

```scss
$grid-columns: 12 !default;
```

## Breakpoints

6 mobile first breakpoints

```scss
$breakpoints: (
    xxs: '', // default
    xs: '640px',
    sm: '768px',
    md: '992px',
    lg: '1200px',
    xl: '1600px'
);
```

Which can be used with the following media queries:

```scss
// Extra extra small devices (less than 640px)
// No media query since this is the default

// extra small devices (640+ px)
@media (min-width: map-get($breakpoints, xs) { ... }

// small devices (tablet in portrait, 768+ px)
@media (min-width: map-get($breakpoints, sm) { ... }

// medium devices (small desktops, tablet in landscape, 992+ px)
@media (min-width: map-get($breakpoints, md) { ... }

// large devices (desktops, laptops, 1200+ px)
@media (min-width: map-get($breakpoints, lg) { ... }

// extra large devices (large desktops, 1600+ px)
@media (min-width: map-get($breakpoints, xl) { ... }
```

## Gutter per breakpoint

Custom gutter for each breakpoint

```scss
$gutter-map: (
    xxs: 10,
    xs:  10,
    sm:  30,
    md:  30,
    lg:  30,
    xl:  30
);
```

and a set of helper variables for standalone usage

```scss
$gutter-xxs: map-get($gutter-map, xxs);
$gutter-xs:  map-get($gutter-map, xs);
$gutter-sm:  map-get($gutter-map, sm);
$gutter-md:  map-get($gutter-map, md);
$gutter-lg:  map-get($gutter-map, lg);
$gutter-xl:  map-get($gutter-map, xl);
```

# Grid system

**Columns wrapping**  
If more than `$grid-columns` columns are placed within a single row, they'll wrap onto a new line, as long as they have defined widths.

**No gutter**  
Add `.no-gutter` to the `.row` to remove the gutter between columns.

## Fluid

**Percent based widths**  
Add sizing classes to control individual columns.

```html
<div class="row">
    <div class="col-xxs-12 col-sm-6"></div>
    <div class="col-xxs-12 col-sm-6"></div>
    <div class="col-xxs-12 col-sm-4"></div>
    <div class="col-xxs-12 col-sm-4"></div>
    <div class="col-xxs-12 col-sm-4"></div>
</div>
```

**Auto widths**  
Add `.col-auto` and columns naturally space themselves equaly to fit the row.

```html
<div class="row">
    <div class="col-auto"></div>
    <div class="col-auto"></div>
    <div class="col-auto"></div>
    <div class="col-auto"></div>
</div>

<div class="row">
    <div class="col-auto"></div>
    <div class="col-auto"></div>
    <div class="col-auto"></div>
    <div class="col-auto"></div>
    <div class="col-auto"></div>
    <div class="col-auto"></div>
</div>
```

**Mixed sizing**  
Add a sizing class to the desired column and add `.col-auto` to the remainders, in order to fill the row with naturally spaced columns.

```html
<div class="row">
    <div class="col-xxs-6"></div>
    <div class="col-auto"></div>
    <div class="col-auto"></div>
</div>

<div class="row">
    <div class="col-auto"></div>
    <div class="col-xxs-6"></div>
    <div class="col-auto"></div>
</div>

<div class="row">
    <div class="col-auto"></div>
    <div class="col-auto"></div>
    <div class="col-auto"></div>
    <div class="col-xxs-8"></div>
</div>
```

## Nesting columns

Rows and columns are infinitely nestable inside other columns.

```html
<div class="row">
    <div class="col-xxs-12 col-sm-8">
        <div class="row">
            <div class="col-xxs-12 col-sm-8"></div>
            <div class="col-xxs-12 col-sm-4"></div>
        </div>
    </div>
</div>

<div class="row">
    <div class="col-xxs-12 col-sm-4">
        <div class="row">
            <div class="col-xxs-12 col-sm-6"></div>
            <div class="col-xxs-12 col-sm-6"></div>
        </div>
    </div>
</div>
```

## Offseting columns

Add `.col-{$breakpoint}-offset-*` to the desired columns to offset them.

```html
<div class="row">
    <div class="col-xxs-offset-3 col-xxs-6"></div>
</div>

<div class="row">
    <div class="col-xxs-offset-2 col-xxs-3"></div>
    <div class="col-xxs-3"></div>
    <div class="col-xxs-offset-1 col-xxs-3"></div>
</div>

<div class="row">
    <div class="col-xxs-4"></div>
    <div class="col-xxs-offset-4 col-xxs-4"></div>
</div>
```

# Columns direction

## Reverse

Add `.reverse` to the `.row` to invert the order of the columns.

```html
<div class="row reverse">
    <div class="col-xxs-2"> 1 </div>
    <div class="col-xxs-2"> 2 </div>
    <div class="col-xxs-2"> 3 </div>
    <div class="col-xxs-2"> 4 </div>
    <div class="col-xxs-2"> 5 </div>
    <div class="col-xxs-2"> 6 </div>
</div>
```

## Vertical

Add `.vertical` to the `.row` to display the columns in a vertical flow.

```html
<div class="row vertical">
    <div class="col-xxs-4"> 1 </div>
    <div class="col-xxs-4"> 2 </div>
    <div class="col-xxs-4"> 3 </div>
    <div class="col-xxs-4"> 4 </div>
    <div class="col-xxs-4"> 5 </div>
    <div class="col-xxs-4"> 6 </div>
</div>
```

## Vertical reverse

Add `.vertical-reverse` to the `.row` to display the columns in a reversed vertical flow.

```html
<div class="row vertical-reverse">
    <div class="col-xxs-12"> 1 </div>
    <div class="col-xxs-12"> 2 </div>
    <div class="col-xxs-12"> 3 </div>
    <div class="col-xxs-12"> 4 </div>
    <div class="col-xxs-12"> 5 </div>
    <div class="col-xxs-12"> 6 </div>
</div>
```

# Reorder columns

## First

Add `.col-{$breakpoint}-first` to easily make the desired column the first. Applies to either horizontal or vertical directions.

```html
<div class="row">
    <div class="col-xxs-2"> 1 </div>
    <div class="col-xxs-2"> 2 </div>
    <div class="col-xxs-2"> 3 </div>
    <div class="col-xxs-2"> 4 </div>
    <div class="col-xxs-2"> 5 </div>
    <div class="col-xxs-2 col-xxs-first"> 6 </div>
</div>
```

## Last

Add `.col-{$breakpoint}-last` to easily make the desired column the last (if nor other column has order specified). Applies to either horizontal or vertical directions.

```html
<div class="row">
    <div class="col-xxs-2 col-xxs-last"> 1 </div>
    <div class="col-xxs-2"> 2 </div>
    <div class="col-xxs-2"> 3 </div>
    <div class="col-xxs-2"> 4 </div>
    <div class="col-xxs-2"> 5 </div>
    <div class="col-xxs-2"> 6 </div>
</div>
```

# Items alignment

If you want the text to follow the alignment, simply add `.align-text` to the horizontal alignment class.

## Start

Add `.justify-start-{$breakpoint}` to the `.row` to align the columns to the start.

```html
<div class="row justify-start-sm align-text">
    <div class="col-xxs-6"></div>
</div>
```

```html
<div class="row justify-start-sm align-text">
    <div class="col-xxs-2"></div>
    <div class="col-xxs-2"></div>
    <div class="col-xxs-2"></div>
</div>
```

## Center

Add `.justify-center-{$breakpoint}` to the `.row` to align the columns to the center.

```html
<div class="row justify-center-sm align-text">
    <div class="col-xxs-6"></div>
</div>
```

```html
<div class="row justify-center-sm align-text">
    <div class="col-xxs-2"></div>
    <div class="col-xxs-2"></div>
    <div class="col-xxs-2"></div>
</div>
```

## End

Add `.justify-end-{$breakpoint}` to the `.row` to align the columns to the end.

```html
<div class="row justify-end-sm align-text">
    <div class="col-xxs-6"></div>
</div>
```

```html
<div class="row justify-end-sm align-text">
    <div class="col-xxs-2"></div>
    <div class="col-xxs-2"></div>
    <div class="col-xxs-2"></div>
</div>
```

## Top

Add `.align-top-{$breakpoint}` to the `.row` to align the columns to the end.

```html
<div class="row align-top-sm">
    <div class="col-xxs-6">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
        quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
        consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
        cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
        proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
    </div>
    <div class="col-xxs-6">
        col-6
    </div>
</div>
```

## Top

Add `.align-top-{$breakpoint}` to the `.row` to align the columns to the end.

```html
<div class="row align-top-sm">
    <div class="col-xxs-6">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
        quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
        consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
        cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
        proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
    </div>
    <div class="col-xxs-6">
        col-6
    </div>
</div>
```

## Middle

Add `.align-middle-{$breakpoint}` to the `.row` to align the columns to the end.

```html
<div class="row align-middle-sm">
    <div class="col-xxs-6">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
        quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
        consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
        cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
        proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
    </div>
    <div class="col-xxs-6">
        col-6
    </div>
</div>
```

## Bottom

Add `.align-bottom-{$breakpoint}` to the `.row` to align the columns to the end.

```html
<div class="row align-bottom-sm">
    <div class="col-xxs-6">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
        quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
        consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
        cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
        proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
    </div>
    <div class="col-xxs-6">
        col-6
    </div>
</div>
```

## Stretch

Add `.stretch-{$breakpoint}` to the `.row` to apply the same height to all columns.

```html
<div class="row stretch">
    <div class="col-xxs-3">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
        quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
        consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
        cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
        proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
    </div>
    <div class="col-xxs-3">
        col-3
    </div>
    <div class="col-xxs-3">
        col-3
    </div>
    <div class="col-xxs-3">
        col-3
    </div>
</div>
```

# Self alignment and stretch

Add `.align-self-_[alignment]_-{$breakpoint}` to the desired columns to align them indivudually or `.self-stretch-{$breakpoint}` to stretch them individually.

```html
<div class="row">
    <div class="col-xxs-2">
        col-2
    </div>
    <div class="col-xxs-2">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
        quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
        consequat.
    </div>
    <div class="col-xxs-2 align-self-start-sm">
        col-2
    </div>
    <div class="col-xxs-2 align-self-middle-sm">
        col-2
    </div>
    <div class="col-xxs-2 align-self-bottom-sm">
        col-2
    </div>
    <div class="col-xxs-2 self-stretch-sm">
        col-2
    </div>
</div>
```

# Distribution

## Space around

Add `.space-around-{$breakpoint}` to the `.row` to distribute the columns with equal space around them.

```html
<div class="row space-around-sm">
    <div class="col-xxs-2"></div>
    <div class="col-xxs-2"></div>
    <div class="col-xxs-2"></div>
</div>
```

## Space between

Add `.space-between-{$breakpoint}` to the `.row` to distribute the columns evenly: first item is on the start of the row, last item on the end of the row.

```html
<div class="row space-between-sm">
    <div class="col-xxs-2"></div>
    <div class="col-xxs-2"></div>
    <div class="col-xxs-2"></div>
</div>
```
