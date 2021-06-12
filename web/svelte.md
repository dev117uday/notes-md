---
description: better than vue ?
---

# Svelte

## Learning Svelte

### Reactive Components

Svelte components are saved in : `.svelte` format

#### Hello World

```jsx
<script>
let name = 'world'
</script>

<h1>Hello {name.toUpperCase()}!</h1>
```

#### Dynamic Image

```jsx
<script>
    let src = 'tutorial/image.gif';
</script>

<img {src} alt="A man dances.">
```

#### Full component

```jsx
<p>{text}</p>

<script>
let text = 'This is a paragraph.'
</script>

<style>
    p {
        color: purple;
        font-family: 'Comic Sans MS', cursive;
        font-size: 2em;
    }
</style>
```

#### HTML strings

```jsx
<script>
    let string = `this string contains some <strong>HTML!!!</strong>`;
</script>

<p>{@html string}</p>
```

#### Functions Binding

```jsx
<script>
    let count = 0;
    function handleClick() {
        count += 1
    }
</script>

<button on:click={handleClick}>
    Clicked {count} {count%2 == 1 ? 'time' : 'times'}
</button>
```

#### Reactive Assignments

```jsx
<script>
    let count = 0;
    $: doubled = count * 2;
    function handleClick() {
        count += 1;
    }
</script>

<button on:click={handleClick}>
    Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
<p>{count} doubled is {doubled}</p>
```

#### Reactive Statements

```jsx
<script>
    let count = 0;
    $: if (count >= 10) {
        alert(`count is dangerously high!`);
        count = 9;
    }
    function handleClick() {
        count += 1;
    }
</script>

<button on:click={handleClick}>
    Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
```

### Nested Components

#### Main File

```jsx
<script>
    import Nested from './Nested.svelte';
</script>

<Nested answer={42}/>
<Nested/>
```

#### Nested.svelte File

```jsx
<script>
    // Requires export keyword to receive prop
    // default value
    export let answer = 'a mystery';
</script>

<p>The answer is {answer}</p>
```

### Conditional Logic

### If Else Block

```text
<script>
    let user = { loggedIn: false };

    function toggle() {
        user.loggedIn = !user.loggedIn;
    }
</script>

{#if user.loggedIn}
    <button on:click={toggle}>
        Log out
    </button>
{:else}
    <button on:click={toggle}>
        Log in
    </button>
{/if}
```

#### If Else-If Else Block

```jsx
<script>
    let x = 7;
</script>

{#if x > 10}
    <p>{x} is greater than 10</p>
{:else if 5 > x}
    <p>{x} is less than 5</p>
{:else}
    <p>{x} is between 5 and 10</p>
{/if}
```

#### For Each Block

```jsx
<ul>
    {#each cats as cat}
        <li><a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
            {cat.name}
        </a></li>
    {/each}
</ul>
```

#### Await For Promise

```jsx
<script>
    async function getRandomNumber() {
        const res = await fetch(`tutorial/random-number`);
        const text = await res.text();
        if (res.ok) {
            return text;
        } else {
            throw new Error(text);
        }
    }

    let promise = getRandomNumber();
    function handleClick() {
        promise = getRandomNumber();
    }
</script>

<button on:click={handleClick}>
    generate random number
</button>

{#await promise}
    <p>...waiting</p>
{:then number}
    <p>The number is {number}</p>
{:catch error}
    <p style="color: red">{error.message}</p>
{/await}

// Another way to catching promise
{#await promise then value}
    <p>the value is {value}</p>
{/await}
```

#### Data Binding

### js\# Input Binding

```jsx
<script>
    let name = 'world';
</script>

<input bind:value={name}>
<h1>Hello {name}!</h1>
```

#### CheckBox Binding

```jsx
<script>
    let yes = false;
</script>

<label>
    <input type=checkbox bind:checked={yes}>
    Yes! Send me regular email spam
</label>

{#if yes}
    <p>Thank you. We will bombard your inbox and sell your personal details.</p>
{:else}
    <p>You must opt in to continue. If you're not paying, you're the product.</p>
{/if}

<button disabled={!yes}>
    Subscribe
</button>
```

#### Group Input Binding

```jsx
<script>
    let scoops = 1;
    let flavours = ['Mint choc chip'];

    let menu = [
        'Cookies and cream',
        'Mint choc chip',
        'Raspberry ripple'
    ];

    function join(flavours) {
        if (flavours.length === 1) return flavours[0];
        return `${flavours.slice(0, -1).join(', ')} and ${flavours[flavours.length - 1]}`;
    }
</script>

<h2>Size</h2>

<label>
    <input type=radio bind:group={scoops} value={1}>
    One scoop
</label>
<label>
    <input type=radio bind:group={scoops} value={2}>
    Two scoops
</label>
<label>
    <input type=radio bind:group={scoops} value={3}>
    Three scoops
</label>
<h2>Flavours</h2>

{#each menu as flavour}
    <label>
        <input type=checkbox bind:group={flavours} value={flavour}>
        {flavour}
    </label>
{/each}

{#if flavours.length === 0}
    <p>Please select at least one flavour</p>
{:else if flavours.length > scoops}
    <p>Can't order more flavours than scoops!</p>
{:else}
    <p>
        You ordered {scoops} {scoops === 1 ? 'scoop' : 'scoops'}
        of {join(flavours)}
    </p>
{/if}
```

#### Text Area Binding

```jsx
<script>
    import marked from 'marked';
    let value = `Some words are *italic*, some are **bold**`;
</script>

<textarea bind:value={value}></textarea>

{@html marked(value)}

<style>
    textarea { width: 100%; height: 200px; }
</style>
```

#### Select Bindings

```jsx
<select bind:value={selected} on:change="{() => answer = ''}">
    {#each questions as question}
        <option value={question}>
            {question.text}
        </option>
    {/each}
</select>
```

#### Content editable bindings

```jsx
<script>
    let html = '<h1>Write some text!</h1>';
</script>

<div contenteditable="true" bind:innerHTML={html}></div>

<pre>{html}</pre>

<style>
    [contenteditable] {
        padding: 0.5em;
        border: 1px solid #eee;
        border-radius: 4px;
    }
</style>
```

