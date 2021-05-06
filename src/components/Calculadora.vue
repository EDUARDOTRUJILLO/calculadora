<template>
<div class="h-screen bg-gray-200 flex justify-center py-16">
    <div class="w-11/12">
        <div class="p-4 text-right shadow-2xl rounded-t-lg bg-gray-800">
            <p class="font-semibold text-gray-500 h-6">{{getOperacion}}</p>
            <p class="font-bold text-3xl text-white my-4">{{getResultado}}</p>
        </div>
        <div class="grid grid-cols-4 grid-rows-5 shadow-xl rounded-b-lg ">
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700 col-span-2" @click="clickAC()">AC</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="clickDEL()">DEL</button>
            <!-- <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('%')">%</button> -->
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('÷')">÷</button>

            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('7')">7</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('8')">8</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('9')">9</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('x')">x</button>

            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('4')">4</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('5')">5</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('6')">6</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('-')">-</button>

            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('1')">1</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('2')">2</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('3')">3</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('+')">+</button>

            <button class="h-16 text-xl text-white font-semibold bg-gray-600 col-span-2 border-gray-800 hover:bg-gray-700 rounded-bl-lg"  @click="click('0')">0</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700" @click="click('.')">.</button>
            <button class="h-16 text-xl text-white font-semibold bg-gray-600 border-gray-800 hover:bg-gray-700 rounded-br-lg"  @click="clickResultado()">=</button>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'Calculadora',
    data(){
        return{
            getOperacion: '',
            getResultado: '0',
        }
    },
    methods:{
        clickAC(){
            this.getResultado = '0';
        },
        clickDEL(){
            if(this.getResultado.length > 1){
                this.getResultado = this.getResultado.substring(0,this.getResultado.length - 1);
            }else{
                this.getResultado = '0';
            }
        },
        click(num){
            if(this.getResultado === '0'){
                this.getResultado = num;
            }else{
                this.getResultado += num;
            }
        },
        clickResultado(){
            let operacion = this.getResultado;
            this.getOperacion = operacion;

            operacion = operacion.replace('x', '*');
            operacion = operacion.replace('÷', '/');
            this.getResultado = eval(operacion);
        }
    }
}
</script>

<style scoped>
button{
    @apply border-2 focus:outline-none hover:bg-green-300;
}

</style>