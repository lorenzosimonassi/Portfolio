<script setup>

import { ref, onMounted } from 'vue';

const icon = ref('moon');
const modals = ref({
  modal1: false,  // Controle do primeiro modal
  modal2: false,  // Controle do segundo modal
});

function updateIcon() {
  icon.value = document.documentElement.classList.contains('dark') ? 'sun' : 'moon';
}

function toggleDark() {
  const currentTheme = localStorage.theme;
  
  if (currentTheme === 'dark') {
    document.documentElement.classList.remove('dark');
    localStorage.theme = 'light';
  } else {
    document.documentElement.classList.add('dark');
    localStorage.theme = 'dark';
  }
  updateIcon();
}

function openModal(modalName) {
  modals.value[modalName] = true;
}

function closeModal(modalName) {
  modals.value[modalName] = false;
}


onMounted(() => {
  updateIcon();
});

</script>



<template>
  <div class="">
  <section id="main" class="flex w-full h-screen bg-fundo flex-col dark:bg-slate-800">
    <!--Navegação-->
    <nav class="flex flex-wrap w-full h-24 bg-fundo items-center justify-between dark:bg-slate-800"> 
        <div id="logo" class="flex flex-wrap ml-28 items-center justify-center">
            <NuxtLink to="/"><img class="size-20" src="/logo2.png" alt="logo"></NuxtLink>
          <NuxtLink to="/"> <h1 class="text-xl font-bold tracking-wide dark:text-white" >Lorenzo Simonassi</h1></NuxtLink>
          <h1 class="ml-12 dark:text-white" >Desenvolvedor Web</h1>
        </div>

        <div id="btns" class="mr-32 mt-4 space-x-20">
          <button @click="toggleDark()" class="h-10 w-10 rounded-full bg-neutral-200 transition duration-300 dark:bg-slate-700 items-center justify-center text-center flex absolute dark:text-white fixed">
            <svg v-if="icon === 'moon'" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M21.752 15.002A9.72 9.72 0 0 1 18 15.75c-5.385 0-9.75-4.365-9.75-9.75 0-1.33.266-2.597.748-3.752A9.753 9.753 0 0 0 3 11.25C3 16.635 7.365 21 12.75 21a9.753 9.753 0 0 0 9.002-5.998Z" />
            </svg>
            <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 3v2.25m6.364.386-1.591 1.591M21 12h-2.25m-.386 6.364-1.591-1.591M12 18.75V21m-4.773-4.227-1.591 1.591M5.25 12H3m4.227-4.773L5.636 5.636M15.75 12a3.75 3.75 0 1 1-7.5 0 3.75 3.75 0 0 1 7.5 0Z" />
            </svg>

          </button>
          <NuxtLink to="/meusprojetos"><button class="h-10 w-36 rounded-3xl border border-black font-bold transition-transform duration-200 hover:scale-[1.20] hover:bg-black hover:text-white dark:text-white dark:border-white dark:bg-inherit">Meus Projetos</button></NuxtLink>
          <NuxtLink to="/habilidades"><button class="h-10 w-36 rounded-3xl border border-black font-bold transition-transform duration-200 hover:scale-[1.20] hover:bg-black hover:text-white dark:text-white dark:border-white dark:bg-inherit"><a href=""></a>Habilidades</button></NuxtLink>
        </div>
    </nav>

    <!--Principal-->
    <div class="flex w-full h-[80vh] mb-4">
        
        <div class="justify-center text-start mt-4 grid grid-cols-4 gap-8 p-4 w-full mr-12 ml-12">
        <!-- Card com imagem -->
        <div  @click="openModal('modal1')" class="bg-gray-200  rounded-xl h-[300px] flex items-center justify-center flex-col transition-transform duration-200 hover:scale-[1.10] cursor-pointer dark:bg-gray-900">
            <img class="h-full w-full object-cover rounded-xl p-4" src="/projeto1.png" alt="">
            <div class="h-[40px] w-full bg-slate-400 dark:bg-green-600 rounded-b-lg font-semibold items-center flex dark:shadow-lg dark:shadow-green-500/50 dark:text-white"><h1 class="ml-4">Projeto 1 - Website Para Um Dentista</h1></div>
        </div>

       <!-- Modal (Janelinha) -->
       <div v-if="modals.modal1" class="fixed inset-0 bg-black bg-opacity-50 flex justify-center items-center">
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 w-[90%] h-[380px] max-w-xl">
                    <h2 class="text-2xl font-bold mb-4 dark:text-white">Detalhes do Site Dentista</h2>
                    <p class="mb-4 dark:text-gray-300">Criei um website moderno para um dentista, utilizando as tecnologias HTML, CSS e JavaScript. Para o design e estilização, utilizei Tailwind CSS, permitindo a criação de uma interface limpa e profissional, com uma experiência de usuário intuitiva. O site foi desenvolvido em Vue.js, o que facilitou a implementação de componentes reativos e interativos, como agendamento online.</p>
                  <p class="mt-8 dark:text-white">Acesse ele aqui: <a class="underline-offset-2 underline decoration-sky-500" href="" target="_blank">drnorivaltonini.com</a></p>
                    <button class="bg-red-500 mt-8 text-white px-4 py-2 rounded-lg hover:bg-red-600 dark:shadow-lg dark:shadow-red-500/50" @click="closeModal('modal1')">Fechar</button>
                </div>
            </div>

        <!-- Outros cards -->
        <div @click="openModal('modal2')"  class="bg-gray-200  rounded-xl h-[300px] flex items-center justify-end flex-col transition-transform duration-200 hover:scale-[1.10] cursor-pointer dark:bg-gray-900">
            <img class="h-full w-full object-cover bg-cover rounded-xl p-4" src="/portimage.png" alt="">
            <div class="h-[40px] w-full bg-slate-400 dark:bg-green-600  rounded-b-lg font-semibold items-center flex dark:shadow-lg dark:shadow-green-500/50 dark:text-white"><h1 class="ml-4">Projeto 2 - Meu portfolio</h1></div>
        </div>

        <!-- Modal (Janelinha) -->
        <div v-if="modals.modal2" class="fixed inset-0 bg-black bg-opacity-50 flex justify-center items-center">
                <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-6 w-[90%] h-[350px] max-w-xl">
                    <h2 class="text-2xl font-bold mb-4 dark:text-white">Detalhes do Meu Portfolio</h2>
                    <p class="mb-4 dark:text-gray-300">Para criar meu portfólio web, utilizei uma combinação de tecnologias modernas, incluindo HTML, CSS, JavaScript, Tailwind CSS e Vue.js. O objetivo principal era desenvolver um site que não apenas demonstrasse minhas habilidades técnicas, mas também refletisse a minha identidade como desenvolvedor, com um design limpo e interativo.</p>
                  <p class="mt-8 dark:text-white">Acesse ele aqui: <a class="underline-offset-2 underline decoration-sky-500" href="https://portfolio-1ud.pages.dev/" target="_blank"> https://portfolio-1ud.pages.dev/</a></p>
                    <button class="bg-red-500 mt-8 text-white px-4 py-2 rounded-lg hover:bg-red-600 dark:shadow-lg dark:shadow-red-500/50" @click="closeModal('modal2')">Fechar</button>
                </div>
            </div>


        <div class="bg-gray-200 p-4 rounded-xl h-[300px] justify-center flex items-center text-center transition-transform duration-200 hover:scale-[1.10] cursor-pointer dark:bg-gray-900 dark:text-white">Indisponível</div>
        <div class="bg-gray-200 p-4 rounded-xl h-[300px] justify-center flex items-center text-center transition-transform duration-200 hover:scale-[1.10] cursor-pointer dark:bg-gray-900 dark:text-white">Indisponível</div>
        <div class="bg-gray-200 p-4 rounded-xl h-[300px] justify-center flex items-center text-center transition-transform duration-200 hover:scale-[1.10] cursor-pointer dark:bg-gray-900 dark:text-white">Indisponível</div>
        <div class="bg-gray-200 p-4 rounded-xl h-[300px] justify-center flex items-center text-center transition-transform duration-200 hover:scale-[1.10] cursor-pointer dark:bg-gray-900 dark:text-white">Indisponível</div>
        <div class="bg-gray-200 p-4 rounded-xl h-[300px] justify-center flex items-center text-center transition-transform duration-200 hover:scale-[1.10] cursor-pointer dark:bg-gray-900 dark:text-white">Indisponível</div>
        <div class="bg-gray-200 p-4 rounded-xl h-[300px] justify-center flex items-center text-center transition-transform duration-200 hover:scale-[1.10] cursor-pointer dark:bg-gray-900 dark:text-white">Indisponível</div>
    </div>

    </div>

    <!-- Footer -->
    <div id="footer" class="flex flex-col items-center w-full">
      <!-- Linha Cinza -->
      <div class="w-[95%] h-[1px] bg-gray-400 mb-12"></div>

      <!-- Conteúdo do Footer -->
      <div class="flex flex-wrap justify-between w-[95%] text-center mb-12">
        <!-- Email -->
        <div class="flex flex-col items-start">
          <h1 class="text-lg font-bold dark:text-neutral-200">Email</h1>
          <p class="text-md dark:text-neutral-200">lorenzosimonassimoura@gmail.com</p>
        </div>
        <!-- Github -->
        <div class="flex flex-col items-start">
          <h1 class="text-lg font-bold dark:text-neutral-200">Github</h1>
          <p class="text-md dark:text-neutral-200"><a href="https://github.com/lorenzosimonassi" target="_blank" class=" hover:underline hover:underline-offset-2 hover:decoration-fuchsia-500">github.com/lorenzosimonassi</a></p>
        </div>
        <!-- Celular -->
        <div class="flex flex-col items-start">
          <h1 class="text-lg font-bold dark:text-neutral-200">Celular</h1>
          <p class="text-md dark:text-neutral-200">(27) 99871-2510</p>
        </div>
        <!-- Copyright -->
        <div class="flex items-start gap-x-2 mt-4">
          <h1 class="text-md dark:text-neutral-200">© 2024</h1>
          <p class="text-md dark:text-neutral-200">by Lorenzo Simonassi</p>
        </div>
      </div>
    </div>
 




  </section>
</div>
</template>




