<script setup>
import { onUpdated, ref } from 'vue';
const isClose = ref(true)
</script>
<template>
    <div class="wrapper-popup" :class="{ 'open-popup': isClose }">
        <div class="rule">
            <h3>Luật chơi</h3>
            <h2 style =" color :aqua ">Tìm người đạt điểm nhanh nhất</h2>
            <p>Nhấn nút roll dice để xoay cho đến khi bạn muốn giữ điểm hãy nhấn nút Hold. <br> Cẩn thận, đừng quá tham lam bạn sẽ mất lượt nếu roll trúng số 1.</p><br><h3 style = "color :aqua">Chúc bạn may mắn</h3>
            <button class="confirm" @click=" isClose = !isClose ">Đã hiểu</button>
        </div>
    </div>
</template>



<style >
.wrapper-popup {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.4);
    opacity: 0;
    visibility: hidden;
    transition: all .3s ease;
}

.wrapper-popup.open-popup {
    opacity: 1;
    visibility: visible;
}

.rule {
    width: 350px;
    padding: 20px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(1.2);
    background-color: #fff;
    position: absolute;
    font-family: Arial, Helvetica, sans-serif;
    transition: all .3s ease;
    text-align: center;
}

.open-popup .rule {

    transform: translate(-50%, -50%) scale(1);
}

/* scale -> class */
.rule h3 {
    margin-bottom: 10px;
}

.rule .confirm {
    cursor: pointer;
    margin-top: 20px;
    padding: 8px 15px;
    border: 2px solid #333;
    background-color: #fff;
    transition: all .3s ease;
}

.rule .confirm:hover {
    color: #fff;
    background-color: #333;
}
</style>
