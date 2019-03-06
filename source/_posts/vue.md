---
title: vue
date: 2019-03-04 22:50:21
tags: vue
categories: web
---
- [Component](#component)
  - [define component `image.vue`](#define-component-imagevue)
  - [use component `main.vue`](#use-component-mainvue)
- [Debug](#debug)
  - [dependency](#dependency)
  - [command](#command)
  
<!-- more -->

# Component
## define component `image.vue`
```html
<template>
   <div>
     <img v-bind:src="image.src">
   </div>
</template>

<script>
export default{
    props:[image]
}
</script>

<style scoped>
div{
    width:100px;
    display:inline-block
}
</style>
```

## use component `main.vue`
```html
<template>
    <div>
        <myImage 
        v-for="image in images"
        v-key="image.id"
        v-bind="image">
        </myImage>
    </div>
</template>

<script>
import myImage from './image.vue'
var app = new Vue({
    el:"#app",
    data:{
        images:[
            {key:1,src:'./1.jpg'},
            {key:2,src:'./2.jpg'}
        ]
    }
})

</script>

<style scoped>
</style>
```


# Debug
## dependency
`npm install -g @vue/cli-service-global`

## command
`vue serve *.vue`