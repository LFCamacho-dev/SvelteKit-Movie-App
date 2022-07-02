<script context="module">

    export async function load({ fetch, params }){
        const res = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=${import.meta.env.VITE_API}&language=en-US&query=${params.id}&page=1`);
        const data = await res.json();
        // console.log(data);

        if (res.ok) {
            return {
                props: {
                    searchedMovie: data.results
                }
            }
        }
        

        
    }
</script>


<script>
    import PopularMovies from "../../components/PopularMovies.svelte";

    export let searchedMovie;
</script>

<section>
    <PopularMovies movies={searchedMovie}/>
</section>