<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-sm-6">
                <form v-on:submit.prevent="submit">
                    <div class="form-group row">
                        <labael for="title" class="col-sm-3 col-form-label">タイトル</labael>
                        <input type="text" class="col-sm-9 form-control" id="title" v-model="task.title">
                    </div>
                    <div class="form-group row">
                        <label for="content" class="col-sm-3 col-form-label">内容</label>
                        <input type="text" class="col-sm-9 form-control" id="content" v-model="task.content">
                    </div>
                    <div class="form-group row">
                        <label for="person-in-charge" class="col-sm-3 col-form-label">やる人</label>
                        <input type="text" class="col-sm-9 form-control" id="person-in-charge" v-model="task.person_in_charge">
                    </div>
                    <button type="submit" class="btn btn-primary">Submit</button>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data: function () {
        return {
            task: {}
        }
    },
    methods: {
        submit() {
            axios.post('/api/tasks', this.task)
            .then((res) => {
                this.$router.push({name: 'task.list'});
            });
        }
    }
}
</script>
