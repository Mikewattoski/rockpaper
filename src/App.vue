<template>
<div id="app">
    <h1 class="text-center">Rock Paper scissors game</h1>
    <br>
    <br>
    <br>
    <br>
    <h4 class="text-center" v-if="start">
        You choose {{userPick}} ---- Computer choose {{randPick}}
    </h4>
    <br>
    <div class="card">
        <div class="card-body text-center">
            {{userScore}}
        </div>
    </div>
    <br>
    <h3 class="text-center">{{result}}</h3>
    <br>
    <div class="card">
        <div class="card-body text-center">
            {{computerScore}}
        </div>
    </div>
    <br>
    <div class="text-center">
        <button type="button" class="btn btn-outline-light" @click="choose('rock') &check()">
            <i class="fa fa-hand-rock-o"></i>
        </button>

        <button type="button" class="btn btn-outline-light" @click="choose('paper') &check()">
            <i class="fa fa-hand-paper-o"></i>
        </button>
        <button type="button" class="btn btn-outline-light" @click="choose('scissors') &check()">
            <i class="fa fa-hand-scissors-o"></i>
        </button>
    </div>
</div>
</template>

<script>
export default {
    name: 'app',
    data() {
        return {
            computerScore: 0,
            userScore: 0,
            result: '',
            userPick: '',
            randPick: '',
            start: false
        }
    },
    methods: {
        check() {
            if (this.computerScore == 5) {
                alert('computer wins')
                this.computerScore = 0
                this.userScore = 0
                this.start = false
            } else if (this.userScore == 5) {
                alert('You wins')
                this.computerScore = 0
                this.userScore = 0
                this.start = false

            }

        },
        choose: function (pick) {
            this.start = true
            this.userPick = pick;
            const picks = ['rock', 'paper', 'scissors'];
            this.randPick = picks[Math.floor(Math.random() * picks.length)];
            this.setScore();
        },
        setScore: function () {
            if (this.userPick == 'rock') {
                if (this.randPick == 'paper') {
                    this.result = 'Computer wins';
                    this.computerScore++;
                } else if (this.randPick == 'scissors') {
                    this.result = 'User wins';
                    this.userScore++;
                } else {
                    this.result = 'Draw';
                }
            } else if (this.userPick == 'paper') {
                if (this.randPick == 'rock') {
                    this.result = 'User wins';
                    this.userScore++;
                } else if (this.randPick == 'scissors') {
                    this.result = 'Computer wins';
                    this.computerScore++;
                } else {
                    this.result = 'Draw';
                }
            } else {
                if (this.randPick == 'rock') {
                    this.result = 'Computer wins';
                    this.computerScore++;
                } else if (this.randPick == 'paper') {
                    this.result = 'User wins';
                    this.userScore++;
                } else {
                    this.result = 'Draw';
                }
            }
        }
    },

}
</script>

<style>
</style>
