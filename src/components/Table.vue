<template>
  <div class="card border-primary">
    <div class="card-body">
      <h5 class="card-title"></h5>
      <table id="table-users" class="table table-striped table-bordered" style="width:100%"></table>
    </div>
  </div>
</template>

<script>
import $ from "jquery";
export default {
  name: "Table",
  data() {
    return {
      dataTable: null
    };
  },
  mounted: function() {
    $(document).ready(function($) {
      this.dataTable = $("#table-users").DataTable({
        responsive: true,
        processing: true,
        scrollX: true,
        scrollY: '200',
        dom:
          "<'row'<'col-sm-12 col-md-6'f>>" +
          "<'row'<'col-sm-12'tr>>" +
          "<'row'<'col-sm-12 col-md-5'i><'col-sm-12 col-md-7'p>>",
        ajax: "https://reqres.in/api/users",
        columns: [
          { title: "Correo", data: "email", name: "email" },
          { title: "Nombre", data: "first_name", name: "first_name" },
          { title: "Apellido", data: "last_name", name: "last_name" },
          { title: "Avatar", data: "avatar", name: "avatar" }
        ],
        columnDefs: [
          {
            targets: 3,
            render: function(data, type, row) {
              return `<img src="${data}" class="img-fluid" alt="image">`;
            }
          }
        ],
        language: {
          sProcessing: "Procesando...",
          sLengthMenu: "Mostrar _MENU_ registros",
          sZeroRecords: "No se encontraron resultados",
          sEmptyTable: "Ningún dato disponible en esta tabla",
          sInfo:
            "Mostrando registros del _START_ al _END_ de un total de _TOTAL_ registros",
          sInfoEmpty:
            "Mostrando registros del 0 al 0 de un total de 0 registros",
          sInfoFiltered: "(filtrado de un total de _MAX_ registros)",
          sInfoPostFix: "",
          sSearch: "Buscar:",
          sUrl: "",
          sInfoThousands: ",",
          sLoadingRecords: "Cargando...",
          oPaginate: {
            sFirst: "Primero",
            sLast: "Último",
            sNext: "Siguiente",
            sPrevious: "Anterior"
          },
          oAria: {
            sSortAscending:
              ": Activar para ordenar la columna de manera ascendente",
            sSortDescending:
              ": Activar para ordenar la columna de manera descendente"
          }
        }
      });
    });
  }
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/style.scss";
</style>

