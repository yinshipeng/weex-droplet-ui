<template>
    <div class="wx-radio-items">
        <div class="wx-radio-item" 
            v-for="item in items" 
            @click="handleClick(item)">
            <text :style="textStyles" v-if="align === 'left'" class="wx-radio-label-right">{{ item.label }}</text>
            <div class="wx-radio"
                :style="getRadioStyle(item)"
                :class="[item.checked ? 'wx-radio-checked' : 'wx-radio-nochecked']">
                <text v-if="item.checked" :style="checkedStyle" class="checked"></text>
            </div>
            <text :style="textStyles" v-if="align === 'right'" class="wx-radio-label-left">{{ item.label }}</text>
        </div>
    </div>
</template>
<style scoped>
    .wx-radio-items {
        flex-direction: row;
    }

    .wx-radio-item {
        flex-direction: row;
        align-items: center;
        padding-right: 20px;
    }

    .wx-radio-label-right {
        padding-right: 10px;
    }

    .wx-radio-label-left {
        padding-left: 10px;
    }

    .wx-radio {
        position: relative;
        border-radius: 40px;
    }

    .wx-radio-checked {
        border-width: 0px;
    }

    .wx-radio-nochecked {
        background-color: #fff;
        border-width: 2px;
        border-style: solid;
        border-color: #ddd;
    }

    .checked {
        /*width: 20px;*/
        /*height: 20px;*/
        /*border-radius: 20px;*/
        background-color: #fff;
        position: absolute;
        /*top: 10px;*/
        /*left: 10px;*/
        z-index: 100;
    }

</style>
<script>
    export default {
        props: {
            size: {
                type: String,
                default: '50px'
            },
            align: {
                type: String,
                default: 'left'
            },
            items: {
                type: Array,
                default: function () {
                    return []
                },
                required: true
            },
            checkedColor: {
                type: String,
                default: '#027FF3'
            },
            textColor: {
                type: String,
                default: '#4D4D4D'
            },
            textFontSize: {
                type: String,
                default: '32px'
            }
        },

        data () {
            return {
                checkedStyle: {},
                textStyles: {},
            }
        },

        created () {
            this.setCheckedStyle();
            this.setTextStyle();
        },

        methods: {
            setTextStyle () {
                this.textStyles = {
                    color: this.textColor,
                    fontSize: this.textFontSize
                };
            },

            setCheckedStyle () {
                const value = Number(this.size.replace('px', '')) / 2;
                const size = value + 'px';
                this.checkedStyle = {
                    height: size,
                    width: size,
                    'border-radius': size,
                    top: value / 2 + 'px',
                    left: value / 2 + 'px',
                };
            },

            getRadioStyle (item) {
                return {
                    height: this.size,
                    width: this.size,
                    'border-radius': this.size,
                    'background-color': item.checked ? this.checkedColor : '#fff',
                };
                
            },

            handleClick (item) {
                this.items.forEach(el => {
                    el.checked = false;
                });
                item.checked = true;
                this.$emit('wxChange', item);
            },
        }
    }
</script>