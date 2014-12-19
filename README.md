# rs-facet

Angular directive for [Canon](http://rackerlabs.github.io/canon) facets.

## Requirements

- AngularJS v1.3 or higher
- Canon v1.1 or higher

## Installation

This package is not currently published to either NPM or Bower. Once the API
stabilizes, the built files will be published. Until then, you can install
directly from the GitHub repository.

To install with Bower, add the following line to dependencies in your bower.json:

```
"rs-facet": "https://github.com/rackerlabs/rs-facet.git"
```

Once you have installed the package, you'll need to:

1. Include `rs-facet.js` or `rs-facet.min.js` in your application.
2. Add `rs.facet` to your main module's list of dependencies.

## Usage

### `rs-facet-group`

This directive defines a group of related facets.

```
<rs-facet-group name="Status" on-facet="filter($facets)" size="5" multiple>
  ...
</rs-facet-group>
```

#### Attributes

##### `name`

Type: `String`, Required

The name of the facet group.

##### `size`

Type: `Number`, Default: `undefined`

The number of facet items to be displayed within the group. When the number of
facet items exceeds the specified size, extra items will be hidden under a
collapsible section. When this attribute is not provided, all facet items will
be displayed.

##### `multiple`

Type: `Boolean`, Default: `false`

Specifies whether multiple items in a facet group may be selected. This
attribute can be used in two ways. First, the presence or absence of the
attribute will indicate whether multiple selection is enabled or disabled.
Second, the attribute can be used with an expression. Truthy values will enable
multiple selection and falsey values will disable multiple selection.

##### `on-facet`

Type: `Expression`, Default: `''`

An expression to be evaluated when a facet is selected or deselected. Several
special variables will be available within the scope of the expression.

- `$facets` - An array of all selected facets within a group.
- `$facet` - The first item in `$facets`. For facet groups that do not allow multiple selection, this is a shortcut for getting the selected value from the `$facets` array.

### `rs-facet-item`

This directive defines a single facet within a group, and it must be contained
within an `rs-facet-group` directive.

```
<rs-facet-item status="error" count="5" value="{ arbitrary: 'data' }" selected>Error</rs-facet-item>
```

#### Attributes

##### `status`

Type: `String`, Default: `undefined`

Specifies the status icon to be used with the facet. When this attribute is not
provided, a status icon will not be displayed.

- `ok` - Indicates a positive condition.
- `warning` - Indicates a warning condition.
- `error` - Indicates an error condition.

##### `count`

Type: `Number`, Default: `null`

Specifies the count that is displayed beside a facet item. When this attribute
is not provided, a count will not be displayed.

##### `selected`

Type: `Boolean`, Default: `false`

Specifies whether the facet is currently selected. This attribute can be used
in two ways. First, the presence or absence of the attribute will indicate
whether the facet is selected. Second, the attribute can be used with an
expression. Truthy values will select the facet.

##### `value`

Type: `Expression`, Default: `''`

The value represented by the facet item. These correspond to the values made
available in `$facet` and `$facets` when the `on-facet` expression is evaluated.


## License

rs-popover is released under the [MIT License](LICENSE).
