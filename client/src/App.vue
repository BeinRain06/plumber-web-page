<script>
import { ref, onMounted } from "vue";
import LandingPage from "./components/LandingPage.vue";
export default {
  components: { LandingPage },
  setup() {
    const navlinks = ref([
      { id: "navlink-1", label: "HOME", ref: null },
      { id: "navlink-2", label: "ABOUT", ref: null },
      { id: "navlink-3", label: "EXPERTISE", ref: null },
      { id: "navlink-4", label: "FEEDBACKS", ref: null },
      { id: "navlink-5", label: "SERVICES", ref: null },
      { id: "navlink-6", label: "CONTACT", ref: null },
    ]);

    const currentActiveLink = ref(null);

    const setElementsLinkRef = (el, i) => {
      if (el) {
        navlinks.value[i].ref = el;
      }
    };

    const handleNavLinks = async (el, i) => {
      if (currentActiveLink.value) {
        currentActiveLink.value.classList.remove("active_navlink");
      }
      currentActiveLink.value = await navlinks.value[i].ref;
      currentActiveLink.value?.classList.add("active_navlink");
    };

    onMounted(() => {
      currentActiveLink.value = navlinks.value[0].ref;
      currentActiveLink.value.classList.add("active_navlink");
    });

    return {
      navlinks,
      setElementsLinkRef,
      handleNavLinks,
    };
  },
};
</script>

<template>
  <header>
    <nav class="w-full flex justify-between py-5 px-10">
      <div class="logo_brand">
        <h3>DimiTr</h3>
        <h3 class="logo_letter_color">i</h3>
        <h3>o Cling</h3>
      </div>
      <ul class="flex space-x-6">
        <li
          class="navlink"
          :key="item.id"
          :id="item.id"
          v-for="(item, i) in navlinks"
          :ref="(el) => setElementsLinkRef(el, i)"
          @click="async (el) => handleNavLinks(el, i)"
        >
          {{ item.label }}
        </li>
      </ul>
    </nav>
  </header>
  <!-- <HelloWorld msg="Vite + Vue" /> -->
  <main class="w-full">
    <LandingPage />
  </main>

  <footer>
    <div class="footer_container w-full">
      <div
        class="footer_resume w-full h-[500px] flex xxs:flex-col sm:flex-row items-center justify-between pt-40 px-10"
      >
        <div class="footer_logo_brand self-start flex flex-row">
          <h2>DimiTr</h2>
          <h2 class="logo_letter_color">i</h2>
          <h2>o Cling</h2>
        </div>
        <div class="footer_links w-8/12 self-start flex flex-row justify-start">
          <div class="footer_space w-1/4 flex flex-col items-start gap-8">
            <h4 class="sub_links_title">Home</h4>
            <div
              class="footer_expand_links w-full flex flex-col items-start gap-4"
            >
              <a>about me</a>
              <a>assistance</a>
              <a>learn more</a>
            </div>
          </div>
          <div class="footer_space w-1/4 flex flex-col items-start gap-8">
            <h4 class="sub_links_title">Expertise</h4>
            <div
              class="footer_expand_links w-full flex flex-col items-start gap-4"
            >
              <a>quotation</a>
              <a>advisory equipments</a>
              <a>water plan drawings</a>
            </div>
          </div>
          <div class="footer_space w-1/4 flex flex-col items-start gap-8">
            <h4 class="sub_links_title">Services</h4>
            <div
              class="footer_expand_links w-full flex flex-col items-start gap-4"
            >
              <a>repairments</a>
              <a>new installation</a>
              <a>renovation</a>
            </div>
          </div>
          <div class="footer_space w-1/4 flex flex-col items-start gap-8">
            <h4 class="sub_links_title">Contact</h4>
            <div
              class="footer_expand_links w-full flex flex-col items-start gap-4"
            >
              <a>xyzdimitrio@gmail.com</a>
              <a>learn more</a>
              <div
                class="social_media px-[0.5em] py-2 w-full flex flex-row items-center gap-5"
              >
                <i id="facebook" class="media">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="18"
                    height="18"
                    viewBox="0 0 486.037 1000"
                  >
                    <path
                      fill="currentColor"
                      d="M124.074 1000V530.771H0V361.826h124.074V217.525C124.074 104.132 197.365 0 366.243 0C434.619 0 485.18 6.555 485.18 6.555l-3.984 157.766s-51.564-.502-107.833-.502c-60.9 0-70.657 28.065-70.657 74.646v123.361h183.331l-7.977 168.945H302.706V1000z"
                    />
                  </svg>
                </i>
                <i id="linkedin" class="media">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="18"
                    height="18"
                    viewBox="0 0 1046.16 1000"
                  >
                    <path
                      fill="currentColor"
                      d="M237.485 1000V325.301H13.229V1000zM125.386 233.127c78.202 0 126.879-51.809 126.879-116.553C250.808 50.37 203.591-.001 126.87-.001C50.161-.001-.002 50.371-.002 116.574c0 64.747 48.665 116.553 123.924 116.553h1.457zM361.61 1000h224.256V623.215c0-20.165 1.457-40.309 7.379-54.724c16.212-40.289 53.111-82.017 115.06-82.017c81.149 0 113.613 61.872 113.613 152.572v360.949h224.242V613.129c0-207.241-110.636-303.668-258.183-303.668c-120.977 0-174.094 67.622-203.603 113.679h1.497v-97.853H361.615c2.943 63.31 0 674.699 0 674.699z"
                    />
                  </svg>
                </i>
                <i id="tweeter" class="media">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="18"
                    height="18"
                    viewBox="0 0 1231.051 1000"
                  >
                    <path
                      fill="currentColor"
                      d="M1231.051 118.453q-51.422 76.487-126.173 130.403q.738 14.46.738 32.687q0 101.273-29.53 202.791q-29.53 101.519-90.215 194.343T841.297 843.145T639.62 957.395t-252.474 42.606q-210.2 0-387.147-113.493q31.406 3.495 60.242 3.495q175.605 0 313.687-108.177q-81.877-1.501-146.654-50.409q-64.777-48.907-89.156-124.988q24.097 4.59 47.566 4.59q33.782 0 66.482-8.812q-87.378-17.5-144.975-87.04q-57.595-69.539-57.595-160.523v-3.126q53.633 29.696 114.416 31.592q-51.762-34.508-82.079-89.999q-30.319-55.491-30.319-120.102q0-68.143 34.151-126.908q95.022 116.607 230.278 186.392q135.258 69.786 290.212 77.514q-6.609-27.543-6.621-57.485q0-104.546 73.994-178.534Q747.623 0 852.169 0q109.456 0 184.392 79.711q85.618-16.959 160.333-61.349q-28.785 90.59-110.933 139.768q75.502-8.972 145.088-39.677z"
                    />
                  </svg>
                </i>
              </div>
              <div
                class="adress_tel w-full sm:w-max flex flex-col items-center sm:items-start gap-1"
              >
                <div
                  class="footer_contact_label w-40 m-0 p-0 flex flex-row items-center"
                >
                  <p>
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="18"
                      height="18"
                      viewBox="0 0 24 24"
                    >
                      <path
                        fill="currentColor"
                        d="M16 11V8h-3V7h3V4h1v3h3v1h-3v3zm2.93 9q-2.528 0-5.184-1.266t-4.935-3.555t-3.545-4.935T4 5.07q0-.458.3-.763T5.05 4h2.473q.408 0 .712.257t.411.659L9.142 7.3q.07.42-.025.733t-.333.513L6.59 10.592q.616 1.117 1.361 2.076t1.59 1.817q.87.87 1.874 1.62q1.004.749 2.204 1.414l2.139-2.177q.244-.263.549-.347q.304-.083.674-.033l2.103.43q.408.1.662.411t.254.712v2.435q0 .45-.306.75t-.763.3M6.12 9.654l1.92-1.765q.095-.077.124-.212q.03-.135-.01-.25l-.443-2.12q-.039-.153-.135-.23T7.327 5H5.275q-.115 0-.192.077t-.077.192q.029 1.025.321 2.14t.794 2.245m8.45 8.334q1.014.502 2.16.743q1.148.24 2 .257q.115 0 .192-.077T19 18.72v-2.008q0-.153-.077-.25q-.077-.096-.23-.134l-1.85-.379q-.116-.039-.203-.01q-.086.03-.182.125zm0 0"
                      />
                    </svg>
                  </p>
                  <p class="mx-1 w-10">Contact us</p>
                </div>
                <p class="footer_contact_number pl-2 pb-4 -mt-1">
                  003 2450 8379 / 005 7240 2108
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="footer_terms_use w-full p-5 flex flex-row justify-between">
        <div class="w-40 flex gap-2">
          <p class="logo_copyright">&copy;</p>
          <p>Dimitrio Cling</p>
        </div>
        <div class="terms_use flex gap-4">
          <a>Privacy Policy</a>
          <a>Terms of services</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
@import "tailwindcss";

@theme {
  --breakpoint-xxs: 8rem;
}

ul {
  list-style: none;
}

.logo_brand h3 {
  display: inline;
}

.logo_letter_color {
  color: var(--accent-color-3);
  margin: 0;
  padding: 0;
  letter-spacing: 0;
  display: inline;
}

h4.sub_links_title {
  font-family: "Source Sans 3", sans-serif;
  font-weight: 600;
}

nav {
  position: fixed;
  top: 0;
  background-color: var(--background-navbar);
  box-shadow: 0px 0px 3px var(--accent-color-2);
  z-index: 25;
}

@media (min-width: 8rem) {
  .footer_terms_use p.logo_copyright {
    width: 40%;
  }
}

@media (min-width: 28rem) {
  .logo_brand {
    font-family: "Source Sans 3", sans-serif;
    font-size: var(--size-regular);
    font-weight: 600;
    color: var(--background-main-content-1);
    opacity: 0.9;
  }

  .navlink {
    font-size: var(--size-cater);
    color: var(--background-main-content-2);
    font-weight: inherit;
    /*  text-decoration: none; */
    transform: skew(0deg, 0deg);
    transition: all 450ms ease-in-out;
  }

  .navlink:hover {
    cursor: pointer;
  }

  .navlink.active_navlink {
    color: var(--primary-color);
    font-size: calc(16px + 0.1vw);
    font-weight: 600;
    transform: skew(0deg, -0.5deg);
  }

  footer a {
    line-height: 32px;
    font-size: var(--size-sm);
  }

  .footer_container {
    color: var(--background-main-content-1);
    background-color: var(--background-footer);
    font-family: "Source Sans 3", sans-serif;
    font-weight: 300;
  }

  .footer_logo_brand {
    padding: 2rem 2rem 1rem;
    font-family: "Source Sans 3", sans-serif;
    font-weight: 600;
    font-size: 28px;
    letter-spacing: 2px;
    opacity: 0.85;
  }

  .footer_links .adress_tel {
    font-size: calc(12px + 0.12vw);
  }

  .adress_tel p {
    width: max-content;
  }

  .footer_terms_use p.logo_copyright {
    width: 20%;
  }
}
</style>
