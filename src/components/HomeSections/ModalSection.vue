<template
  ><div>
    <!-- Galeria Okna-->
    <!-- Galeria Modal 1-->
    <div class="galeria-modal modal fade" id="galeriaModal1" tabindex="-1" role="dialog" aria-labelledby="galeriaModal1Label" aria-hidden="true">
      <div class="modal-dialog modal-xl" role="document">
        <div class="modal-content">
          <button class="close" type="button" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true"><i class="fas fa-times"></i></span>
          </button>
          <div class="modal-body text-center">
            <div class="container">
              <div class="row justify-content-center">
                <div class="col-lg-8">
                  <!-- Galeria Modal - Tytuł-->
                  <h2 class="galeria-modal-title text-secondary text-uppercase mb-0">Dollar</h2>
                  <!-- Podział Ikon-->
                  <div class="divider-custom">
                    <div class="divider-custom-line"></div>
                    <div class="divider-custom-icon"><i class="fas fa-star"></i></div>
                    <div class="divider-custom-line"></div>
                  </div>
                  <!-- Galeria Modal - Obraz--><img class="img-fluid rounded mb-5" src="../../assets/galeria/dolar.png" alt="Ekran Startu" />
                  <!-- Galeria Modal - Text-->
                  <p class="mb-5">Aktualny kurs Dolara Amerykanskiego(USD)</p>
                  <button class="btn btn-primary" href="#" data-dismiss="modal"><i class="fas fa-times fa-fw"></i>Zamknij</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Galeria Modal 2-->
    <div class="galeria-modal modal fade" id="galeriaModal2" tabindex="-1" role="dialog" aria-labelledby="galeriaModal2Label" aria-hidden="true">
      <div class="modal-dialog modal-xl" role="document">
        <div class="modal-content">
          <button class="close" type="button" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true"><i class="fas fa-times"></i></span>
          </button>
          <div class="modal-body text-center">
            <div class="container">
              <div class="row justify-content-center">
                <div class="col-lg-8">
                  <!-- Galeria Modal - Tytuł-->
                  <h2 class="galeria-modal-title text-secondary text-uppercase mb-0">Euro</h2>
                  <!-- Podział Ikon-->
                  <div class="divider-custom">
                    <div class="divider-custom-line"></div>
                    <div class="divider-custom-icon"><i class="fas fa-star"></i></div>
                    <div class="divider-custom-line"></div>
                  </div>
                  <!-- Galeria Modal - Obraz--><img
                    class="img-fluid rounded mb-5"
                    src="../../assets/galeria/euro.png"
                    alt="Ekran Logowania"
                  /><!-- Galeria Modal - Text-->
                  <p class="mb-5">Aktualny kurs Euro (EUR)</p>
                  <button class="btn btn-primary" href="#" data-dismiss="modal"><i class="fas fa-times fa-fw"></i>Zamknij</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Galeria Modal 3-->
    <div class="galeria-modal modal fade" id="galeriaModal3" tabindex="-1" role="dialog" aria-labelledby="galeriaModal3Label" aria-hidden="true">
      <div class="modal-dialog modal-xl" role="document">
        <div class="modal-content">
          <button class="close" type="button" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true"><i class="fas fa-times"></i></span>
          </button>
          <div class="modal-body text-center">
            <div class="container">
              <div class="row justify-content-center">
                <div class="col-lg-8">
                  <!-- Galeria Modal - Tytuł-->
                  <h2 class="galeria-modal-title text-secondary text-uppercase mb-0">Korona</h2>
                  <!-- Podział Ikon-->
                  <div class="divider-custom">
                    <div class="divider-custom-line"></div>
                    <div class="divider-custom-icon"><i class="fas fa-star"></i></div>
                    <div class="divider-custom-line"></div>
                  </div>
                  <!-- Galeria Modal - Obraz--><img
                    class="img-fluid rounded mb-5"
                    src="../../assets/galeria/korona.png"
                    alt="Ekran Wyboru Składników"
                  /><!-- Galeria Modal - Text-->
                  <p class="mb-5">Aktualny kurs Korony Nowerskiej (NOK)</p>
                  <button class="btn btn-primary" href="#" data-dismiss="modal"><i class="fas fa-times fa-fw"></i>Zamknij</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalSection',
  components: {},
};
</script>
