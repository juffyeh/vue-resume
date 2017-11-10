<template>
    <div id="editor">
        <nav>
            <ol>
                <li v-for="i in [0,1,2,3,4,5]"
                    v-bind:class="{active : currentTab === i}"
                    v-on:click="currentTab = i"
                    >
                    <svg class="icon">
                        <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
                    </svg>
                </li>
            </ol>
        </nav>
        <ol class="panes">
            <li v-bind:class="{active: currentTab === 0}">Tab1</li>
            <li v-bind:class="{active: currentTab === 1}">Tab2</li>
            <li v-bind:class="{active: currentTab === 2}">Tab3</li>
            <li v-bind:class="{active: currentTab === 3}">Tab4</li>
            <li v-bind:class="{active: currentTab === 4}">Tab5</li>
            <li v-bind:class="{active: currentTab === 5}">Tab6</li>
        </ol>
    </div>
</template>
<script>
    export default{
        data(){
            return{
                currentTab: 0,
                icons: ['sfz','bag','book','project','cup','phone']
            }
        }
    }
</script>
<style lang="scss">
#editor{
    min-height: 100px;
    display: flex;
    > nav{
        width: 80px;
        background: #000;
        > ol > li{
            padding: 16px 0;
            text-align: center;
            > .icon{
                width: 24px;
                height: 24px;
                fill: #fff;
            }
            &.active{
                background: #fff;
                > .icon{
                    fill: #000;
                }
            }
        }
    }
    > .panes{
        >li{
            display: none;
            &.active{
                display: block;
            }
        }
    }
}
</style>
