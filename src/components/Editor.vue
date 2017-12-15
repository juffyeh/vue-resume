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
                <ArrayEditor v-bind:items="ArrayEditor" v-bind:labels="{company:'公司名称',duration:'起止时间',content:'工作内容'}" title="工作经历"/>
            </li>

            <li v-bind:class="{active: currentTab === 2}">
                <ArrayEditor v-bind:items="studyHistory" v-bind:labels="{school:'学校名称',time: '起止时间',major: '专业',degree:'学位'}" title="学习经历"/>
            </li>
            <li v-bind:class="{active: currentTab === 3}">
                <ArrayEditor v-bind:items="projects" v-bind:labels="{name:'项目名称',content:'项目内容'}" title="项目经历"/>
            </li>
            <li v-bind:class="{active: currentTab === 4}">
                <ArrayEditor v-bind:items="awards" v-bind:labels="{name:'奖励详情'}" title="获奖情况"/>
            </li>
            <li v-bind:class="{active: currentTab === 5}">
                <h2>联系方式</h2>
                <el-form>
                    <el-form-item label="QQ">
                        <el-input v-model="contacts.qq"></el-input>
                    </el-form-item>
                    <el-form-item label="微信">
                        <el-input v-model="contacts.wechat"></el-input>
                    </el-form-item>
                    <el-form-item label="邮箱">
                        <el-input v-model="contacts.email"></el-input>
                    </el-form-item>
                    <el-form-item label="手机">
                        <el-input v-model="contacts.phone"></el-input>
                    </el-form-item>
                </el-form>
            </li>
        </ol>
    </div>
</template>
<script>
    import ProfileEditor from './ProfileEditor'
    import ArrayEditor from './ArrayEditor'
    export default{
        components:{ ProfileEditor,ArrayEditor},
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
                ArrayEditor:[
                    {company: '',duration: '',content: '',}
                ],
                studyHistory:[
                    {school: '',time: '',major: '',degree: ''}
                ],
                projects:[
                    {name: '',content: ''}
                ],
                awards:[
                    {name: ''}
                ],
                contacts:[
                    {qq: '',wechat: '',emali: '',phone: ''}
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
        .container{
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
