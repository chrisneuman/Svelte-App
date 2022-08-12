<script>
 
    import { copy } from '$lib';

    let text = 'https://www.vote.org/polling-place-locator/';

    const error = (event) => {
        alert(event.detail.message);
    };
</script>
<main class="col">
    <label for="text">Text To Copy:</label>

    <input
        id="text"
        type="text"
        placeholder="Text to copy..."
        bind:value={text} />

    <button use:copy={text} on:svelte-copy:error={error}>
        Copy
    </button>

  
</main>



<style>
    main {
        padding: 32px 12px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 2;
    }
</style>