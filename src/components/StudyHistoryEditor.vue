<template>
    <div>
        <h2>学习经历</h2>
        <el-form>
            <div class="container" v-for="(study,index) in studyHistory">
                <el-form-item label="学校名称">
                    <el-input v-model="study.school"></el-input>
                </el-form-item>
                <el-form-item label="起止时间">
                    <el-input v-model="study.time"></el-input>
                </el-form-item>
                <el-form-item label="所学专业">
                    <el-input v-model="study.degree"></el-input>
                </el-form-item>
                <i class="el-icon-delete" v-on:click="removestudyHistory(index)"></i>
            </div>
            <el-button type="primary" v-on:click="addstudyHistory">添加一项</el-button>
        </el-form>
    </div>
</template>
<script>
    export default {
        props: ['studyHistory'],
        methods:{
            addstudyHistory(){
                this.studyHistory.push({
                    school: '',time: '',degree: ''
                })
            },
            removestudyHistory(index){
                this.studyHistory.splice(index,1)
            }
        }
    }
</script>