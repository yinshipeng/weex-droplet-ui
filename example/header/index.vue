<template>
    <div class="wx-demo">
        <wx-header text="帮助" @wxBack="wxBackHandle"></wx-header>
    </div>
</template>
<script>
    import { WxHeader } from '../../index';
    const modal = weex.requireModule('modal');
    export default {
        components: {
            WxHeader
        },
        data () {
            return {

            }
        },
        created () {

        },
        methods: {
            wxBackHandle () {
                modal.toast({
                    message: 'back'
                })
            },
        }
    }
</script>
