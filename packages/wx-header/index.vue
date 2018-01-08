<template>
    <div class="wx-header">
        <!-- default -->
        <slot>
            <div class="header-title">
                <text class="title">{{ text }}</text>
            </div>
            <div class="header-arrow" 
                @click="handleClick" 
                v-if="hasBackIcon">
                <text class="icon-arrow-left"></text>
            </div>
        </slot>
        <!-- customer slot layout 'left center right' -->
        <slot name="header-left"></slot>
        <slot name="header-center"></slot>
        <slot name="header-right"></slot>
    </div>
</template>
<style scoped>
    .wx-header {
        border-bottom-width: 1px;  
        border-style: solid;  
        border-color:  #DCDCDC;  
        height: 100px;
        background-color: #fff;
    }

    .header-arrow {
        position: absolute;
        left: 0px;
        top: 0px;
        /*browser*/
        z-index: 100;
        width: 100px;
        height: 100px;
    }

    .icon-arrow-left {
        border-right-width:3px ;
        border-right-style: solid;
        border-right-color: #000;
        border-bottom-style: solid;
        border-bottom-width: 3px;  
        border-bottom-color:  #000; 
        width: 32px;
        height: 32px;  
        transform: rotate(135deg); 
        margin-left: 46px;
        margin-top: 34px;
    }

    .header-title {
        width: 750px;
        height: 100px;
    }

    .title {
        width: 750px;
        font-size: 40px;
        text-align: center;
        color: #333333;
        height: 100px;
        line-height: 100px;
    }
    
</style>
<script>
    export default {
        props: {
            hasBackIcon: {
                type: Boolean,
                default: true
            },
            text: {
                type: String,
                default: ''
            },
            useDefaultBack: {
                type: Boolean,
                default: true
            },
        },

        created () {

        },

        methods: {
            handleClick () {
                if (this.useDefaultBack) {
                    this.$router.back()
                } else {
                    this.$emit('wxBack')
                }
            }
        }
    }
</script>