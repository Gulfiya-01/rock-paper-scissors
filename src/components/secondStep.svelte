<script lang="ts">
	import { createEventDispatcher } from "svelte";
    export let selectedItem:string;
    const dispatch = createEventDispatcher();
   
    function selectMove(move:string) {
    dispatch('setpage', { page: 3, move }); 
    }
</script>

<section class="second-step">
    <p >Selected Item: {selectedItem} </p>
</section>


<style>
    
   </style>
   