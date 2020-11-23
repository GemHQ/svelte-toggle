# svelte-toggle

[![NPM][npm]][npm-url]
[![Build][build]][build-badge]

> Accessible toggle switch component.

This component implements best practices from the [Inclusive Components guide](https://inclusive-components.design/toggle-button/) for toggle buttons.

Try it in the [Svelte REPL](https://svelte.dev/repl/7eee5c643a684315a4fdfe45964aca61?version=3.24.1).

## [Demo](https://metonym.github.io/svelte-toggle/)

## Install

```bash
yarn add -D svelte-toggle
# OR
npm i -D svelte-toggle
```

## Usage

### Basic

```svelte
<script>
  import Toggle from "svelte-toggle";

  let toggled;
</script>

<Toggle bind:toggled />

<strong>Toggled? {toggled ? 'Yes' : 'No'}</strong>
```

### Switch descriptors

Customize the toggle switch descriptors through the "on" and "off" props.

```svelte
<Toggle on="On" off="Off" />
```

Alternatively, you can use named slots:

```svelte
<Toggle on off>
  <span style="margin-left: .5rem" slot="on">"on" descriptor</span>
  <span style="margin-left: .5rem" slot="off">"off" descriptor</span>
</Toggle>
```

### Small variant

```svelte
<Toggle small />
```

### Custom colors

```svelte
<Toggle
  switchColor="#eee"
  toggledColor="#24a148"
  untoggledColor="#fa4d56"
/>
```

### Hidden label

```svelte
<Toggle hideLabel label="My toggle label" />
```

### Fully controlled

`ToggleCore` is an unstyled component that provides the accessibility attributes for the label and button elements.

```svelte
<script>
  import { ToggleCore } from "svelte-toggle";
</script>

<ToggleCore {toggled} let:label let:button>
  <!-- svelte-ignore a11y-label-has-associated-control -->
  <label {...label}>Label</label>
  <button
    {...button}
    on:click={() => {
      toggled = !toggled;
    }}>
    {toggled ? 'On' : 'Off'}
  </button>
</ToggleCore>
```

## API

API for the default `Toggle` component.

| Prop name      | Value                                                        |
| :------------- | :----------------------------------------------------------- |
| id             | `string` (default: `"toggle" + Math.random().toString(36)"`) |
| label          | `string` (default: `"Label"`)                                |
| hideLabel      | `boolean` (default: `false`)                                 |
| small          | `boolean` (default: `false`)                                 |
| toggled        | `boolean` (default: `true`)                                  |
| disabled       | `boolean` (default: `false`)                                 |
| on             | `string` (default: `undefined`)                              |
| off            | `string` (default: `undefined`)                              |
| switchColor    | `string` (default: `"#fff"`)                                 |
| toggledColor   | `string` (default: `"#0f62fe"`)                              |
| untoggledColor | `string` (default: `"#8d8d8d"`)                              |

## Dispatched events

The `Toggle` component dispatches a "change" event.

```svelte
<script>
  let events = [];
</script>

<Toggle
  on:change={({ detail }) => {
    events = [...events, detail.toggled];
  }}
/>

<strong>Events:</strong> {events.join(', ')}
```

## Forwarded events

- on:click
- on:mouseover
- on:mouseenter
- on:mouseout
- on:focus
- on:blur
- on:keydown

## [Changelog](CHANGELOG.md)

## License

[MIT](LICENSE)

[npm]: https://img.shields.io/npm/v/svelte-toggle.svg?color=%230f62fe
[npm-url]: https://npmjs.com/package/svelte-toggle
[build]: https://travis-ci.com/metonym/svelte-toggle.svg?branch=master
[build-badge]: https://travis-ci.com/metonym/svelte-toggle
