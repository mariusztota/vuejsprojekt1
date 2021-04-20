<template
  ><!-- Sekcja Promo-->
  <section class="page-section" id="promo">
    <div class="container">
      <!-- Sekcja Promo tytuł-->
      <h2 class="page-section-heading text-center text-uppercase text-secondary mb-0"></h2>
      <!-- Podział ikon-->
      <div class="divider-custom">
        <div class="divider-custom-line"></div>
        <div class="divider-custom-icon"><i class="fas fa-star"></i></div>
        <div class="divider-custom-line"></div>
      </div>
      <!-- Carousel-->
      <div class="container">
        <div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
          <ol class="carousel-indicators">
            <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
            <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
          </ol>
          <div class="carousel-inner">
            <div class="carousel-item active">
              <img class="d-block w-100" src="../../assets/kursy.jpg" alt="Kursy walut" />
              <div class="carousel-caption d-none d-md-block">
                <h5>Kursy</h5>
                <p>Wyszukaj aktualne kursy walut</p>
              </div>
            </div>
            <div class="carousel-item">
              <img class="d-block w-100" src="../../assets/przelicznik.jpg" alt="Przeliczniki walut" />
              <div class="carousel-caption d-none d-md-block">
                <h5>Przeliczniki</h5>
                <p>Sprwadz aktualny wkaźnik wymiany dla interesujących Cię walut</p>
              </div>
            </div>
            <div class="carousel-item">
              <img class="d-block w-100" src="../../assets/wykresy.jpg" alt="Wykresy walut" />
              <div class="carousel-caption d-none d-md-block">
                <h5>Wykresy</h5>
                <p>Sprawdź historię kupa i sprzedaży dla wskazanych walut</p>
              </div>
            </div>
          </div>
          <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="sr-only">Poprzedni</span>
          </a>
          <a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="sr-only">Następny</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'PromoSection',
  components: {},
};
</script>
