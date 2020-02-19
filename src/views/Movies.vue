<template>
    <div>
        <div class="pageTitle">
            <h1>Movies</h1>
        </div>
        <div v-if="isLoading">Loading...    </div>
        <div v-if="!isLoading" class="movieList">
            <div class="movie" v-for="movie in movieList" v-bind:key="movie.id">
                <h1 class="fieldName">Title</h1>
                <div class="movieField">{{movie.title}}</div>
                <div class="smallFields">
                    <div class="flexItem">                    
                        <h1 class="fieldName smallField">Genre</h1>
                        <div class="movieField movieGenre">{{movie.genre}}</div>
                    </div>
                    <div class="flexItem">
                        <h1 class="fieldName smallField">Director</h1>                    
                        <div class="movieField movieDirector smallField">{{movie.director}}</div>
                    </div>
                    <div class="flexItem">
                        <h1 class="fieldName smallField">Release Date (US)</h1>
                        <div class="movieField movieRelease smallField">{{movie.releaseDate}}</div>
                    </div>
                </div>
                <h1 class="fieldName">Synopsis</h1>
                <div class="movieField movieSynopsis">{{movie.synopsis}}</div>
                <h1 class="fieldName">Review</h1>            
                <div class="movieField movieReview">{{movie.review}}</div>
                <h1 class="fieldName">Score</h1>
                <div class="movieField movieScore">{{movie.score}}</div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'movies',
    data: function (){
        return {
            movieList: [],
            hasErrors: false,
            isLoading: false
        }
    },    
    methods: {
        /*createMovie: function(){
            const movie = {
                id:'0',
                title: 'Star Wars: Episode IX - Rise of Skywalker',
                genre: 'Sci-Fi',
                director: 'J. J. Abrams',
                releaseDate: '20/12/2019',
                synopsis: 'A ghost of the sith returns and spreads terror throughout the galaxy! While Kylo Ren ventures forth to maintain his position, Rey embarks on a journey to find a powerful relic, accompanied by Finn and Poe.',
                review: 'WHYYYYYYYYYYYYYYYYYYYYYYYYYYY?!',
                score: '3/10'
            }
            this.movieList.push(movie);
        }*/
    },
    created: function() {
        this.isLoading = true
        axios.get('http://5e48a84b728fde0014e34e74.mockapi.io/movies')
            .then(response => {
                response.data.forEach(movie => {
                    this.movieList.push(movie)    
                });
                this.isLoading = false
            }).catch(err => {
                console.log(err)
                this.isLoading = false
            })
    }
}
</script>

<style scoped>
    
    .pageTitle{
        font-size: 20px;
        font-weight: bold;
        text-align: left;
        margin-left: 50px;
        padding-bottom: 30px;
    }

    .movie{
        font-size: 20px;
        text-align: left;
        margin-left: 150px;
        margin-right: 150px;
        margin-bottom: 100px;
        padding-left: 10px;
        padding-right: 10px;
        padding-top: 5px;
        padding-bottom: 5px;
        border-style: solid;
        border-width: 1px;

    }

    .fieldName{
        font-size: 15px;
        margin-top: 5px;
        margin-bottom: 5px;
    }

    .movieField{
        padding: 8px;
        border-style: solid;
        border-width: 1px;
        margin-left: 5px;
        margin-right: 5px;
        margin-bottom: 10px;
    }
    
    .smallFields{
        display: flex;
        flex-direction: row;
    }

    .flexItem{
        flex-grow:1
    }
</style>