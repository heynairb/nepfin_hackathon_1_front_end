<template>
    <div class="center">
        <div class="wrapper">
            <div v-bind:class="['cabo', cabo]">Cabo</div>
            <div v-bind:class="['kiawah', kiawah]">Kiawah</div>
            <div v-bind:class="['huron', huron]">Huron</div>
            <div v-bind:class="['omaha', omaha]">Omaha</div>
        </div>
    </div>
</template>

<script>
    import Room from "./Room.vue"
    import axios from "axios";
    let baseurl = "http://localhost:8000";
    export default {
        name: "Office",
        component: {
            room: Room
        },
        mounted(){
            this.getServerState();
        },
        data() {
            return {
                cabo: "empty",
                huron: "empty",
                kiawah: "empty",
                omaha: "empty",
                user: "brian"
            }
        }, methods: {
            getServerState(){
                let that = this;
                axios.get(baseurl+"/main/").then(function(response){
                    console.log(response.data);
                    that.huron = response.data.huron ? "empty" : "filled";
                    that.cabo = response.data.cabo ? "empty" : "filled";
                    that.kiawah = response.data.kiawah ? "empty" : "filled";
                    that.omaha = response.data.omaha ? "empty" : "filled";
                    setTimeout(that.getServerState, 1000);
                }).catch(function(){
                    setTimeout(that.getServerState, 1000);
                });
            },
            //
            // updateServerState(){
            //     let that = this;
            //     axios.post("", {
            //         cabo: that.caboState !== "empty",
            //         huron: that.huronState !== "empty",
            //         omaha: that.omahaState !== "empty",
            //         kiawah: that.kiawahState !== "empty"
            //     }).then(function(response){
            //         console.log(response);
            //     });
            // }
        }
    }
</script>

<style scoped>
    .empty {
        background-color: green;
    }

    .filled {
        background-color: red;
    }

    .center {
        display: inline-block;
        width: 66%;
    }

    .wrapper {
        display: grid;
        grid-template-columns: 21% 37% 42%;
        grid-template-rows: 27% 8% 18% 17% 30%;
        width: 100%;
        height: 100vh;
    }

    .cabo {
        grid-column-start: 1;
        grid-column-end: 2;
        grid-row-start: 1;
        grid-row-end: 3;
        border: 6px dashed black;
    }

    .kiawah {
        grid-column-start: 1;
        grid-column-end: 2;
        grid-row-start: 3;
        grid-row-end: 4;
        border: 6px dashed black;
        border-top: 3px;
    }

    .huron {
        grid-column-start: 1;
        grid-column-end: 2;
        grid-row-start: 4;
        grid-row-end: 5;
        border: 6px dashed black;
        border-top: 3px;
    }

    .omaha {
        grid-column-start: 3;
        grid-column-end: 4;
        border: 6px dashed black;
    }
</style>