<template>
    <div>
        Frank
    </div>
</template>
<script lang="ts">
import {Component, Vue} from 'vue-property-decorator';
import HelloWorld from './HelloWrod.vue'

@Component({
    components: {
        HelloWorld
    }
})
export default class Frank extends Vue{

}
</script>