<template>
    <div>
        <div>
            <p>{{blockTitle}}</p>
        </div>
        <div v-html="apiInfo" id="info"></div>
        <div id="info">{{json}}</div>
        <ButtonUpdate @click="getApiInfo"></ButtonUpdate>
    </div>
</template>

<script>
import ButtonUpdate from './ButtonUpdate.vue';

export default {
    name: 'ApiInfoBlock',
    data() {
        return {
            apiInfo: "",
            json: {}
        }
    },
    components: {
        // HelloWorld
        ButtonUpdate
    },
    props: {
        apiUrl: {
            type: String,
            required: true
        },
    },
    computed: {
        blockTitle() {
            return "Информация получена через API : " + this.apiUrl
        }
    },
    methods: {
        getApiJson: async function (url) {
            let response = await fetch(url);
            this.json = await response.json();
            return true;
        },
        parseJson: function (apiResponseJson) {
            // let tmp
            Object.entries(apiResponseJson).forEach(([key, value]) => {
                if (typeof value === "object" && value !== null) {
                    this.parseJson(value);
                } else {
                    this.apiInfo += `${key} : ${value}<br>`;
                    // tmp = "{" + `${key} : ${value}` + "}"
                    // console.log(tmp)
                    // this.apiInfo[key] = `${value}`
                    // Object.assign(this.apiInfo, `${key} : ${value}`)
                }
            });
        },
        getApiInfo: async function () {
            await this.getApiJson(this.apiUrl)
            this.apiInfo = ""
            this.parseJson(this.json)
        },
        // 
        // !!!!!!!!!!!!!!!!!!! Разобраться почуму срабатывает по второму нажатию кнопки, написать нормальные стили !!!!!!!!!!!!
        // 
    }
}
</script>

<style scoped>
#info {
    background-color: lightgreen;
    border: 1px solid black;
    width: 80%;
    height: 200px;
    margin: 10px;
    overflow: scroll;
}
</style>