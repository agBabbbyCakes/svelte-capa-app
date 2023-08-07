<script>
	import Slideshow from './Slideshow.svelte';
	import { wallet } from './WalletStore.js';
	import { onMount } from 'svelte';
	import { ethers } from 'ethers';
	import { Wallet } from '@wagmi/core';
	
	let provider;
	let signer;
	let connected = false;

	onMount(() => {
	  setupWalletConnect();
	});
	
	async function setupWalletConnect() {
	  provider = new Wallet.Provider.WalletConnectProvider({
		rpc: {
		  1: "https://mainnet.infura.io/v3/YOUR_INFURA_PROJECT_ID"
		  // Add other networks if necessary
		}
	  });
	  
	  await provider.enable();
	  
	  signer = new ethers.providers.Web3Provider(provider).getSigner();
	  wallet.set(signer);  // Update the wallet store with the connected signer
	  connected = true;
	}
	
	async function disconnect() {
	  await provider.close();
	  wallet.set(null);
	  connected = false;
	}
</script>

<main>
	<h1>babbycakes 11 Slideshow App</h1>
	<Slideshow />
	<header>
		This is a header (html)
	</header>
	<div>
		<h3>Updates</h3>
		<ul><li>Added WalletStore </li></ul>
	</div>

	<!-- WalletConnect UI elements -->
	<div>
		{#if connected}
			<button on:click={disconnect}>Disconnect</button>
		{:else}
			<button on:click={setupWalletConnect}>Connect with WalletConnect</button>
		{/if}
	</div>

	<footer>
		Is this reayoooolly html footer? (svelte updated)
	</footer>
	<b>how can svelte be used to link up to other things?</b>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #0040ff;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
