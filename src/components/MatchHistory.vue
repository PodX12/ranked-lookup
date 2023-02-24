<template>
    <div class="hello">
        <div>
            <div>
                <input class="text-input" type="text" placeholder="Type mc name here..." v-model="mcName" />
                <button @click="getUserUUID()">Search</button>
            </div>

            {{ JSON.stringify(this.user) }}
            <hr />
            {{ JSON.stringify(this.matches) }}
        </div>
    </div>
</template>

<script>
export default {
    name: 'MatchHistory',
    data() {
        return {
            mcName: "podx12",
            user: null,
            matches: null
        }
    },
    methods: {
        getUserUUID: function () {
            console.log(this.mcName);
            fetch(`https://api.ashcon.app/mojang/v2/user/${this.mcName}`)
                .then((response) => response.json())
                .then((data) => { this.user = data; this.getMatchHistory() });
        },
        getMatchHistory: function() {
            fetch(`https://mcsrranked.com/api/users/${this.user.uuid}/matches`)
                .then((response) => response.json())
                .then((data) => this.matches = data);
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}

.text-input {
    padding: 10px 10px;
    border-radius: 4px;
    border: none;
    text-align: center;
    width: 500px;
    font-size: 18px;
}

button {
    padding: 10px;
    font-size: 18px;
    background: #42b983;
    border: none;
    border-radius: 4px;
    margin-left: 5px;
}
</style>
