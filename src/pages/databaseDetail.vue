<template>
    <div id="databaseDetail">
        <div><img style="width: 100%;" src="../imgs/21.jpg" alt="picture"></div>
    </div>
</template>
<script>
    export default {
        name: 'databaseDetail',
        data() {
            return {
                msg: 'Welcome to Your Vue.js App'
            }
        },
        mounted: function () {
            var that = this;
            that.$http.get("https://service.chemlinked.com/api/v1/coslist/headinfo", {name: "abc"})
                .then(function (res) {
                    console.log('11', res.data.data)
                }, function (error) {
                    console.log('1ss')
                });

            that.$http.post("https://service.chemlinked.com/api/v1/coslist/search", {name: "abc"}, {emulateJSON: true})
                .then(function (res) {
                        console.log('22', res.data)
                    }, function (error) {
                        console.log('sss')
                    }
                );
        }
    }
</script>
<style lang="scss">

</style>


