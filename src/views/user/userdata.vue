<script setup>
import { ref,onMounted } from 'vue';
import { getUserInfo } from '@/apis/userAPI';

const show = ref(false)

const userinfo = ref({
    email:'',
    phone:""
})
onMounted(async()=>{
    show.value = true
    const res =  await getUserInfo()
    userinfo.value = res.data
})
</script>


<template>
<Transition>
    <div class="center-card" v-if="show">
        <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-youxiang1-copy"></use>
        </svg>
        <span>邮箱</span>
        <div class="center-card-js">
            {{ userinfo.email }}
        </div>
    </div>
</Transition>
<Transition>
    <div class="center-card" v-if="show">
    <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-dianhua-copy"></use>
    </svg>
    <span>电话</span>
    <div class="center-card-js" >
        {{ userinfo.phone }}
    </div>
</div>
</Transition>
<Transition>
    <div class="center-card" v-if="show">
    <svg class="icon" aria-hidden="true">
        <use xlink:href="#icon-xingbie-copy"></use>
    </svg>
    <span>性别</span>
    <div class="center-card-js">
        男
    </div>
</div>
</Transition>


</template>

<style>
.v-enter-active {
  animation: bounce-in 0.6s;
}
.v-leave-active {
  animation: bounce-in 0.6s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}

.center-card {
    position: relative;
    width: 28%;
    height: 25%;
    margin-left: 30px;
    border-radius: 10px;
    background-color: #1d72fc;
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    box-shadow: 0 0 10px 5px #d2d2d2;
    justify-content: center;
    overflow: hidden;
}
.center-card svg {
    font-size: 100px;
}
.center-card span {
    margin-top: 20px;
    font-size: 20px;
    color: #fff;
}
.center-card:nth-child(1) {


}
.center-card:nth-child(2) {

    background-color: #1bb9d9;
}
.center-card:nth-child(3) {

background-color: #b20c88;
}

.center-card-js {
    position: absolute;
    bottom: 0;
    width: 100%;
    height: 20%;
    font-size: 15px;
    background-color: rgba(255, 255, 255, 1);
    transform: translateY(200%);
    transition: all .5s;
    display: flex;
    align-items: center;
    justify-content: center;
}

.center-card:hover .center-card-js {
    transform: translateY(-10px);
    transition: all .5s;
}



</style>