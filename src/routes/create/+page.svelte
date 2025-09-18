<script lang="ts">
    const actors = ["Narrator", "Player"];

    let addingAction = false;
    let addNarratorAction = false;
    let addPlayerAction = false;

    let selectedActor = '';

    function handleAdd(actor: string) {
        addingAction = true;
        if (actor === 'Narrator') addNarratorAction = true;
        if (actor === 'Player') addPlayerAction = true;
    }
</script>

<div class="flex flex-col w-full">
    {#if addingAction}
        <div>
            {#if addNarratorAction}
                <p>Narrator</p>
            {/if}
            {#if addPlayerAction}
                <p>Player</p>
            {/if}
        </div>
    {:else}
        <div class="flex justify-between w-full">
            {#each actors as a}
                <button on:click={() => handleAdd(a)} class="bg-white/10 px-2 py-1 rounded-lg hover:bg-white/20 hover:scale-105 transition-transform duration-200">{`Add ${a} Action`}</button>
            {/each}
        </div>
    {/if}
</div>