<template>
    <div id="preview">
        <h1>{{resume.profile.name}}</h1>
        <p>{{resume.profile.city}} | {{resume.profile.birth}}</p>
        <hr>
        <section v-if="resume.workHistory.length > 0">
            <h2>工作经历</h2>
            <ul>
                <li v-for="work in filter(resume.workHistory)">
                    {{work.company}}
                    {{work.duration}}
                    {{work.content}}
                </li>
            </ul>
        </section>
        <section v-if="resume.projects.length > 0">
            <h2>项目</h2>
            <ul>
                <li v-for="project in filter(resume.projects)">
                    {{project.name}}
                    {{project.content}}
                </li>
            </ul>
        </section>
    </div>
</template>
<style>
#preview{

    min-height: 100px;
}
</style>
<script>
    export default {
        props:['resume'],
        methods: {
            filter(array){
                return array.filter(item=> !this.isEmpty(item))
            },
            isEmpty(object){
                let empty = true
                for(let key in object){
                    if(object[key]){
                        empty = false
                        break
                    }
                }
                return empty
            }
        }
    }
</script>
