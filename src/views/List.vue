<template>
    <div>
        <div class="page-title">
            <h1>Movies</h1>
        </div>
        <div class="loading">
            <h1>Loading...</h1>
        </div>
        <div class="movie-list">
            <table>
                <thead>
                    <th>Title</th>
                    <th>Genre</th>
                    <th>Score</th>
                    <th></th>
                </thead>
                <tbody>
                    <tr>
                        <td>Run</td>
                        <td>Thriller</td>
                        <td>9/10</td>
                        <td>More...</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: "list",
    data: function(){
        return {
            title: '',

        }
    }
}
</script>

<style scoped>

</style>