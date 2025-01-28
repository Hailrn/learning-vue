<template>
    <div class="main-container flex-row" id="main-container">
        <div class="form-container flex-column" id="form-container">
            <div class="inner-container flex-column" id="inner-container">
                <h1 align="center">To-Do List</h1>
                <form @submit.prevent="createNewTask">
                    <div style="overflow: hidden;" class="form-inner">
                        <div :class="['form-inner', 'flex-column', { hidden: !errorMsg }]" id="form-inner">
                            <span :class="['error-msg', { hide: !errorMsg }]">{{ errorMsg }}</span>
                            <div class="flex-row input-container">
                                <input type="text" class="task-input" id="task-input" v-model="taskTitle">
                                <label for="task-input" :class="['task-label', { valueTrue: taskTitle }]"
                                    id="task-label">Task Title</label>
                            </div>
                            <button type="submit" class="submit-btn btn">Create!</button>
                        </div>
                    </div>
                </form>
            </div>
        </div>
        <div class="task-container flex-column" id="task-container">
            <div class="tasks flex-row" v-for="(task, index) in tasks" :key="index">
                <span>{{ task }}</span>
                <div class="btn-container flex-row">
                    <button class="btn finish-btn">Selesai</button>
                    <button class="btn delete-btn">Hapus</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'SimpleToDoList',
    data() {
        return {
            taskTitle: "",
            errorMsg: "",
            tasks: ["test", "test2"]
        }
    },
    methods: {
        createNewTask() {
            if (this.taskTitle) {
                if (!this.tasks.includes(this.taskTitle)) {
                    this.tasks.push(this.taskTitle)
                    this.errorMsg = ""
                } else {
                    this.errorMsg = "Task Sudah Ada!"
                }
            } else {
                this.errorMsg = "Task Tidak Boleh Kosong!"
            }
        }
    }
}
</script>
<style scoped>
.main-container {
    border: solid 1px black;
    border-radius: 25px;
    width: 800px;
    height: 400px;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

.form-container {
    width: 35%;
    border-right: solid 1px black;
    padding: 0px 50px;
    align-items: center;
    justify-content: center;
}

.inner-container {
    transform: translateY(-20px);
}

.input-container {
    transform: translateX(30px);
    margin-top: 19px;
}

.task-input {
    all: unset;
    border-bottom: 2px solid;
    text-align: left;
    transition: all 0.3s;
}

.task-label {
    transform: translateX(-160px) translateY(-1px);
    cursor: text;
    transition: all 0.6s;
}

.task-input:focus {
    border-color: rgb(85, 85, 255);
}

.task-input:focus+.task-label,
.valueTrue {
    transform: translateX(-160px) translateY(-20px);
    color: rgb(85, 85, 255);
}

.task-container {
    width: 65%;
    height: 100%;
    align-items: center;
    /* justify-content: center; */
}

.tasks {
    align-items: center;
    justify-content: space-between;
    width: 80%;
    height: 50px;
    border: solid 1px black;
    border-radius: 5em;
    margin-top: 20px;
    border-right: none;
}

.tasks span {
    text-align: center;
    width: 60%;
}

.btn-container {
    width: 40%;
    height: 100%;
    align-items: center;
}

.btn {
    all: unset;
    cursor: pointer;
    width: 100px;
    height: 30px;
    border-radius: 10em;
    font-weight: bold;
    position: relative;
    z-index: 2;
    overflow: hidden;
}

.btn::before {
    content: "";
    position: absolute;
    left: 100%;
    top: 50%;
    width: 110px;
    height: 110px;
    border-radius: 50%;
    background-color: rgb(85, 85, 255);
    z-index: -1;
    transition: all 0.7s ease;

}

.submit-btn {
    border: solid 2px rgb(113, 113, 255);
    color: rgb(85, 85, 255);
    transition: all 1.4s ease;
}

.submit-btn:hover {
    color: rgb(251, 240, 240);
}

.submit-btn:hover::before {
    left: -5px;
    top: -40px;
}

.finish-btn {
    border: solid 2px rgb(56, 174, 99);
    border-radius: 0;
    height: 100%;
    color: rgb(56, 174, 99);
    transition: all 0.7s ease;
    font-size: 12px;
    border-right: none;
    /* overflow: visible; */
}

.finish-btn::before{
    left: -5%;
    top: 105%;
    border-radius: 0;
    width: 110%;
    height: 110%;
    background-color: rgb(56, 174, 99);
}

.finish-btn:hover{
    color: rgb(234, 234, 234);
}

.finish-btn:hover::before{
    top: -5%;
}

.delete-btn {
    border: solid 2px rgb(209, 47, 47);
    border-radius: 0 5em 5em 0;
    height: 100%;
    color: rgb(209, 47, 47);
    transition: all 0.7s ease;
    font-size: 12px;
}

.delete-btn::before{
    left: -5%;
    top: 105%;
    border-radius: 0;
    width: 110%;
    height: 110%;
    background-color: rgb(209, 47, 47);
}

.delete-btn:hover{
    color: rgb(234, 234, 234);
}

.delete-btn:hover::before{
    top: -5%;
}

.form-inner {
    height: 128px;
    justify-content: space-around;
    align-items: center;
    transform: translateX(3px) translateY(0px);
    transition: all 0.6s;
}

.flex-row {
    display: flex;
    flex-direction: row;
}

.flex-column {
    display: flex;
    flex-direction: column;
}

.hidden {
    transform: translateX(3px) translateY(-35px);
}

.error-msg {
    color: red;
    transition: 0.6s all;
    height: 19px;
    opacity: 1;
}

.hide {
    opacity: 0;
}
</style>