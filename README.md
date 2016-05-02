*   [Foxgrid](#foxgrid)
    *   [Columns](#columns)
    *   [Breakpoints](#nbreakpoints)
    *   [Gutter per breakpoint](#gutter)
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
*   [Self alignment and stretch](#self-alignment)
*   [Distribution](#distrubution)
    *   [Space around](#space-around)
    *   [Space between](#space-between)

<article class="container">

# Foxgrid

Foxgrid follows some rules to work properly:

*   Rows must be placed within a `.container` for proper alignment, or just add the class `.no-gutter-row` to remove the negative margin
*   Use rows to wrap columns (they're the ones with `display: flex`)

And has the following options fully customizable:

## Columns

12 columns by default

    $grid-columns: 12 !default;

## Breakpoints

6 mobile first breakpoints

    $breakpoints: (
        xxs: '', // default
        xs: '640px',
        sm: '768px',
        md: '992px',
        lg: '1200px',
        xl: '1600px'
    );

Which can be used with the following media queries:

    /* Extra extra small devices (less than 640px)
    No media query since this is the default */

    /* extra small devices (640+ px)
    @media (min-width: map-get($breakpoints, xs) { ... }

    /* small devices (tablet in portrait, 768+ px)
    @media (min-width: map-get($breakpoints, sm) { ... }

    /* medium devices (small desktops, tablet in landscape, 992+ px)
    @media (min-width: map-get($breakpoints, md) { ... }

    /* large devices (desktops, laptops, 1200+ px)
    @media (min-width: map-get($breakpoints, lg) { ... }

    /* extra large devices (large desktops, 1600+ px)
    @media (min-width: map-get($breakpoints, xl) { ... }

## Gutter per breakpoint

Custom gutter for each breakpoint

    $gutter-map: (
        xxs: 10,
        xs:  10,
        sm:  30,
        md:  30,
        lg:  30,
        xl:  30
    );

and a set of helper variables for standalone usage

    $gutter-xxs: map-get($gutter-map, xxs);
    $gutter-xs:  map-get($gutter-map, xs);
    $gutter-sm:  map-get($gutter-map, sm);
    $gutter-md:  map-get($gutter-map, md);
    $gutter-lg:  map-get($gutter-map, lg);
    $gutter-xl:  map-get($gutter-map, xl);

</article>
