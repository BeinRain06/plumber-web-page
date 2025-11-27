<script>
export default {
  setup() {
    return {};
  },
};
</script>
<template>
  <div class="landing_page p-0">
    <!-- hero page -->
    <div class="hero_wrapper">
      <div class="hero_context">
        <div class="hook_container">
          <div class="hook_value">
            <h1 class="core_value_main">
              Install Water Powering Devices For Your Building, on new Worldwide
              Standard
            </h1>
            <h4 class="core_value_sub">
              Work with Real professional and get unique installation that take
              from the best norm in the world
            </h4>
          </div>
          <div class="hook_cta">
            <a href="#" class="btn btn_contact">Contact Us</a>
          </div>
        </div>
      </div>
      <div class="hero_image"></div>
    </div>
    <!-- mission page -->
    <div class="mission_wrapper">
      <div class="mission_cover">
        <div class="mission_image"></div>
        <div class="mission_context">
          <div class="mission_value">
            <h2 class="mission_title t_under sp_b_1">Mission</h2>
            <p class="mission_text text_usage sp_b_2 w-4/5">
              Our Entreprize regard on standard are very strict on construction
            </p>

            <p class="mission-text text_usage">
              Dimitrio Cling With over 7 Years in the field, focus are technical
              efficienccy and installation. With a team of 60+ technicians
              trained to equip household and industries with modern devices.
            </p>
          </div>
          <div class="mission_cta">
            <a href="#" class="btn_link">Career</a>
          </div>
        </div>
      </div>
    </div>
    <!-- preview-projects page -->
    <div class="projects_preview_wrapper">
      <div class="projects_preview_cover">
        <div class="projects_preview_title flex justify-center">
          <h2 class="preview_title">Projects Build On Trust</h2>
        </div>
        <div class="projects_preview_cards">
          <div id="card-1" class="project_preview_card">
            <div class="preview_image"></div>
            <div class="preview_location">
              <h6 class="building_name">Home Dicklan</h6>
              <p class="location_name loc_img">Nord-West, Callun</p>
            </div>
          </div>
          <div id="card-2" class="project_preview_card">
            <div class="preview_image"></div>
            <div class="preview_location">
              <h6 class="building_name">Home Dicklan</h6>
              <p class="location_name loc_img">Nord-West, Callun</p>
            </div>
          </div>
          <div id="card-3" class="project_preview_card">
            <div class="preview_image"></div>
            <div class="preview_location">
              <h6 class="building_name">Home Dicklan</h6>
              <p class="location_name loc_img">Nord-West, Callun</p>
            </div>
          </div>
          <div id="card-4" class="project_preview_card">
            <div class="preview_image"></div>
            <div class="preview_location">
              <h6 class="building_name">Home Dicklan</h6>
              <p class="location_name loc_img">Nord-West, Callun</p>
            </div>
          </div>
          <div id="card-5" class="project_preview_card">
            <div class="preview_image"></div>
            <div class="preview_location">
              <h6 class="building_name">Home Dicklan</h6>
              <p class="location_name loc_img">Nord-West, Callun</p>
            </div>
          </div>
          <div id="card-6" class="project_preview_card">
            <div class="preview_image"></div>
            <div class="preview_location">
              <h6 class="building_name">Home Dicklan</h6>
              <p class="location_name loc_img">Nord-West, Callun</p>
            </div>
          </div>
        </div>
        <div class="preview_redirect_link sp_r_1 flex justify-end">
          <a href="#" class="btn_link">Our Work</a>
        </div>
      </div>
    </div>
    <!-- trust -->
    <div class="trust_wrapper">
      <div class="trust_cover">
        <h2 class="trust_main_title flex justify-center">Why Us ?</h2>
        <div class="trust_main_card">
          <div class="trust_img_one"></div>
          <div class="trust_a_context">
            <div class="trust_value">
              <h2 class="trust_title t_under sp_b_1">Credibility</h2>

              <p class="trust_text text_usage sp_b_2 w-4/5">
                Transparency over the quality and costs of the materials
              </p>

              <p class="trust_text text_usage">
                Adapt Demands to a budget that align with safetiness
              </p>
            </div>
            <div class="trust_cta">
              <a href="#" class="btn btn_wrap btn_contact">Contact Us</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- testimonials -->
  <!-- services -->
  <!-- breathing-section -->
  <!-- reinforcement-value -->
</template>

<style scoped>
@import "tailwindcss";

/* local utilities */
.t_under {
  border-bottom-width: 1px;
  border-style: solid;
  border-color: inherit;
}

.sp_b_1 {
  margin-bottom: 2.025rem;
}

.sp_b_2 {
  margin-bottom: 1.35rem;
}

.sp_r_1 {
  padding-right: 1.35rem;
}

/* <Hero-Section> */
.hero_wrapper {
  position: relative;
  top: 42px;
  scroll-margin-top: 0;
  width: 100%;
  height: 80vh;
  padding: 5.85rem 0 4.05rem;
  margin: 0;

  /* background: linear-gradient(
    97.39deg,
    rgb(54, 56, 57) 25.12%,
    rgb(33, 37, 41) 82.16%
  ); */

  background: linear-gradient(
    97.39deg,
    rgb(43, 53, 58) 25.12%,
    rgb(42, 51, 56) 82.16%
  );
  display: flex;
  flex-direction: row;
  gap: 0.45rem;
  border-top: 1px solid transparent;
}

.hero_context {
  width: 56.4%;
  padding-left: 2.925rem;
}

.hero_image {
  width: 43.6%;
  height: 100%;
  padding: 0.675rem 2.025rem;
  background: url("../assets/new-images/indosup-pixebay-1.png") right center
    no-repeat;
  background-size: 94.4%;
  border: none;
  outline: none;
}

h1.core_value_main {
  padding-bottom: 0.45rem;
  margin-bottom: 0.9rem;
  font-weight: bold;
}

.hook_cta {
  margin-top: 1.575rem;
}

/* <Mission-Section> */
.mission_wrapper {
  width: 100%;
  height: 36rem;
  padding: 8.55rem 0 4.05rem;
  background-color: var(--aux-background);
}

.mission_cover {
  width: 100%;
  padding-left: 2.925rem;
  display: flex;
  flex-direction: row;
  gap: 2.025rem;
}

.mission_image {
  width: 41.2%;
  height: 20.7rem;
  background: url("../assets/new-images/ReinhardThrainer-pixabay.jpg") left
    center no-repeat;
  background-size: 94.4%;
}

.mission_context {
  width: 54.6%;
}

.mission_cta {
  padding-top: 2.7rem;
}

/* <Projects-Preview-Section> */
.projects_preview_wrapper {
  width: 100%;
  height: auto;
  padding: 1.575rem 0 4.05rem;
}

.projects_preview_title {
  width: 100%;
  padding: 2.475rem 3.7125rem;
}

.projects_preview_cards {
  width: 86.2%;
  padding: 5.4rem 2.925rem 7.2rem;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(3, minmax(15.075rem, 1fr));
  grid-auto-rows: 16.65rem;
  gap: 1.35rem;
}

.project_preview_card {
  width: 100%;
  padding: 1.35rem 2.7rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.9rem;
}

.preview_image {
  width: 100%;
  height: 100%;
  background: url("../assets/new-images/PeterH-pixabay.jpg") left center
    no-repeat;
  background-size: cover;
}

.preview_location {
  width: 100%;
  height: 12.2%;
  display: flex;
  flex-direction: row;
  justify-content: end;
  align-items: center;
  gap: 0.81rem;
}

/* <Trust-Section> */

.trust_cover {
  width: 100%;
  height: auto;
  background-color: var(--color-accent-two);
}

.trust_main_title {
  width: 100%;
  padding: 1.35rem 3.7125rem;
  background-color: var(--color-accent-two);
}

.trust_main_card {
  width: 100%;
  height: 18.9rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 1.35rem;
}

.trust_img_one {
  width: 34.6%;
  height: 100%;
  transform: scale(0.92);
  background: url("../assets/new-images/BobDmyt-pixabay.jpg") left center
    no-repeat;
  background-size: 100%;
}

.trust_a_context {
  display: flex;
  flex-direction: column;
}

.trust_cta {
  padding-top: 1.4625rem;
}
</style>
