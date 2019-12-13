<template>
    <div class="container">
        
        <app-header></app-header>
        <div class="row">
            <div class="col-xs-12">
                <transition name="slide" mode="out-in">
                   
                    <router-view></router-view>
                </transition>
            </div>
        </div>
    </div>
</template>

<script>
import Header from './components/Header.vue'
    

    export default {
        components: {
        appHeader: Header
        },
        
        created() {
            this.$store.dispatch('initStocks')
        }
        
    }
</script>

<style>
    body {
        padding: 30px;
    }

.slide-enter-active {
    animation: slide-in 2s ease-out forwards;
}
.slide-leave-active {
    transition: opacity 2s ease;
    opacity: 0;
    animation: slide-in 1s ease-out forwards;
}

.slide-leave {
    opacity: 1;
    transform: translateX(0);
}
   
@keyframes slide-in {
    from {
        transform: translateY(0);
        opacity: 0;
        transform: scale(1.1);
        
    }
    to {
        transform: translateY(-45px);
        opacity: 1;
        transform: scale(1);
        
    }
}

@keyframes slide-out {
    from {
        transform: translateY(-45px);
        opacity: 1;
        transform: scale(1); 
    }
     to {
        transform: translateY(0);
        opacity: 0;
        transform: scale(1.1); 
     }
}
</style>

