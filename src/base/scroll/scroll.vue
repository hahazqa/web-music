<template>
    <div ref="wrapper">
        <slot></slot>
    </div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
    props: {
        probeType:{
            type:Number,
            default:1
        },
        click: {
            type:Boolean,
            default:true,
        },
        data: {
            type:Array,
            default:null
        }
    },
    mounted() {
        setTimeout(()=>{
            this._initScroll()
        },20)
    },
    methods: {
        _initScroll() {
            this.scroll = new BScroll(this.$refs.wrapper, {
                probeType:this.probeType,
                click:this.click
            })
        },
        enable() {
            this.scroll && this.scroll.enable()
        },
        disable() {
            this.scroll && this.scroll.disable()
        },
        refresh() {
            this.scroll && this.scroll.refresh()
        }
    },
    watch: {
        data() {
            setTimeout(()=>{
                // console.log(1)
                this.refresh()
            },20)
        }
    }    
}
</script>

<style lang="stylus" scoped>

</style>
