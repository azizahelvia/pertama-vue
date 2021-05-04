<template>
    <header>
        <h1>{{ title }}</h1>
        <!-- <h2>Ini Latihan Pertama <em>Vue Js</em></h2> -->
        <Button 
        @btn-click="$emit('toggle-add-task')" 
        :text="showAddTask ? 'Tutup' : 'Buat Tugas'"
        :color="showAddTask ? 'red' : '#20bac5'" />
    </header>
</template>

<script>
import Button from './Button'

export default {
    name: 'Header',
    props: //['title'],
    {
        title: String,
        showAddTask: Boolean,
    
        // title: {
        //     type: String,
        //     default: 'Task 1'
        // }
    },

    components: {
        Button
    }
}
</script>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>