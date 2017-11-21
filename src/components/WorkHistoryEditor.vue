<template>
    <div>
        <h2>工作经历</h2>
        <el-form>
            <div class="awork" v-for="(work,index) in workHistory">
                <el-form-item label="公司名称">
                    <el-input v-model="work.name"></el-input>
                </el-form-item>
                <el-form-item label="起止时间">
                    <el-input v-model="work.duration"></el-input>
                </el-form-item>
                <el-form-item label="工作内容">
                    <el-input v-model="work.city"></el-input>
                </el-form-item>
                <i class="el-icon-delete" v-on:click="removeWorkHistory(index)"></i>
            </div>
            <el-button type="primary" v-on:click="addWorkHistory">添加</el-button>
        </el-form>
    </div>
</template>
<script>
    export default {
        props: ['workHistory'],
        methods:{
            addWorkHistory(){
                this.workHistory.push({
                    company: '',duration: '',content: ''
                })
            },
            removeWorkHistory(index){
                this.workHistory.splice(index,1)
            }
        }
    }
</script>