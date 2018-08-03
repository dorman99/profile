<template>
    <div>
        <app-tool-bar></app-tool-bar>
        <app-body></app-body>
    </div>
</template>

<script>
import AppToolBar from './ToolBar.vue'
import AppBody  from './AppBody.vue'

export default {
    components: {AppToolBar,AppBody}
}
</script>

<style>

</style>
