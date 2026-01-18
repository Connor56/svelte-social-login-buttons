<script lang="ts">
	import { onMount } from 'svelte';
	import { GoogleSignInButton, XSignInButton, GitHubSignInButton } from '$lib';
	import hljs from 'highlight.js/lib/core';
	import typescript from 'highlight.js/lib/languages/typescript';
	import shell from 'highlight.js/lib/languages/shell';
	import 'highlight.js/styles/github-dark.css';
	
	hljs.registerLanguage('typescript', typescript);
	hljs.registerLanguage('shell', shell);

	onMount(() => {
		hljs.highlightAll();
	});

	async function mockSignIn() {
		await new Promise((resolve) => setTimeout(resolve, 900));
	};
</script>

<svelte:head>
	<title>Svelte Social Login Buttons</title>
	<meta
		name="description"
		content="Simple, accessible Svelte 5 social sign-in buttons. Includes a Google sign-in component."
	/>
</svelte:head>

<main class="page">
    <div class="title-container">
    <h1 style="font-size: 48px;">Svelte Social Login Buttons</h1>
    </div>
	<section class="hero">
		<p class="badge">Svelte 5 • Components</p>
		<p class="lede">
			Drop-in sign-in buttons with sensible defaults, accessibility, and customization.
		</p>
		<div class="cta-row" style="width: 100%;">
			<GoogleSignInButton signInFunction={mockSignIn} />
		</div>
		<div class="cta-row" style="width: 100%;">
			<GitHubSignInButton signInFunction={mockSignIn} />
		</div>
		<div class="cta-row" style="width: 100%;">
			<XSignInButton signInFunction={mockSignIn} />
		</div>
		<p class="hint">Demo buttons use a mocked async sign-in.</p>
	</section>

	<section class="section">
		<h2>Install</h2>
		<pre><code class="language-shell">npm install svelte-social-login-buttons</code></pre>
	</section>

	<section class="section">
		<h2>Usage</h2>
		<pre><code class="language-typescript">{`<script lang="ts">
  import { GoogleSignInButton } from 'svelte-social-login-buttons';

  async function signIn() {
    // Your auth flow here
  }
</script>

<GoogleSignInButton signInFunction={signIn} />`}</code></pre>
	</section>

	<section class="section grid">
		<div class="card">
			<h3>Props</h3>
			<ul>
				<li><code>signInFunction</code> — async callback invoked on click.</li>
			</ul>
		</div>
		<div class="card">
			<h3>Notes</h3>
			<ul>
				<li>Works with Svelte 5 (runes).</li>
			</ul>
		</div>
	</section>
</main>

<style>
	:global(body) {
		margin: 0;
		font-family: system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, sans-serif;
		color: #111827;
		background: #f9fafb;
	}

    .title-container {
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 50px;
    }

	.page {
		max-width: 980px;
		margin: 0 auto;
		padding: 64px 20px 96px;
	}

	.hero {
		background: #ffffff;
		border: 1px solid #e5e7eb;
		border-radius: 18px;
		padding: 32px;
		box-shadow: 0 10px 30px rgba(15, 23, 42, 0.08);
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.badge {
		display: inline-flex;
		align-items: center;
		gap: 8px;
		padding: 6px 12px;
		background: #eef2ff;
		color: #4338ca;
		border-radius: 999px;
		font-size: 12px;
		font-weight: 600;
		letter-spacing: 0.04em;
		text-transform: uppercase;
		margin-bottom: 16px;
	}

	h1 {
		margin: 0 0 8px;
		font-size: 36px;
		line-height: 1.1;
	}

	.lede {
		margin: 0 0 24px;
		color: #4b5563;
		font-size: 18px;
	}

	.cta-row {
		max-width: 360px;
		margin-bottom: 16px;
	}

	.hint {
		margin-top: 14px;
		color: #6b7280;
		font-size: 13px;
	}

	.section {
		margin-top: 32px;
	}

	.section h2 {
		margin-bottom: 12px;
		font-size: 22px;
	}

	pre {
		background: #111827;
		color: #e5e7eb;
		padding: 16px;
		border-radius: 12px;
		overflow-x: auto;
		font-size: 14px;
	}

	.grid {
		display: grid;
		gap: 16px;
		grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
	}

	.card {
		background: #ffffff;
		border: 1px solid #e5e7eb;
		border-radius: 14px;
		padding: 18px;
	}

	.card h3 {
		margin: 0 0 10px;
		font-size: 18px;
	}

	ul {
		margin: 0;
		padding-left: 18px;
		color: #4b5563;
	}
</style>
