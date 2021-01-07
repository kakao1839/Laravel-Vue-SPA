<template>
    <div class="container">
        <table class="table table-hover">
            <thead class="thead-light">
            <tr>
                <th scope="col">#</th>
                <th scope="col">タイトル</th>
                <th scope="col">内容</th>
                <th scope="col">やる人</th>
                <th scope="col">見る</th>
                <th scope="col">編集</th>
                <th scope="col">削除</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="task in tasks">
                <th scope="row">{{ task.id }}</th>
                <td>{{ task.title }}</td>
                <td>{{ task.content }}</td>
                <td>{{ task.person_in_charge }}</td>
                <td>
                    <router-link v-bind:to="{name: 'task.show', params: {taskId: task.id}}">
                        <button class="btn btn-primary">見る</button>
                    </router-link>
                </td>
                <td>
                    <router-link v-bind:to="{name: 'task.edit', params: {taskId: task.id}}">
                        <button class="btn btn-success">編集</button>
                    </router-link>
                </td>
                <td>
                    <button class="btn btn-danger" v-on:click="deleteTask(task.id)">削除</button>
                </td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    data: function () {
        return {
            tasks: []
        }
    },
    methods: {
        getTasks() {
            axios.get('/api/tasks')
            .then((res) => {
                this.tasks = res.data;
            });
        },
        deleteTask(id) {
            axios.delete('/api/tasks/' + id)
            .then((res) => {
                this.getTasks();
            });
        }
    },
    mounted() {
        this.getTasks();
    }
}
</script>
