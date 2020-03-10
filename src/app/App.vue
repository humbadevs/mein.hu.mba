<template>
    <div class="">
        <div class="">
            <div class="">
                <div class="">
                    <div v-if="alert.message" :class="`px-4 py-3 rounded absolute m-3 ${alert.type}`">{{alert.message}}</div>
                    <router-view></router-view>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { mapState, mapActions } from 'vuex'

export default {
    name: 'app',
    computed: {
        ...mapState({
            alert: state => state.alert
        })
    },
    methods: {
        ...mapActions({
            clearAlert: 'alert/clear'
        })
    },
    watch: {
        $route (to, from){ // eslint-disable-line no-unused-vars
            // clear alert on location change
            this.clearAlert();
        }
    }
};
</script>
