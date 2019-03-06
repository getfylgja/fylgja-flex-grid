# Fylgja - Flex Grid

Create a complete grid using flexbox.
And only set the columns you need.

Making it even smaller than other flex grids.

## Installation

```bash
npm install @fylgja/flex-grid --save-dev
```

## How to use

Include the flex-grid package in to your code, via.

```scss
@import "@fylgja/flex-grid/flex-grid";
```

This grid does not work like Bootstrap with a 12 column layout.
Or some other grid that uses 24 columns.
This only makes your CSS bigger with unused columns.
Which is more unused CSS.

The power of the flex-grid is in it's smallness.
For each Media Query there are amount of columns set.
So for example on mobile you might only need 2 columns.
Then you can set the flex-grid to only load 2 columns.

So to create something like this.

```html
<div class="flex-grid">
    <div class="cell sm-2">item 1</div>
    <div class="cell sm-2">item 2</div>
</div>
```

Each cell size is 100% divided by `$i`.

Making it way more clear what size you can set.
And unlike 12 column grid you can set a 5 column grid row.
Since each column you create is based on the 100% divided by `$i`.

### Classes

_$mq = @media, e.g. `.sm-2` or `.lg-2`_

`.flex-grid`: Sets the grid and this is also the wrapper class. (required)

`.cell`: Sets the grid item (required)

*  `.${mq}-${1}`: the grid item size
*  `.${mq}-grow`: the grid item size that grows to fit the available space
*  `.${mq}-shrink`: the grid item size that shrinks to fit the content size

**Depends on the booleans set, [see config](#config)**

`.-gap`: modifier class to set grid gap

`.-fill`: modifier class to makes each cell equal height and it's content.
Works great with cards.

`.offset-${mq}-${i}`: set the cell offset, from left.

## Config

By default the config is set for the smallest use case.
So many configs are disabled or load only what is needed.

### Booleans

| Var                 | Default | Description                             |
| ------------------- | ------- | --------------------------------------- |
| $enable-flex-gap    | true    | Load the gap directly without gap class |
| $enable-flex-fill   | false   | Enable the fill class                   |
| $enable-flex-offset | false   | Enable the cell offset classes          |

### Setters

| Var              | Default                      | Description                    |
| ---------------- | ---------------------------- | ------------------------------ |
| $flex-grid-gaps  | ()                           | Additional gaps to load        |
| $flex-grid-cells | xs 2, sm 3, md 4, lg 5, xl 5 | Amount of cells to load per MQ |
| $gap-size        | 1rem                         | The default gap size           |

### Breakpoints

All breakpoints are set via the SCSS map `$breakpoints`.
Each point is based on the bootstrap naming.

See the upcoming Fylgja helperUtil module for more information.

## Helper (mixins)

The flex grid is build using a few helper mixins.
You can use the helpers if you need a little more than the config can offer you.

| mixin            | options | Description                   |
| ---------------- | ------- | ----------------------------- |
| flex-grid-mq     | $mq     | Create a mq with if statement |
| flex-grid-gap    | $size   | Create a grid gap             |
| flex-grid-cell   | $mq, $i | Create a cell size            |
| flex-grid-offset | $mq, $i | Create a cell offset size     |

## FAQ

<details><summary>What is mq?</summary>

As stated under the section [How to use, classes](#Classes)

mq is shorthand for media query.

</details>

<details><summary>Why is there a hyphen before some classes?</summary>

Some classes are modifier classes.
And we wanted to have different naming,
to separate them from normal css class naming.

In the upcoming framework you will see a little more of this.
And we will also add a section to explain our css naming convention.

So good stuff to come 😉

</details>

<details><summary>Why should I still use a flex-grid instead of a CSS Grid</summary>

While it is not an valid answer to say browser support.

Since you can use CSS grid in IE11, via Explicit grid (fixed size).

Flex-grid makes sense for flexable grids.
Where you don't know the layout, before hand.

</details>

<details><summary>Why release a flex-grid in 2019</summary>

The Fylgja flex-grid was part of our private code base for a long time.

_Even had a LESS version._

With our near completion of Fylgja we also wanted to share this piece of history.
That is is still usable for many cases even in 2019.

</details>

