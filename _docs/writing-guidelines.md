# Cheatsheet guidelines

## Content organisation

- **Progressive complexity:** Start with basics, move to advanced
- **Logical sections:** Group related functionality together
- **H2 and H3:** Organise documents into H2 and H3 sections

H2 content length:

- Short H2s: 2-4 H3s (e.g., "Installing", "Getting started")
- Medium H2s: 4-7 H3s (e.g., "Components", "Lifecycle")  
- Long H2s: 7+ H3s (use column layouts)

H3 content length:

- Focused: One main concept + examples
- Consistent: Similar depth within each H2
- Self-contained: Each H3 should be understandable independently

## Format

- Documentation is in the format of Markdown with Kramdown class extensions
- H3's can have the following class names:
  - `{: .-prime}` - Visually highlighted section. Only use once per document at most.
- PRE elements can have:
  - `{: .-setup}` - Visually muted section. Used for sections with less importance. Deprecated, use sparingly.
- H2's can have:
  - `{: .-three-column}` - use if the H3's are short, and if there are at least 3 H3's in the H2.
  - `{: .-two-column}` - the default

## Writing guidelines

- Aim for brevity
- Sentence case headings, never Title Case
- Omit explanations if they are obvious

## Content priorities

1. **Essential first**: Most commonly used 20% of functionality
2. **Progressive disclosure**: Basic → intermediate → advanced
3. **Practical examples**: Real-world use cases over theoretical
4. **Quick reference**: Dense information for experienced developers
5. **Learning path**: Logical progression for newcomers

## Examples

- Place documentation links in the end.
- Prefer to write explanations *after* a pre/table.

````markdonw
### Setting default props

```jsx
Hello.defaultProps = {
  color: 'blue'
}
```

Default properties are used if no properties are given.

See: [defaultProps](https://reactjs.org/docs/react-component.html#defaultprops)
````
