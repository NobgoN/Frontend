<script>
    export default {
        props: {
            isVisible: {
                required: true,
                type: Boolean,
                default: false,
            }
        },
        data () {
            return {

            }
        },
        methods: {
            close() {
                this.$emit('close')
            }

            
        }

        
    }
    
</script>

<template>
    <teleport to="body">
        <div class="modal" id="modal" v-show="isVisible" @click="close"></div>
        <div class="modal-content" v-show="isVisible">投稿画面</div>
    </teleport>
</template>

<style scoped lang="scss">

.modal {
    position: fixed;
    top:0;
    right: 0;
    left: 0;
    bottom: 0;
    background-color: rgba(0,0,0,0.5);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.modal-content {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: rgba(0,0,0,0.5);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: white;
    width: 600px;
    height: auto;
    border-radius: 20px;
    padding: 20px;
}
</style>