<template>
    <div>
        <div class="page-title">
            <h1>Submit New Review</h1>
        </div>
        <div class="outer-margin">
            <div class="movie">
                <div class="input-rows">
                    <div class="flex-item">
                        <h1 class="field-name large-field-name">Title</h1>
                        <input type="text" class="input title-input" v-model="title" />
                    </div>
                </div>
                <div class="input-rows">
                    <div class="flex-item">                    
                        <h1 class="field-name small-field-name">Genre</h1>
                        <select name="genre" class="input input-small" v-model="genre">
                            <option class ="input-small" value="Action">Action</option>
                            <option class ="input-small" value="Adventure">Adventure</option>
                            <option class ="input-small" value="Comedy">Comedy</option>
                            <option class ="input-small" value="Drama">Drama</option>
                            <option class ="input-small" value="Fantasy">Fantasy</option>
                            <option class ="input-small" value="Horror">Horror</option>
                            <option class ="input-small" value="Romance">Romance</option>
                            <option class ="input-small" value="Sci-Fi">Sci-Fi</option>
                        </select>
                    </div>
                    <div class="flex-item">
                        <h1 class="field-name small-field-name">Director</h1>                    
                        <input type="text" class="input input-small" v-model="director"/>
                    </div>
                    <div class="flex-item">
                        <h1 class="field-name small-field-name">Release Date (US)</h1>
                        <input type="date" class="input input-small" v-model="releaseDate" value="2020-02-18"/>
                    </div>
                </div>
                <div class="input-rows">
                    <div class="flex-item">
                        <h1 class="field-name large-field-name">Synopsis</h1>
                        <textarea class="input large-text" v-model="synopsis" />
                    </div>
                </div>
                <div class="input-rows">
                    <div class="flex-item">
                        <h1 class="field-name large-field-name">Review</h1>            
                        <textarea class="input large-text" v-model="review" />
                    </div>
                </div>
                <div class="input-rows">
                    <div class="flex-item">
                        <h1 class="score-field">Score</h1>
                        <div>
                            <select name="score" class="input score-input" v-model="score">
                                <option value="1">1</option>
                                <option value="2">2</option>
                                <option value="3">3</option>
                                <option value="4">4</option>
                                <option value="5">5</option>
                                <option value="6">6</option>
                                <option value="7">7</option>
                                <option value="8">8</option>
                                <option value="9">9</option>
                                <option value="10">10</option>
                            </select>
                            /10
                        </div>
                    </div>
                </div>
                <div class="input-rows">
                    <div class="flex-item">
                        <input type="button" class="button" value="Submit"/>                        
                    </div>                    
                </div>
                <div class="input-rows">
                    <div class="flex-item">
                        <input type="button" class="button clear-button" value="Clear"/>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: `submit`,
    data: function(){
        return {
            id: '',
            title: '',
            genre: '',
            director: '',
            releaseDate: moment().format("MMM Do YY"),
            synopsis: '',
            review: '',
            score: '',
            movieList: [],
            hasErrors: false
        }
    },
    methods: {
        createMovie: function(){
            const movie = {
                id: this.movieID(),
                title: this.title,
                genre: this.genre,
                director: this.director,
                releaseDate: this.releaseDate
            }
        },

        movieID: function(){
            if(!this.movieList.length){
                return 0;
            }else{
                return ;
            }
        }
    }
}

</script>

<style scoped>

.outer-margin{
    margin-left: 15.1%;
    margin-right: 15.1%;
    margin-bottom: 50px;
}

.page-title{
    font-size: 20px;
    font-weight: bold;
    text-align: center;
    padding-bottom: 30px;
}

.movie{
    font-size: 20px;
    text-align: left;    
    border-style: solid;
    border-width: 1px;
    width: 100%;
}

.title-input{
    margin-left: 5%;
    width: 90%;
    height: 35px;
}

.input-small{
    width: 71%;
    height: 35px;
    margin-left: 36px;
}

.large-text{
    height: 200px;
    width: 90%;
    margin-left: 5%;
}

.score-input{
    height: 35px;
    margin-left: 43%;    
}

.field-name{
    font-size: 15px;
    margin-top: 5px;
    margin-bottom: 5px;    
}

.small-field-name{
    margin-left: 10%;
}

.large-field-name{
    margin-left: 2%;
}

.score-field{
    font-size: 15px;
    margin-top: 5px;
    margin-bottom: 5px;
    margin-left: 39%;
}

.input{    
    margin-bottom: 10px;   
}

.input-rows{
    display: flex;
    flex-direction: row;
}

input, select {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}

.flex-item{
    flex-grow:1
}

.button{
    height: 35px;
    width: 100px;
    margin-bottom: 5px;
    margin-top: 10px;
    margin-left: 40%;
}

.clear-button{
    margin-bottom: 30px;
}

</style>