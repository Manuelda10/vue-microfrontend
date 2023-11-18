<!-- eslint-disable vue/no-parsing-error -->
<template>
  <Header/>
  <div className="flex justify-center items-center">
          <div className="w-[80%] my-12">
            <h1 className="font-semibold text-2xl">SEGUIMIENTO</h1>
            <p className="mt-2">Información de los departamentos con deudas pendientes de pago</p>
            <div className='bg-gray-200 py-2 my-4 flex'>
              <input type='search' placeholder='Nombre o apellidos' className='border-solid border-2 border-gray-300 px-3 py-[5px] rounded-sm outline-none focus:border-blue-500 mx-2 '/>
              <button className='rounded-md px-4 bg-white text-gray-600 mx-2 hover:text-gray-900 ease-in duration-200'>
                Filtrar
              </button>
            </div>
            <div className='py-2 my-4'>
            <table className='w-[100%]'>
              <thead className='text-left text-gray-500 border-b-2 border-gray-300'>
                <tr>
                  <th>Departamento</th>
                  <th>Servicio</th>
                  <th>Fecha de pago</th>
                  <th>Estado</th>
                  <th>Cantidad</th>
                </tr>
              </thead>
              <tbody className='text-left'>
              </tbody>
            </table>
            </div>
          </div>
        </div>
</template>

<script>
import Header from './components/Header.vue'
import './assets/tailwind.css';

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>
