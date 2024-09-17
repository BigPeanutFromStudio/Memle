<script lang="ts">
  import Card from './components/Card.svelte';

  const mapToMemeCard = (meme: any): MemeCard =>{
    return {
      id: meme.id,
      name: meme.name,
      url: meme.blank
    };
  };

  const memes : Promise<MemeCard[]> = (async () =>{
    const response = await fetch('https://api.memegen.link/templates');
    const rawMemes = await response.json();
    return rawMemes.map(mapToMemeCard);
  })();

</script>

<main>
  
  {#await memes}
  <p>...loading</p>
  {:then data}
  <div class="memes">
    {#each data as meme}
      <Card memeData={meme} />
    {/each}
  </div>
  {:catch error}
  <p>Ups hihi</p>
  {/await}

</main>

<style>

.memes{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 50px;
  margin: 50px;
}
</style>