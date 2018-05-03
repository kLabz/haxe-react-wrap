This feature has been merged in `haxe-react`, and will be available starting next release (current version being `1.4.0`). It is already available using `haxelib git react https://github.com/massiveinteractive/haxe-react`.

# `@:wrap` support for haxe-react

Use the power of `@:jsxStatic` to wrap a component with multiple wrappers/HOCs: redux's `connect`, i18n with intl, react-router's `withRouter`, etc. with a simple meta.

To wrap a component with a single wrapper:

```haxe
@:wrap(ReactRouter.withRouter)
class MyComponentWithRouter extends ReactComponentOfProps<MyProps>
{
	// ...
}

// And use it with
jsx('<$MyComponentWithRouter />')
```

You can also combine wrappers, `@:wrap` instructions' order will be respected (the first one will be the entry point, and the last one will provide the final props to the component):

```haxe
@:wrap(ReactRouter.withRouter)
@:wrap(ReactIntl.injectIntl)
class MyComponentWithWrappers extends ReactComponentOfProps<MyProps>
{
	// ...
}

// And use it with
jsx('<$MyComponentWithWrappers />')
```

Will generate the equivalent of `MyComponentWithWrappers = ReactRouter.withRouter(ReactIntl.injectIntl(MyComponent))`

