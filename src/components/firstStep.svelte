<script lang="ts">
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    function selectMove(move:string) {
        dispatch('setpage', { page: 2, move });
    }
</script>

<section class="first-step">
    <p>Logic for item selection</p>
    <label>
        <input type="radio" name="move" value="rock" on:change={() => selectMove('rock')} />
        Rock
    </label>
    <label>
        <input type="radio" name="move" value="paper" on:change={() => selectMove('paper')} />
        Paper
    </label>
    <label>
        <input type="radio" name="move" value="scissors" on:change={() => selectMove('scissors')} />
        Scissors
    </label>
    </section>
    