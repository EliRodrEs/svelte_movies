<script context="module">
  import { onMount } from "svelte";

  export async function load({fetch}){
    const res = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=285031c3b0efaff15415b39facc434ec&language=en-US&page=1`)
    const data = await res.json()
    console.log(data)
    if(res.ok){
      return {
        props: {popular: data.results}
      }
    }
  }

</script>

<script>
  import PopularMovies from "../components/PopularMovies.svelte";
  export let popular;
</script>

<section>
  <PopularMovies {popular}/>
</section>