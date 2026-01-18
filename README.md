# Svelte Social Login Buttons

**Svelte 5 • Components**

Drop-in sign-in buttons with sensible defaults, accessibility, and customization.

## Install

```sh
npm install svelte-social-login-buttons
```

## Usage

```html
<script lang="ts">
  import { GoogleSignInButton } from 'svelte-social-login-buttons';

  async function signIn() {
    // Your auth flow here
  }
</script>

<GoogleSignInButton signInFunction={signIn} />
```

## Components

- `GoogleSignInButton`
- `GitHubSignInButton`
- `XSignInButton`

## Props

- `signInFunction` — async callback invoked on click.

## Notes

- Works with Svelte 5 (runes).

## License

MIT
