<template>
    <div class="main-container" id="app">
        <div id="app-6" class="title-container">
            <h1 class="title">Rubles conventor</h1>
        </div>
            <div>convert rubles to
            <select v-model="selected" v-on:change="convertCurrency()" >
                <option v-for="name1 in countries" :key="name1.id">{{name1}}</option>
            </select>
            </div>
        <div class="currency-container">
            <div >
                <input type="number" class="currency-input" v-on:change="test"  v-model="firstField">
            </div>
                <button class = "container2" v-on:click.native="test()">convert</button>
            <div class = "container">
                <p>{{secondField}}</p>
            </div>
        </div>
    </div>
</template>


<script>


    export default {
        name: "test1",
        data: function () {
            return {
                counter:0,
                selected :"",
                firstField : 0,
                secondField : 0,
                conventor:1,
                countries:
                    {
                        us: "USD",
                        brs: "BYN",
                        europe: "EUR",
                        chn: "CNY"
                    },


            }
        }, /*data end*/
        methods:
            {
                test :function(){
                    this.secondField = (this.conventor*this.firstField);
                },
                convertCurrency: function () {
                    var apiKey = '308296d8bc38fdc59cdc';
                    var fromCurrency = encodeURIComponent(this.selected);
                    var toCurrency = encodeURIComponent("RUB");
                    var query = fromCurrency + '_' + toCurrency;
                    var url = 'https://free.currconv.com/api/v7/convert?q='
                        + query + '&compact=ultra&apiKey=' + apiKey;
                    switch (query) {
                        case "USD_RUB" :
                            fetch(url)
                                .then(response => response.json())
                                .then(json => {
                                    this.conventor = json.USD_RUB;
                                });
                            break;

                        case "EUR_RUB" :
                            fetch(url)
                                .then(response => response.json())
                                .then(json => {
                                    this.conventor = json.EUR_RUB
                                });
                            break;

                        case "BYN_RUB" :
                            fetch(url)
                                .then(response => response.json())
                                .then(json => {
                                    this.conventor= json.BYN_RUB
                                });
                            break;

                        case "CNY_RUB" :
                            fetch(url)
                                .then(response => response.json())
                                .then(json => {
                                    this.conventor = json.CNY_RUB
                                });
                            break;
                    }
                    /*try catch for weak*/
                    if (this.conventor == 1)
                    {
                        fetch(url)
                            .then(response => response.json())
                            .then(json => {
                                this.secondField = json.error
                            });
                    }
                    this.secondField= this.conventor*this.firstField;
                }


            } /*method end*/

    }

</script>
<style>
    body {
        background: yellow;
    }
    .container{
        margin: 50px;
        justify-content: center;
        font-size: 20px;
        height: 40px;
        border-radius: 5px;
        border: 1px solid #CCC;
        padding: 10px;
        background: #ffffff;
    ;
    }
    button{
        width: 80%;
        height: 100%;
        margin: 50px;
    }
    button:hover {
        color: rgb(24,24,24);
        border: 1px solid rgb(198,198,198);
        background: #f7f7f7 linear-gradient(#f7f7f7, #f1f1f1);
        box-shadow: 0 1px 2px rgba(0,0,0,.1);
    }
    button:active {
        color: rgb(51,51,51);
        border: 1px solid rgb(204,204,204);
        background: rgb(238,238,238) linear-gradient(rgb(238,238,238), rgb(224,224,224));
        box-shadow: 0 1px 2px rgba(0,0,0,.1) inset;
    }

    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    .title-container {
        margin-bottom: 25px;
        margin-left: 0;
        text-align: center;

        .title {
            margin-right: 15px;
            text-align: left;
        }
    }
    .main-container {
        width: 800px;
        position: absolute;
        border-radius: 10px;
        padding: 50px;
        top: 40%;
        left: 50%;
        transform: translate(-50%, -40%);
        background: honeydew;
        box-shadow: 0 12px 10px -6px $blue-dark;
        ;
    }
    .currency-input {
        width: 70%;
        margin-right: 5px;
        font-size: 20px;
        height: 40px;
        border-radius: 5px;
        border: 1px solid #CCC;
        padding-left: 10px;
        text-align: center;
    }
</style>
провальный проект который даже на компоненты не стоит рассовывать