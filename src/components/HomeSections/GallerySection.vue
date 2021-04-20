<template>
  <!-- Sekcja Galerii-->
  <section class="page-section galeria" id="galeria">
    <div class="container">
      <!-- Sekcja Galerii Tytuł-->
      <h2 class="page-section-heading text-center text-uppercase text-secondary mb-0">Galeria</h2>
      <!-- Ikony Podział-->
      <div class="divider-custom">
        <div class="divider-custom-line"></div>
        <div class="divider-custom-icon"><i class="fas fa-star"></i></div>
        <div class="divider-custom-line"></div>
      </div>
      <!-- Galeria Siatka-->
      <div class="row">
        <!-- Galeria nr 1-->
        <div class="col-md-6 col-lg-4 mb-5">
          <div class="galeria-item mx-auto" data-toggle="modal" data-target="#galeriaModal1">
            <div class="galeria-item-caption d-flex align-items-center justify-content-center h-100 w-100">
              <div class="galeria-item-caption-content text-center text-white"><i class="fas fa-plus fa-3x"></i></div>
            </div>
            <img class="img-fluid" src="../../assets/galeria/dolar.png" alt="Minaturka- Ekran Start" />
          </div>
        </div>
        <!-- Galeria nr 2-->
        <div class="col-md-6 col-lg-4 mb-5">
          <div class="galeria-item mx-auto" data-toggle="modal" data-target="#galeriaModal2">
            <div class="galeria-item-caption d-flex align-items-center justify-content-center h-100 w-100">
              <div class="galeria-item-caption-content text-center text-white"><i class="fas fa-plus fa-3x"></i></div>
            </div>
            <img class="img-fluid" src="../../assets/galeria/euro.png" alt="Minaturka- Ekran Logowania" />
          </div>
        </div>
        <!-- Galeria nr 3-->
        <div class="col-md-6 col-lg-4 mb-5">
          <div class="galeria-item mx-auto" data-toggle="modal" data-target="#galeriaModal3">
            <div class="galeria-item-caption d-flex align-items-center justify-content-center h-100 w-100">
              <div class="galeria-item-caption-content text-center text-white"><i class="fas fa-plus fa-3x"></i></div>
            </div>
            <img class="img-fluid" src="../../assets/galeria/korona.png" alt="Minaturka- Ekran Składników" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'GallerySection',
  components: {},
};
</script>
