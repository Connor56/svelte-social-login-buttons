<script lang="ts">
	let { signInFunction } = $props();

	let isLoading = $state(false);

	async function handleGoogleSignIn() {
		isLoading = true;

		await signInFunction();
		isLoading = false;
	}
</script>

<div class="google-signin">
	<button
		onclick={handleGoogleSignIn}
		disabled={isLoading}
		class="google-signin__button"
		aria-label="Sign in with Google"
	>
		{#if isLoading}
			<svg
				class="google-signin__spinner"
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
				class="google-signin__logo"
				viewBox="0 0 24 24"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					fill="#4285F4"
					d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z"
				/>
				<path
					fill="#34A853"
					d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z"
				/>
				<path
					fill="#FBBC05"
					d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l2.85-2.22.81-.62z"
				/>
				<path
					fill="#EA4335"
					d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z"
				/>
			</svg>
			<span>Sign in with Google</span>
		{/if}
	</button>
</div>

<style>
	.google-signin {
		width: 100%;
	}

	.google-signin__button {
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

	.google-signin__button:hover:not(:disabled) {
		border-color: #9ca3af;
		background: #f9fafb;
		box-shadow: 0 6px 14px rgba(15, 23, 42, 0.12);
	}

	.google-signin__button:active:not(:disabled) {
		background: #f3f4f6;
		transform: translateY(1px);
	}

	.google-signin__button:focus-visible {
		outline: 2px solid #2563eb;
		outline-offset: 2px;
	}

	.google-signin__button:disabled {
		cursor: not-allowed;
		opacity: 0.6;
	}

	.google-signin__spinner {
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

	.google-signin__logo {
		width: 24px;
		height: 24px;
		flex-shrink: 0;
		transition: transform 0.2s ease;
	}

	.google-signin__button:hover:not(:disabled) .google-signin__logo {
		transform: scale(1.08);
	}

	@keyframes spin {
		to {
			transform: rotate(360deg);
		}
	}
</style>
