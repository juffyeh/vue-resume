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
            <li v-bind:class="{active: currentTab === 0}">
                <ProfileEditor v-bind:profile="profile"/>
            </li>
            <li v-bind:class="{active: currentTab === 1}">
                <WorkHistoryEditor v-bind:workHistory="workHistory"/>
            </li>
            <li v-bind:class="{active: currentTab === 2}">
                <h2>学习经历</h2>
            </li>
            <li v-bind:class="{active: currentTab === 3}">
                <h2>项目经历</h2>
            </li>
            <li v-bind:class="{active: currentTab === 4}">
                <h2>获奖情况</h2>
            </li>
            <li v-bind:class="{active: currentTab === 5}">
                <h2>联系方式</h2>
            </li>
        </ol>
    </div>
</template>
<script>
    import ProfileEditor from './ProfileEditor'
    import WorkHistoryEditor from './WorkHistoryEditor'
    export default{
        components:{ ProfileEditor,WorkHistoryEditor },
        data(){
            return{
                currentTab: 0,
                icons: ['sfz','bag','book','project','cup','phone'],
                profile: {
                    name: '',
                    age: '',
                    city: '',
                    birth: ''
                },
                workHistory:[
                    {company: '',duration: '',content: ''},
                ]
            }
        },
        methods:{

        },
        created(){

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
        flex: 1;
        .awork{
            position: relative;
            border: 1px solid #d8dce5;
            padding: 16px;
            margin: 8px auto;
            .el-icon-delete{
                position: absolute;
                right: 8px;
                top: 8px;
            }
        }
        > li{
            display: none;
            padding: 32px;
            height: 100%;
            overflow: auto;
            &.active{
                display: block;
            }
        }
    }
}
</style>
