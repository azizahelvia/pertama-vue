<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Tugas</label>
            <input 
            type="text" 
            v-model="notes"
            name="notes"
            placeholder="Tambah Tugas">
        </div>
        <div class="form-control">
            <label>Hari & Waktu</label>
            <input 
            type="text" 
            v-model="time"
            name="time"
            placeholder="Tambah Hari & Waktu">
        </div>
        <div class="form-control form-control-check">
            <label>Atur Pengingat</label>
            <input 
            type="checkbox" 
            v-model="reminder"
            name="reminder" >
        </div>

        <input type="submit" value="Simpan Tugas" class="btn btn-block">
    </form>
</template>

<script>
export default {
    name: 'AddTask',
    data() {
        return {
            notes: '',
            time: '',
            reminder: false
        }
    },

    methods: {
        onSubmit(e) {
            e.preventDefault()

            if(!this.notes) {
                alert('Diisi ya tugasnya')
                return
            }

            const newTask = {
                id: Math.floor(Math.random() * 100000),
                notes: this.notes,
                time: this.time,
                reminder: this.reminder,
            }

            // console.log(newTask);
            this.$emit('add-task', newTask)

            this.notes = ''
            this.time = ''
            this.reminder = false
        }
    }
}
</script>

<style scoped>
.add-form {
    margin-bottom: 40px;
}

.form-control {
    margin: 20px 0;
}

.form-control label {
    display: block;
}

.form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}

.form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.form-control-check label {
    flex: 1;
}

.form-control-check input {
    flex: 2;
    height: 20px;
}
</style>