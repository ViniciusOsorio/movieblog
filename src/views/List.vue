<template>
    <div>
        <div class="page-title">
            <h1>Movies</h1>
        </div>
        <div v-if="isLoading" class="loading">
            <h1>Loading...</h1>
        </div>
        <div v-if="!isLoading" class="movie-list">
            <table>
                <thead>
                    <th>#</th>
                    <th>TITLE</th>
                    <th>GENRE</th>
                    <th>SCORE</th>
                    <th>DETAILS</th>
                </thead>
                <tbody>
                    <tr v-for="movie in movieList" v-bind:key="movie.id">
                        <td>{{movie.id}}</td>
                        <td>{{movie.title}}</td>
                        <td>{{movie.genre}}</td>
                        <td>{{movie.score}}</td>
                        <td>More...</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: "list",
    data: function(){
        return {
            movieList: [],
            hasErrors: false,
            isLoading: false
        }
    },
    methods:{

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
    table{
        margin-left: 15%;
        margin-right: 15%;
        width: 70%;
        text-align: center;
        margin-bottom: 5%;
        background-color: black
    }

    td{
        background-color: white
    }

    td{
        font-weight: bold;
    }

    th{
        font-size: 25px;
        color: white;
    }

    table, th, td{
        border: 1px solid black;
        padding-top: 3px;
        padding-bottom: 3px;
    }

    .page-title{
        text-align: center;
        margin-right: 20%;
        margin-left: 20%;
    }

</style>