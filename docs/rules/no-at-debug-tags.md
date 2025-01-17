---
pageClass: "rule-details"
sidebarDepth: 0
title: "@ota-meshi/svelte/no-at-debug-tags"
description: "disallow the use of `{@debug}`"
since: "v0.0.1"
---

# @ota-meshi/svelte/no-at-debug-tags

> disallow the use of `{@debug}`

- :gear: This rule is included in `"plugin:@ota-meshi/svelte/recommended"`.

## :book: Rule Details

This rule reports all uses of `{@debug}`.

The `{@debug}` should be removed when you no longer need it after you use it for debugging.

<eslint-code-block>

<!--eslint-skip-->

```svelte
<script>
  /* eslint @ota-meshi/svelte/no-at-debug-tags: "error" */
</script>

<!-- ✗ BAD -->
{@debug user}
{@debug user1, user2, user3}
{@debug}
```

</eslint-code-block>

## :wrench: Options

Nothing.

## :books: Further Reading

- [Svelte - Tutorial > 18. Debugging / The @debug tags](https://svelte.dev/tutorial/debug)

## :rocket: Version

This rule was introduced in @ota-meshi/eslint-plugin-svelte v0.0.1

## :mag: Implementation

- [Rule source](https://github.com/ota-meshi/eslint-plugin-svelte/blob/main/src/rules/no-at-debug-tags.ts)
- [Test source](https://github.com/ota-meshi/eslint-plugin-svelte/blob/main/tests/src/rules/no-at-debug-tags.ts)
