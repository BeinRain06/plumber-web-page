<script>
import { ref, reactive, onMounted } from "vue";
import LandingPage from "./components/LandingPage.vue";
import LandingPageOne from "./components/LandingPageOne.vue";
export default {
  components: { LandingPageOne },
  setup() {
    const navlinks = ref([
      { id: "navlink-1", label: "home", ref: null },
      { id: "navlink-2", label: "about", ref: null },
      { id: "navlink-3", label: "work", ref: null },
      { id: "navlink-4", label: "contact", ref: null },
      { id: "navlink-5", label: "Tel: + 1 00-45-69-00-007", ref: null },
    ]);

    const currentActiveLink = ref(null);

    const currentLinkLogo = ref(null);

    const checkMenuRef = ref(null);

    const middleBarRef = ref(null);

    const modalMenuRef = ref(null);

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

    const handleMenu = (e) => {
      console.log("checkMenuRef:", checkMenuRef);
      if (!checkMenuRef.value.checked) {
        middleBarRef.value.classList.add("active_menu");
        modalMenuRef.value.classList.add("active_menu");
      } else {
        middleBarRef.value.classList.remove("active_menu");
        modalMenuRef.value.classList.remove("active_menu");
      }
    };

    onMounted(() => {
      currentActiveLink.value = navlinks.value[0].ref;
      currentActiveLink.value.classList.add("active_navlink");

      currentLinkLogo.value = navlinks.value[4].ref;

      currentLinkLogo.value?.firstElementChild.firstElementChild.classList.add(
        "display_contact_logo"
      );
    });

    return {
      navlinks,
      checkMenuRef,
      middleBarRef,
      modalMenuRef,
      setElementsLinkRef,
      handleNavLinks,
      handleMenu,
    };
  },
};
</script>

<template>
  <header>
    <nav
      class="w-full flex justify-between h-16 pl-6 pr-8 sm:h-auto sm:py-5 sm:px-10"
    >
      <div class="logo_brand w-max">
        <h3>DimiTr</h3>
        <h3 class="logo_letter_color">i</h3>
        <h3>o Cling</h3>
      </div>
      <ul class="navlink_desktop hidden sm:flex space-x-6">
        <li
          class="navlink"
          :key="item.id"
          :id="item.id"
          v-for="(item, i) in navlinks"
          :ref="(el) => setElementsLinkRef(el, i)"
          @click="async (el) => handleNavLinks(el, i)"
        >
          <div
            class="holder_navlink inline-flex items-center justify-end tansition-all duration-300 ease-in-out hover:text-[var(--accent-color-three)]"
          >
            <div
              class="nav_contact_logo w-5 h-full bg-color-text-paragraph inline-block rounded-full mr-2"
            >
              <p class="nav_off_p_class">
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
            </div>
            <div>
              <p class="nav_p_link">{{ item.label }}</p>
            </div>
          </div>
        </li>
      </ul>
      <!-- Menu Mobile -->
      <div class="menu_wrap block sm:hidden">
        <div
          class="menu_content relative w-8 h-8 flex justify-center items-center rounded border border-solid border-[var(--color-text)]"
        >
          <div
            class="middle_bar relative h-[1px] w-[72%] bg-[var(--color-text)] z-0"
            ref="middleBarRef"
          ></div>
          <div
            class="input_check_wrap absolute w-4/5 h-4/5 opacity-0 mx-auto z-10"
            @click="handleMenu"
          >
            <input
              type="checkbox"
              name="checkbox"
              class="check_menu w-full h-full rounded cursor-pointer"
              ref="checkMenuRef"
            />
          </div>
        </div>
        <div class="modal_menu" ref="modalMenuRef">
          <div class="modal_close w-full">
            <div
              class="icon_menu_close w-full h-6 cursor-pointer flex flex-row justify-end"
            >
              x
            </div>
          </div>
          <ul class="modal_menu_links flex flex-col space-y-6">
            <li
              class="modal_menu_link"
              :key="item.id"
              :id="item.id"
              v-for="(item, i) in navlinks"
              :ref="(el) => setElementsLinkRef(el, i)"
              @click="async (el) => handleNavLinks(el, i)"
            >
              <div
                class="holder_navlink inline-flex items-center justify-end tansition-all duration-300 ease-in-out hover:text-[var(--accent-color-three)]"
              >
                <div
                  class="nav_contact_logo w-5 h-full bg-color-text-paragraph inline-block rounded-full mr-2"
                >
                  <p class="nav_off_p_class">
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
                </div>
                <div>
                  <p class="nav_p_link">{{ item.label }}</p>
                </div>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
  <!-- <HelloWorld msg="Vite + Vue" /> -->
  <main class="w-full">
    <LandingPageOne />
  </main>

  <footer>
    <div class="footer_container w-full">
      <div
        class="footer_resume w-full h-[400px] md:h-[500px] flex flex-col md:flex-row items-center justify-center md:justify-between pt-10 md:pt-40 px-5 md:px-5"
      >
        <div class="footer_logo_brand self-center md:self-start flex flex-row">
          <h2>DimiTr</h2>
          <h2 class="logo_letter_color">i</h2>
          <h2>o Cling</h2>
        </div>
        <div
          class="footer_links relative w-full md:w-8/12 self-center md:self-start flex flex-row justify-start pt-10 md:pt-0"
        >
          <div
            class="footer_space w-1/4 flex flex-col items-center md:items-start gap-8"
          >
            <h4 class="sub_links_title">Home</h4>
            <div
              class="footer_expand_links w-full flex flex-col items-center md:items-start gap-4"
            >
              <a class="link_footer">about me</a>
              <a class="link_footer">assistance</a>
              <a class="link_footer">learn more</a>
            </div>
          </div>
          <div
            class="footer_space w-1/4 flex flex-col items-center md:items-start gap-8"
          >
            <h4 class="sub_links_title">Expertise</h4>
            <div
              class="footer_expand_links w-full flex flex-col items-center md:items-start gap-4"
            >
              <a class="link_footer">quotation</a>
              <a class="link_footer">advisory equipments</a>
              <a class="link_footer">water plan drawings</a>
            </div>
          </div>
          <div
            class="footer_space w-1/4 flex flex-col items-center md:items-start gap-8"
          >
            <h4 class="sub_links_title">Services</h4>
            <div
              class="footer_expand_links w-full flex flex-col items-center md:items-start gap-4"
            >
              <a class="link_footer">repairments</a>
              <a class="link_footer">new installation</a>
              <a class="link_footer">renovation</a>
            </div>
          </div>
          <div
            class="footer_space w-1/4 flex flex-col items-center md:items-start gap-8"
          >
            <h4 class="sub_links_title">Contact</h4>
            <div
              class="footer_expand_links w-full flex flex-col items-center md:items-start gap-4"
            >
              <a class="link_footer">xyzdimitrio@gmail.com</a>
              <a class="link_footer">learn more</a>
              <div
                class="social_media px-[0.5em] py-1 md:py-2 w-full flex flex-row justify-center md:justify-start items-center gap-5"
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
                class="adress_tel absolute top-58 md:top-0 right-4 md:right-0 md:relative w-full flex flex-row justify-end md:justify-start md:flex-col items-center md:items-start gap-1"
              >
                <div
                  class="footer_contact_label w-max md:w-40 m-0 p-0 flex flex-row justify-center items-center"
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
                  <p class="mx-1 w-max md:w-full footer_contact_title">
                    Contact us
                  </p>
                </div>
                <p
                  class="footer_contact_number w-max md:w-full flex flex-row items-center md:items-start pl-2 md:pb-4 md:-mt-1 break-words"
                >
                  + 1 00-45-69-00-007 / + 1 00-53-72-40-408
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="footer_terms_use w-full p-5 flex flex-row justify-between">
        <div class="w-max md:w-40 flex gap-2">
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
  color: var(--accent-color-three);
  margin: 0;
  padding: 0;
  letter-spacing: 0;
  display: inline;
}

h4.sub_links_title {
  font-size: 26px;
  font-size: calc(1.4625rem + 0.1vw);
  letter-spacing: 1px;
}

nav {
  position: fixed;
  top: 16px;
  left: 0;
  background-color: var(--navbar-background);
  box-shadow: 0px 0px 3px var(--color-title);
  z-index: 25;
}

div.nav_contact_logo {
  display: none;
}

div.nav_contact_logo.display_contact_logo {
  display: inline-flex;
}

@media (min-width: 9.9rem) {
  nav {
    position: fixed;
    top: 0;
    left: 0;
    background-color: var(--navbar-background);
    box-shadow: 0px 0px 3px var(--color-title);
    border-top: 4px solid transparent;
    z-index: 25;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo_brand h3:not(.logo_letter_color) {
    font-family: "Source Sans 3", sans-serif;
    font-size: var(--size-h4);
    font-weight: 600;
    color: var(--color-text);
    opacity: 0.9;
  }

  footer a {
    line-height: 32px;
    font-size: var(--size-sm);
  }

  .footer_contact_number,
  .footer_contact_title {
    font-size: var(--size-sm);
  }

  .footer_container {
    color: var(--color-text);
    background-color: var(--accent-color-one);
    font-family: "Source Sans 3", sans-serif;
    font-weight: 300;
  }

  .footer_logo_brand {
    padding: 1rem 1rem;
    font-family: "Source Sans 3", sans-serif;
    font-weight: 600;
    font-size: var(--size-h4);
    letter-spacing: 2px;
    opacity: 0.85;
  }

  .footer_terms_use p.logo_copyright {
    width: 40%;
  }

  /* Menu Mobile */

  .middle_bar {
    transition: all 1s ease;
  }

  .middle_bar::before {
    content: "";
    position: absolute;
    top: -6px;
    left: 0;
    right: 0;
    width: 100%;
    height: 1px;
    background-color: var(--color-text);
    transition: all 1s ease;
  }

  .middle_bar::after {
    content: "";
    position: absolute;
    top: 6px;
    left: 0;
    right: 0;
    width: 100%;
    height: 1px;
    background-color: var(--color-text);
    transition: all 1s ease;
  }

  .input_check_wrap {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  /* activate menu */

  .middle_bar.active_menu {
    transform: rotate(135deg);
  }

  .middle_bar.active_menu::before {
    top: 0;
    /* transform: rotate(45deg); */
    transform: rotate(90deg);
  }

  .middle_bar.active_menu::after {
    top: 0;
    /* transform: rotate(135deg); */
    transform: rotate(90deg);
  }

  .modal_menu {
    position: absolute;
    top: 3.8rem;
    left: 0;
    transform: scale(0.45) translateX(-50%);
    width: max(260px, 80%);
    height: max-content;
    padding: 1.125rem 0.9rem;
    color: var(--navbar-background);
    background-color: var(--color-text);
    visibility: invisible;
    opacity: 0;
    border-radius: 50%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    transition: all 310ms linear;
  }

  .modal_menu.active_menu {
    position: absolute;
    top: 3.8rem;
    left: 50%;
    transform: scale(1) translateX(-50%);
    width: max(260px, 80%);
    height: max-content;
    padding: 1.125rem 0.9rem;
    visibility: visible;
    opacity: 0.99;
    border-radius: 2px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    transition: all 300ms linear;
  }
}

@media (min-width: 47.925rem) {
  .logo_brand h3 {
    font-family: "Source Sans 3", sans-serif;
    font-size: var(--size-h3);
  }

  .navlink {
    font-size: var(--size-cater);
    color: var(--color-text);
    font-weight: inherit;
    border-radius: 0;
    border: 1px solid transparent;
    transition: all 650ms ease-in-out;
  }

  .navlink:hover {
    cursor: pointer;
  }

  .navlink.active_navlink {
    color: var(--accent-color-three);
    font-weight: 600;
    border-radius: 5px;
    border-bottom: 1px solid var(--accent-color-three);
  }

  footer a {
    line-height: 32px;
    font-size: var(--size-sm);
  }

  .footer_container {
    padding-right: 1.125rem;
  }

  .footer_logo_brand {
    padding: 2rem 2rem 1rem;
    font-family: "Source Sans 3", sans-serif;
    font-size: var(--size-h3);
    opacity: 0.85;
  }

  .footer_contact_number,
  .footer_contact_title {
    font-size: var(--size-regular);
  }

  .footer_links .adress_tel {
    font-size: calc(12px + 0.12vw);
  }

  .footer_terms_use p.logo_copyright {
    width: 20%;
  }
}
</style>
