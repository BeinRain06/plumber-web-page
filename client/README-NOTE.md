## 1. coding problem fix

### Problem 1 : Add logo contact to only the last nav-link when using V-For VueJS

- register all the nav-links as **ref** in the li html tag

```js
<li
          class="navlink"
          :key="item.id"
          :id="item.id"
          v-for="(item, i) in navlinks"
          :ref="(el) => setElementsLinkRef(el, i)" // <-- here
          @click="async (el) => handleNavLinks(el, i)"
        >
        ...
</li>

```

<br/>

- record and array of all reference - **li**

```js
const navlinks = ref([
  { id: "navlink-1", label: "home", ref: null },
  { id: "navlink-2", label: "about", ref: null },
  ...{ id: "navlink-5", label: "Tel: + 1 00-45-69-00-007", ref: null },
]);

// Fn to affect ref(null --> el) properties in navlinks
const setElementsLinkRef = (el, i) => {
  if (el) {
    navlinks.value[i].ref = el;
  }
};
```

- add **navlinks** in action in the life cylce Fn **onMounted**

```js
onMounted(() => {
  currentActiveLink.value = navlinks.value[0].ref;
  currentActiveLink.value.classList.add("active_navlink");

  currentLinkLogo.value = navlinks.value[4].ref; // <-- target li contact

  currentLinkLogo.value?.firstElementChild.firstElementChild.classList.add(
    "display_contact_logo"
  ); // <-- apply a new class that will display the <div> html tag holder
});
```

</br>

---

## 2. resources used

</br>

---

## 3. important reusable resources

A/ > How to remove a background effectively in an image using GIMP (tool)

[Use This Gimp Tip to Remove Picture Backgrounds Quickly](https://www.youtube.com/watch?v=PWZOMFFW9_0)
