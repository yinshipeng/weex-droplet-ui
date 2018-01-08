<template>
    <div class="wx-demo" style="margin-top:100px;margin-left:100px;">
        <wx-checkbox 
            text="我已阅读《xxx》" 
            v-model="checked"
            checkedColor="#027FF3"
            :defaultChecked="checked"
            align="left"
            :disabled="false"
            @wxChange="handleChange">
        </wx-checkbox>
        <text>value：{{ checked }}</text>
    </div>
</template>
<script>
    import { WxCheckbox } from '../../index';
    const modal = weex.requireModule('modal');
    export default {
        components: {
            WxCheckbox,
        },
        data () {
            return {
                 checked: false,
                 wxchange: false,
            }
        },
        created () {

        },
        methods: {
            handleChange (checked) {
                console.log(checked)
            },
        }
    }
</script>
