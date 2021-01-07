<template>
    <div class="container-fluid bg-dark mb-3">
        <div class="container">
            <nav class="navbar navbar-dark">
                <router-link v-bind:to="{name: 'task.list'}">
                    <span class="navbar-brand mb-0 h1">Laravel+Vue+SPAの練習</span>
                </router-link>
                <div>
                    <router-link v-bind:to="{name: 'task.list'}">
                        <button class="btn btn-success">一覧</button>
                    </router-link>
                    <router-link v-bind:to="{name: 'task.create'}">
                    <button class="btn btn-success">追加</button>
                    </router-link>
                </div>
            </nav>
        </div>
    </div>
</template>

<script>
export default {}
</script>
