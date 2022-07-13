<template>
    <transition name="fade">
        <div class="vue-modal" v-show="toggle">
        <transition name="drop-in">
            <div class="vue-modal-inner" v-show="toggle">
                <div class="vue-modal-content">
                    <slot/>
                    <div class="mb-3">
                    <button type="button" class="btn btn-outline-secondary p-2" @click="$emit('close')">Close</button>
                    <button type="button" class="btn btn-primary p-2 m-2" @click="$emit('save')">Save</button>            
                    </div>
                </div>
            </div>
            </transition>
        </div>
    </transition>
</template>


<script>
export default {
    name: 'ModalComponent',
    props: {
        toggle : {
            type: Boolean,
            required: true
        }
    }
}
</script>


<style scoped>
*,
::before,
::after{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.vue-modal{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    overflow-x: hidden;
    overflow-y: auto;
    background-color: rgba(0, 0, 0, 0.4);
    z-index: 1;
}

.vue-modal-inner{
    max-width:500px;
    margin:2rem auto;    
}

.vue-modal-content{
  position:relative;
  background-color:#fff;
  border:1px solid Orgba(0,0,0,0.3);
  background-clip:padding-box;
  border-radius:0.3em;
  padding:1em;
  }

.fade-enter-active,.fade-leave-active{
    transition:opacity 0.5s;
}
.fade-enter-from,
.fade-leave-to{
    opacity: 0;
}
.drop-in-enter-active,
.drop-in-leave-active{
    transition: all 0.3s;    
}
.drop-in-enter-from,
.drop-in-leave-to{
    opacity: 0;
    transform: translateY(-50px);
}
</style>