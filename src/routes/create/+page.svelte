<script lang="ts">
	import { goto } from "$app/navigation";
    import { ChevronLeft } from "@lucide/svelte";
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

    function handleBack() {
        if (addingAction) {
            addNarratorAction = false;
            addPlayerAction = false;
            addingAction = false;
        } else {
            goto('/');
        }
    }
</script>

<div class="flex flex-col w-full border-b-2 border-gray-600 p-1">
    <button
        class="flex px-2 py-1 justify-around items-center max-w-[80px] mb-2 bg-white/10 hover:bg-white/20 hover:scale-105 rounded-lg transition-transform duration-200"
        on:click={handleBack}
    >
        <ChevronLeft />
        Back
    </button>
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