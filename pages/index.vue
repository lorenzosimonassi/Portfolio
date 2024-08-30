<script setup>

import { ref, onMounted } from 'vue';

const icon = ref('moon');

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
          <img class="size-20" src="/logo.png" alt="logo">
          <h1 class="text-xl font-bold tracking-wide dark:text-white" >Lorenzo Simonassi</h1>
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
    <!--Foto-->
    <div class="flex w-1/2 justify-end mr-24">
      <img class="h-96 rounded-lg mt-44 shadow-2xl shadow-slate-800 transition-transform duration-200 scale-[1.20] dark:shadow-lg dark:shadow-blue-900/50" src="/eu.png" alt="eu" srcset="">
    </div>
    
    
    <!--Texto-->
    <div class="flex w-1/2 items-center justify-start">
      <div id="text-box" class="w-2/4 mt-[30px] text-left items-center" >
        <h1 class="text-4xl font-bold tracking-wide dark:text-white">Lorenzo Moura</h1>
        <h2 class="text-2xl mt-4 font-bold dark:text-white">Um Pouco Sobre Mim</h2>
        <p class="mt-4 dark:text-neutral-200">Sou estudante de Ciência da Computação, com interesse em desenvolvimento front-end. Tenho habilidades em HTML, CSS e JavaScript, e gosto de criar interfaces de usuário intuitivas e agradáveis. Possuo nível intermediário de inglês, e estou sempre em busca de novos desafios e oportunidades para crescer na área.</p>
        <div id="btns" class="flex flex-wrap w-96 h-54 items-start mt-4 gap-x-4 gap-y-2"> 
          <button class="h-10 w-20 rounded-3xl bg-[#3EC052] text-white font-bold transition-transform duration-200 hover:scale-[1.20] dark:shadow-lg dark:shadow-green-500/50">Css</button>
          <button class="h-10 w-24 rounded-3xl bg-[#3EA0C0] text-white font-bold transition-transform duration-200 hover:scale-[1.20] dark:shadow-lg dark:shadow-sky-500/50">Html</button>
          <button class="h-10 w-32 rounded-3xl bg-[#8871A5] text-white font-bold transition-transform duration-200 hover:scale-[1.20] dark:shadow-lg dark:shadow-purple-500/50">Javascript</button>
          <button class="h-10 w-16 rounded-3xl bg-[#AB4141] text-white font-bold transition-transform duration-200 hover:scale-[1.20] dark:shadow-lg dark:shadow-red-500/50">C</button>
          <button class="h-10 w-36 rounded-3xl bg-[#294380] text-white font-bold transition-transform duration-200 hover:scale-[1.20] dark:shadow-lg dark:shadow-blue-800/50">Métodos Ágeis</button>
          <button class="h-10 w-24 rounded-3xl bg-[#DB8827] text-white font-bold transition-transform duration-200 hover:scale-[1.20] dark:shadow-lg dark:shadow-yellow-500/50">Java</button>
          <button class="h-10 w-24 rounded-3xl bg-[#29807B] text-white font-bold transition-transform duration-200 hover:scale-[1.20] dark:shadow-lg dark:shadow-teal-500/50">Ui/Ux</button>
        </div>
      </div>
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


