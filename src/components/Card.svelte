<script lang="ts">
    export let memeData : MemeCard
</script>

<div class="card">
    <img src={memeData.url} alt={memeData.name} />
    <h2 class="title">{memeData.name}</h2>
</div>

<style>
    .card{     
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    img{
        width: 300px;
        object-fit: cover;
    }
    .title{
        color: white;
        text-align: center;
    }
</style>