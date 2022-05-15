<script>
    import {pokemon} from "../stores/pokestore";
    import PokemanCard from "../components/pokemanCard.svelte";
    
    let searchTerm = "";
    let filteredPokemon = [];

    $: {
        if(searchTerm){
            filteredPokemon = $pokemon.filter(pokeman => pokeman.name.toLowerCase().includes(searchTerm.toLowerCase()));
        }else {
            filteredPokemon = [...$pokemon];
        }
    }
</script>
<svelte:head>
    <title>
        Svelte Kit Pokedex
    </title>
</svelte:head>
<h1 class="text-4xl text-center my-8 uppercase">Svelte Kit Pokedex</h1>

<input type="text" placeholder="Search Pokemon" bind:value={searchTerm} class="w-full rounded-md text-lg p-4 border-2 border-gray-200">

<div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1">

    {#each filteredPokemon as pokem}
        <PokemanCard pokeman={pokem} />
    {/each}

</div>
