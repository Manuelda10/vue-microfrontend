<!-- eslint-disable vue/require-v-for-key -->
<!-- eslint-disable vue/no-parsing-error -->
<template>
  <Header/>
  <div className="flex justify-center items-center">
          <div className="w-[80%] my-12">
            <h1 className="font-semibold text-2xl">SEGUIMIENTO</h1>
            <p className="mt-2">Información de los departamentos con deudas pendientes de pago</p>
            <div className='bg-gray-200 py-2 my-4 flex'>
              <input v-model="search_department"  type='search' placeholder='Departamento' className='border-solid border-2 border-gray-300 px-3 py-[5px] rounded-sm outline-none focus:border-blue-500 mx-2 '/>
              <button className='rounded-md px-4 bg-white text-gray-600 mx-2 hover:text-gray-900 ease-in duration-200' @click="filterByDepartment" >
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
                <div v-if="loading">Cargando...</div>
                <div v-if="error">Error: {{ error.message }}</div>
                <tr v-for="document in listDocuments" v-show="data" class="border-b-2 border-gray-300">
                  <td class="max-w-[140px]">{{document.departamento}}</td>
                  <td class="max-w-[140px]">{{document.tipo_de_servicio}}</td>
                  <td class="max-w-[140px]">{{document.fecha_de_pago}}</td>
                  <td class="flex">
                    <span className="border rounded-md bg-green-50 text-green-600 font-medium p-1">
                      Aceptado
                    </span>
                  </td>
                  <td class="max-w-[140px]">$500</td>
                </tr>
              </tbody>
            </table>
            </div>
          </div>
        </div>
</template>

<script>
import Header from './components/Header.vue'
import {gql} from '@apollo/client/core'
import apolloClient from '@/apollo-client'

import './assets/tailwind.css';

export default {
  name: 'App',
  components: {
    Header
  },

  data() {
    return {
      listDocuments: [],
      loading: false,
      error: null,
      data: false,
      search_department: ''
    }
  },

  mounted() {
    this.getDocuments()
  },

  methods: {
    async getDocuments() {
      this.loading = true
      try {
        const {data} = await apolloClient.query({
          query: gql`
          query MyQuery{
            GetAll {
              id_documento
              departamento
              residente
              fecha_de_pago
              tipo_de_servicio
              url_pdf
            }
          }
          `
        })
        console.log(data)
        this.listDocuments = data.GetAll
        this.loading = false
        this.data = true
      } catch (error) {
        this.loading = false
        this.error = error
      }
    },

    filterByDepartment() {
      if(this.search_department == '') {
        this.getDocuments()
        return
      }

      const filteredDocuments = this.listDocuments.filter(document => document.departamento == this.search_department)

      this.listDocuments = filteredDocuments
    }
  },

}
</script>
