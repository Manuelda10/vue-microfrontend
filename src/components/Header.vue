<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <header class="bg-blue-500 flex justify-between sticky">
      <div class="w-[25%]">
        <a href="http://localhost:9000">
          <div class="flex items-center w-20">
            <img src='../assets/logo.png' class="w-20" alt="Logo"/>
            <p class="text-sm text-white font-medium" >SISTEMA DE GESTIÓN DOCUMENTAL</p>
          </div>
        </a>
        
      </div>
      <nav class="w-[50%] flex justify-center items-center">
        <ul class="w-[100%] flex justify-around text-gray-100  font-medium">
          <li class="hover:text-white"><a href="http://localhost:9000/reportes">Reportes</a></li>
          <li class="hover:text-white"><a href="http://localhost:9000/documentos" >Documentos</a></li>
          <li class="hover:text-white">Análisis de información</li>
          <li class="hover:text-white"><a href="http://localhost:9000/seguimiento">Seguimiento de pagos</a> </li>
        </ul>
      </nav>
      <div class="flex justify-end items-center w-[25%]">
        <button class="box-border bg-transparent border-solid border-2 border-white text-white rounded-md px-3 py-1 font-medium hover:bg-white hover:text-blue-500 ease-in duration-200 mx-2">Notificaciones</button>
      </div>
    </header>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Header',
  props: {
  }
}
</script>