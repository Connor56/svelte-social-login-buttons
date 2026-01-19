# Svelte Social Login Buttons

Drop-in sign-in buttons for Svelte 5. To see an example visit the documentation
website here: https://connor56.github.io/svelte-social-login-buttons/

<img width="567" height="466" alt="image" src="https://github.com/user-attachments/assets/c11d17ef-f1fa-413b-9d2a-b326d58b96e4" />

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
