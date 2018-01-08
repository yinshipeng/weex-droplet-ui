# weex-droplet-ui

## 说明
目前使用weex-ui的项目结构开发

## install
npm i weex-droplet-ui -S

## run
npm start

## Usage
  
```html
<template>
    <div>
        <wx-button @wxClick="handleClick">点击测试</wx-button>
    </div>
</template>

<script>
    import { WxButton } from 'weex-droplet-ui';
    const modal = weex.requireModule('modal');
    // import WxButton from 'weex-droplet-ui/packages/wx-button';
    export default {
        components: { WxButton },
        methods: {
            handleClick () {
                modal.toast({
                    message: 'test'
                });
            }
        }
    };
</script>
```