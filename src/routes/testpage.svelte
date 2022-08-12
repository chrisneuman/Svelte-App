<script>
  //  import 'ghostsui';
    import { copy } from '$lib';

    let text = 'madatyourmom.com';

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

    <div class="col">
        <h1>Events</h1>

        <button
            use:copy={'MadAtYourMom.com'}
            on:svelte-copy={(e) => alert(e.detail)}
            on:svelte-copy:error={error}>
            Click to Open an alert
        </button>
    </div>
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