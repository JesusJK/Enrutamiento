<script setup>
import { ref } from "vue";
let qty = ref(1);
function add() {
    console.log("auch!")
    qty.value++
    console.log(qty)
}
function rest() {
    
    if (qty.value > 0) {
        qty.value--
        console.log(qty)
        
    }else{
        console.log("pendejon")
    }
        
    
}


</script>

<template>
    <div class="bg-[#ad1818] rounded max-w-80 mx-auto p-6 flex items-center gap-4 justify-center">
        <div
        v-if="qty > 0" 
        class="bg-red-500 text-white size-8 rounded-full flex justify-center items-center font-bold min-w-9 w-max px-1"
        :class="{'bg-blue-400': qty > 5}">
            {{ qty }}
        </div>
        <p v-else>
            Nadie te visita
        </p>
        <div
        @click="add" 
        class="bg-orange-500 text-white rounded size-6 flex justify-center items-center hover:cursor-pointer">
            +
        </div>
        <div
        @click="rest"
        class="bg-orange-500 text-white rounded size-6 flex justify-center items-center hover:cursor-pointer">
            -
        </div>

    </div>
</template>