<script lang="ts">
	let { signInFunction } = $props();

	let isLoading = $state(false);

	async function handleXSignIn() {
		isLoading = true;

		await signInFunction();
		isLoading = false;
	}
</script>

<div class="x-signin">
	<button
		onclick={handleXSignIn}
		disabled={isLoading}
		class="x-signin__button"
		aria-label="Sign in with X"
	>
		{#if isLoading}
			<svg
				class="x-signin__spinner"
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
				class="x-signin__logo"
				viewBox="0 0 24 24"
				xmlns="http://www.w3.org/2000/svg"
				fill="currentColor"
			>
				<path
					d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"
				/>
			</svg>
			<span>Sign in with X</span>
		{/if}
	</button>
</div>

<style>
	.x-signin {
		width: 100%;
	}

	.x-signin__button {
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

	.x-signin__button:hover:not(:disabled) {
		border-color: #9ca3af;
		background: #f9fafb;
		box-shadow: 0 6px 14px rgba(15, 23, 42, 0.12);
	}

	.x-signin__button:active:not(:disabled) {
		background: #f3f4f6;
		transform: translateY(1px);
	}

	.x-signin__button:focus-visible {
		outline: 2px solid #2563eb;
		outline-offset: 2px;
	}

	.x-signin__button:disabled {
		cursor: not-allowed;
		opacity: 0.6;
	}

	.x-signin__spinner {
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

	.x-signin__logo {
		width: 24px;
		height: 24px;
		flex-shrink: 0;
		transition: transform 0.2s ease;
		color: #000000;
	}

	.x-signin__button:hover:not(:disabled) .x-signin__logo {
		transform: scale(1.08);
	}

	@keyframes spin {
		to {
			transform: rotate(360deg);
		}
	}
</style>
