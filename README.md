# gatsby-remark-grid-tables [![Build Status][build-badge]][build-status] [![Coverage Status][coverage-badge]][coverage-status]

This plugin parses custom Markdown syntax to describe tables. It just includes [this package](https://github.com/zestedesavoir/zmarkdown/tree/master/packages/remark-grid-tables) in the gatsby-remark chain

It's useful for extending markdown tables to include things like rowspan, colspan etc.

It adds a new node type to the [mdast][mdast] produced by [remark][remark]: `gridTable`.

A `gridTable` mdast node can contain the following mdast node types:

* `tableHeader`
* `tableRow`
* `tableCell`

The stringified HTML result will be a `table`.

It is up to you to have CSS rules producing the desired result for these `table`.

## Syntax

For example:

```markdown
# Grid table

## Basic example

+-------+----------+------+
| Table Headings   | Here |
+-------+----------+------+
| Sub   | Headings | Too  |
+=======+==========+======+
| cell  | column spanning |
+ spans +----------+------+
| rows  | normal   | cell |
+-------+----------+------+
| multi | cells can be    |
| line  | *formatted*     |
|       | **paragraphs**  |
| cells |                 |
| too   |                 |
+-------+-----------------+
```

produces:

```html
<h1>Grid table</h1>
<h2>Basic example</h2>

<table>
  <thead>
    <tr>
      <th colspan="2" rowspan="1"><p>Table Headings</p></th>
      <th colspan="1" rowspan="1"><p>Here</p></th>
    </tr>
    <tr>
      <th colspan="1" rowspan="1"><p>Sub</p></th>
      <th colspan="1" rowspan="1"><p>Headings</p></th>
      <th colspan="1" rowspan="1"><p>Too</p></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td colspan="1" rowspan="2"><p>cell
spans
rows</p></td>
      <td colspan="2" rowspan="1"><p>column spanning</p></td>
    </tr>
    <tr>
      <td colspan="1" rowspan="1"><p>normal</p></td>
      <td colspan="1" rowspan="1"><p>cell</p></td>
    </tr>
    <tr>
      <td colspan="1" rowspan="1"><p>multi
line</p><p>cells
too</p></td>
      <td colspan="2" rowspan="1"><p>cells can be
<em>formatted</em>
<strong>paragraphs</strong></p></td>
    </tr>
  </tbody>
</table>
```

Note: the top of a cell must be indicated by `+-` followed by some `-` or `+` and finished by `-+`.  
So, this is not a correct cell:
```md
+--+
|a |
+--+
```

But, this is a correct cell:
```md
+---+
| a |
+---+
```

## Installation

[npm][npm]:

```bash
npm install remark-grid-tables
```


## License

[MIT][license] © [Zeste de Savoir][zds]

<!-- Definitions -->

[build-badge]: https://img.shields.io/travis/zestedesavoir/zmarkdown.svg

[build-status]: https://travis-ci.org/zestedesavoir/zmarkdown

[coverage-badge]: https://img.shields.io/coveralls/zestedesavoir/zmarkdown.svg

[coverage-status]: https://coveralls.io/github/zestedesavoir/zmarkdown

[license]: https://github.com/zestedesavoir/zmarkdown/blob/master/packages/remark-grid-tables/LICENSE-MIT

[zds]: https://zestedesavoir.com

[npm]: https://www.npmjs.com/package/remark-grid-tables

[remark]: https://github.com/remarkjs/remark

[mdast]: https://github.com/wooorm/mdast

[rehype]: https://github.com/rehypejs/rehype
