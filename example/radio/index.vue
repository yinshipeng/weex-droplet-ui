<template>
    <div class="wx-demo">
        <wx-radio 
            checkedColor="#027FF3"
            size="50px"
            align="left"
            textColor="#4D4D4D"
            textFontSize="32px"
            :items="items"
            @wxChange="handleChange">
        </wx-radio>
        <text style="margin-top:100px;">{{ selected.label }}</text>
    </div>
</template>
<style type="text/css">
    .wx-demo {
        margin-top: 100px;
        margin-left: 100px;
    }
</style>
<script>
    import { WxRadio } from '../../index';
    const modal = weex.requireModule('modal');
    export default {
        components: {
            WxRadio,
        },
        data () {
            return {
                 items: [
                    {label: '有公积金', value: '0', checked: true},
                    {label: '无公积金', value: '1', checked: false},
                 ],
                 selected: null,
            }
        },
        created () {
            this.selected = this.items[0]
        },
        methods: {
            handleChange (item) {
                this.selected = item;  
            },
        }
    }
</script>
