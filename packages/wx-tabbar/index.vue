<template>
    <div class="wx-tabbar">
        <div class="tab-component" :style="{'transform': translateX, width: totalWidth + 'px'}">
            <slot></slot>
        </div>
        <div class="tabbar" 
            :style="{'bottom': bottom}">
            <div class="tabbar-item" 
                v-for="item in tabItems" 
                @click="changeTab(item)">
                <image v-if="selectedTab.index === item.index" :src="item.selectedImage" class="icon"></image>
                <image v-if="selectedTab.index !== item.index" :src="item.image" class="icon"></image>
                <text class="wx-text">{{ item.title }}</text>
            </div>
        </div>
    </div>
</template>
<style scoped>
    .wx-tabbar {
        
    }

    .tab-component {
        flex-direction: row;
        background-color: #fff;
    }   

    .tabbar {
        flex-direction: row;
        width: 750px;
        height: 100px;
        position: fixed;
        left: 0;
        right: 0;
        z-index: 1000;
        border-top-width: 1px;
        border-top-style: solid;
        border-top-color: #D8D8D8;
        background-color: #fff;
    }

    .tabbar-item {
        flex: 1;
        align-items: center;
        justify-content: center;
    }

    .icon {
        margin-top: 14px;
        margin-bottom: 10px;
        width: 38px;
        height: 38px;
        line-height: 38px;
    }

    .wx-text {
        font-size: 28px;
        padding-top: 2px;
        text-align: center;
        color: #646464;
    }

</style>
<script>
    export default {
        props: {
            tabItems: {
                type: Array,
                default: function () {
                    return []
                },
                required: true
            },

            bottom: {
                type: String,
                default: '0px'
            }
        },

        data () {
            return {
                selectedTab: {index: 0},
                translateX: 'translateX(0px)', 
                deviceWidth: 750,
            }
        },

        created () {
            this.totalWidth = this.deviceWidth * this.tabItems.length;
            this.setTranslateX();
        },

        methods: {
            changeTab (item) {
               this.selectedTab = item;
               this.setTranslateX();
               this.$emit('wxChange', item);
            },

            setTranslateX () {
                const x = this.selectedTab.index * this.deviceWidth;
                this.translateX = `translateX(-${x}px)`;
            },
        }
    }
</script>