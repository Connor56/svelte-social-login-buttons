# Svelte Social Login Buttons

Drop-in sign-in buttons for Svelte 5. To see an example visit the documentation
website here: https://connor56.github.io/svelte-social-login-buttons/

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
