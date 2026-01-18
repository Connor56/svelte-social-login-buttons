<script lang="ts">
	let { signInFunction } = $props();

	let isLoading = $state(false);

	async function handleGitHubSignIn() {
		isLoading = true;

		await signInFunction();
		isLoading = false;
	}
</script>

<div class="github-signin">
	<button
		onclick={handleGitHubSignIn}
		disabled={isLoading}
		class="github-signin__button"
		aria-label="Sign in with GitHub"
	>
		{#if isLoading}
			<svg
				class="github-signin__spinner"
				xmlns="http://www.w3.org/2000/svg"
				fill="none"
				viewBox="0 0 24 24"
			>
				<circle class="spinner-track" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4">
				</circle>
				<path
					class="spinner-path"
					fill="currentColor"
					d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"
				></path>
			</svg>
			<span>Signing in...</span>
		{:else}
			<svg
				class="github-signin__logo"
				viewBox="0 0 24 24"
				xmlns="http://www.w3.org/2000/svg"
				fill="currentColor"
			>
				<path
					d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
				/>
			</svg>
			<span>Sign in with GitHub</span>
		{/if}
	</button>
</div>

<style>
	.github-signin {
		width: 100%;
	}

	.github-signin__button {
		width: 100%;
		display: inline-flex;
		align-items: center;
		justify-content: center;
		gap: 12px;
		padding: 14px 24px;
		border-radius: 9999px;
		border: 1px solid #d1d5db;
		background: #ffffff;
		color: #374151;
		font-size: 16px;
		font-weight: 600;
		cursor: pointer;
		box-shadow: 0 1px 2px rgba(15, 23, 42, 0.08);
		transition: border-color 0.2s ease, background 0.2s ease, box-shadow 0.2s ease,
			transform 0.2s ease;
	}

	.github-signin__button:hover:not(:disabled) {
		border-color: #9ca3af;
		background: #f9fafb;
		box-shadow: 0 6px 14px rgba(15, 23, 42, 0.12);
	}

	.github-signin__button:active:not(:disabled) {
		background: #f3f4f6;
		transform: translateY(1px);
	}

	.github-signin__button:focus-visible {
		outline: 2px solid #2563eb;
		outline-offset: 2px;
	}

	.github-signin__button:disabled {
		cursor: not-allowed;
		opacity: 0.6;
	}

	.github-signin__spinner {
		width: 20px;
		height: 20px;
		color: #4b5563;
		animation: spin 1s linear infinite;
	}

	.spinner-track {
		opacity: 0.25;
	}

	.spinner-path {
		opacity: 0.75;
	}

	.github-signin__logo {
		width: 24px;
		height: 24px;
		flex-shrink: 0;
		transition: transform 0.2s ease;
		color: #1f2328;
	}

	.github-signin__button:hover:not(:disabled) .github-signin__logo {
		transform: scale(1.08);
	}

	@keyframes spin {
		to {
			transform: rotate(360deg);
		}
	}
</style>
