<template>
  <div id="page-top">
    <NavSection />
    <MastheadSection />
    <PromoSection />
    <FunctionsSection />
    <GallerySection />
    <FooterSection />
    <ModalSection />
  </div>
</template>

<script>
// Sekcje HTML
import MastheadSection from '../components/HomeSections/MastheadSection';
import PromoSection from '../components/HomeSections/PromoSection';
import NavSection from '../components/HomeSections/NavSection';
import FunctionsSection from '../components/HomeSections/FunctionsSection';
import GallerySection from '../components/HomeSections/GallerySection';
import FooterSection from '../components/HomeSections/FooterSection';
import ModalSection from '../components/HomeSections/ModalSection';

export default {
  name: 'Home',
  components: { NavSection, MastheadSection, PromoSection, FunctionsSection, ModalSection, FooterSection, GallerySection },
};
</script>

<style>
@import '../assets/style.css';

.content-container {
  background: #313131;
}
</style>
