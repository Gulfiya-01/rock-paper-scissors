<script lang="ts">
    // import { onMount } from 'svelte';
    // import { w3cwebsocket as WebSocket } from 'websocket';
    import FirstStep from "./components/firstStep.svelte";
    import SecondStep from "./components/secondStep.svelte";
    import ThirdStep from "./components/thirdStep.svelte";
	import Footer from './components/Footer.svelte';
    import Rules from './components/Rules.svelte';
	import Header from './components/Header.svelte';
    // let socket;
    let showRules = false;
 
    let step: number = 1;
    let  selectedItem:string;

    function handleSetPage(event:CustomEvent) {
        const data = event.detail;
        step = data.page; 
        selectedItem = data.move; 
    } 
    function handleRulesOpen() {
        showRules = true;
    }

    function handleRulesClosed(event:CustomEvent) {
        step = event.detail.page;
        showRules = false;
    }
   
</script>

<main class="app">
    {#if !showRules} 
     <Header/>
        {#if step === 1}
            <FirstStep on:setpage={handleSetPage}/>
        {:else if step === 2}
            <SecondStep selectedItem={selectedItem} />
        {:else if step === 3}
            <ThirdStep selectedItem={selectedItem} on:setpage={(data) => step = data.detail.page} />
        {/if}
    <Footer on:openRules={handleRulesOpen}/>
    {/if}
    {#if showRules}
        <Rules step={step} on:setpage={handleRulesClosed} on:closeRules={handleRulesClosed} />
    {/if}
</main>

<style>
 .app {
    padding: 2rem;
    background: radial-gradient(134.00% 134.00% at 50% 0%, rgb(31, 55, 87), rgb(19, 21, 55) 100%);
    height: 100vh;
 }
</style>
