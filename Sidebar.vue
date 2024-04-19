<template>
  <div>
    <!-- mobile  EMPLOYEE start -->
    <div v-if="sb_logged_user.role_type == 100 && is_employee" class="flex md:hidden">
      <div class="fixed inset-0 flex z-40" v-show="sidebarMobile.open" :class="sidebarMobile.open ? '' : 'pointer-events-none'">
        <!-- Off-canvas menu overlay, show/hide based on off-canvas menu state. -->
        <transition enter-active-class="transition-opacity ease-linear duration-300" enter-class="opacity-0" enter-to-class="opacity-100" leave-active-class="transition-opacity ease-linear duration-300" leave-class="opacity-100" leave-to-class="opacity-0">
          <div @click="closeSidebar" class="fixed inset-0" v-show="sidebarMobile.open">
            <div class="absolute inset-0 bg-gray-600 opacity-75"></div>
          </div>
        </transition>

        <transition enter-active-class="transition ease-in-out duration-300 transform" enter-class="-translate-x-full" enter-to-class="translate-x-0" leave-active-class="transition ease-in-out duration-300 transform" leave-class="translate-x-0" leave-to-class="-translate-x-full">
          <div class="relative flex-1 flex flex-col max-w-xs w-full bg-gray-800" v-show="sidebarMobile.open">
            <div class="absolute top-0 right-0 -mr-14 p-1 bg-gray-800">
              <button @click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar">
                <Icon name="closemenu" />
              </button>
            </div>
            <div class="flex items-center flex-shrink-0 ">

              <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
              <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
            </div>
            <ActionButton :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>

            <div class="px-3 mt-6 relative inline-block text-left bg-gray-800">
              <button type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-white bg-gray-650 hover:bg-gray-950 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
                <span class="flex w-full justify-between items-center">
                  <span class="flex min-w-0 items-center justify-between space-x-3">
                    <span class="flex-1 flex flex-col min-w-0">
                      <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                      <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                    </span>
                  </span>
                  <!-- Heroicon name: solid/selector -->
                </span>
              </button>
            </div>
          </div>
        </transition>
      </div>
    </div>
    <!-- mobile  EMPLOYEE end -->

    <!-- desktop   EMPLOYEE start -->
    <div v-if="sb_logged_user.role_type == 100 && is_employee" class="hidden md:flex">
      <div class="flex-1 flex flex-col pt-5 pb-4 overflow-y-auto bg-gray-800">
        <div class="flex items-center flex-shrink-0 ">
          <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
          <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
        </div>
        <div class="px-3 mt-6 relative inline-block text-left">
          <button type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-white bg-gray-650 hover:bg-gray-950 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
            <span class="flex w-full justify-between items-center">
              <span class="flex min-w-0 items-center justify-between space-x-3">
                <span class="flex-1 flex flex-col min-w-0">
                  <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                  <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                </span>
              </span>
              <!-- Heroicon name: solid/selector -->
            </span>
          </button>
          <ActionButton :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>

        </div>
      </div>
    </div>
    <!-- desktop   EMPLOYEE end -->

    <!-- mobile menu PVLHTH start -->
    <div v-if="sb_logged_user.role_type == 4 || sb_logged_user.role_type == 5" class="flex md:hidden">
      <div class="fixed inset-0 flex z-40" v-show="sidebarMobile.open" :class="sidebarMobile.open ? '' : 'pointer-events-none'">
        <transition enter-active-class="transition-opacity ease-linear duration-300" enter-class="opacity-0" enter-to-class="opacity-100" leave-active-class="transition-opacity ease-linear duration-300" leave-class="opacity-100" leave-to-class="opacity-0">
          <div @click="closeSidebar" class="fixed inset-0" v-show="sidebarMobile.open">
            <div class="absolute inset-0 bg-gray-600 opacity-75"></div>
          </div>
        </transition>
        <!-- Off-canvas menu overlay, show/hide based on off-canvas menu state. -->
        <transition enter-active-class="transition ease-in-out duration-300 transform" enter-class="-translate-x-full" enter-to-class="translate-x-0" leave-active-class="transition ease-in-out duration-300 transform" leave-class="translate-x-0" leave-to-class="-translate-x-full">
          <div class="relative flex-1 flex flex-col max-w-xs w-full bg-white" v-show="sidebarMobile.open">
            <div class="absolute top-0 right-0 -mr-14 p-1 bg-gray-800">
              <button :click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar2">
                <Icon name="closemenu" />
              </button>
            </div>
            <div class="flex-1 h-0 pt-5 pb-4 overflow-y-auto bg-gray-800">
              <div class="flex items-center flex-shrink-0 ">
                <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
                <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
              </div>
              <div>
                <!-- normal user  sub menu-->
                <div v-on:mouseleave="userMenuOpen = false" class="border border-gray-200 z-10 mx-3 origin-top absolute right-0 left-0 mt-1 rounded-md shadow-lg ring-1 ring-black ring-opacity-5 divide-y divide-gray-200 focus:outline-none bg-gray-650" role="menu" aria-orientation="vertical" aria-labelledby="options-menu-button" tabindex="-1">
                  <div class="absolute top-0 right-0 -mr-14 p-1">
                    <button :click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar">
                      <Icon name="closemenu" />
                    </button>
                  </div>
                  <nav class="mt-5 px-2 space-y-1">
                    <button @click.prevent="sb_run_as_role()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
                      Επίδειξη
                    </button>
                    <ex-router-link v-if="sb_logged_user.trader.is_reseller==0" :to="{ name: 'pvlhthsregister' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
                      Εγγραφή Πελάτη
                    </ex-router-link>
                    <ex-router-link :to="{ name: 'companies' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
                      Εταιρείες {{sb_logged_user.trader.is_reseller}}
                    </ex-router-link>
                    <ex-router-link :to="{ name: 'ananevseis' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
                      Ανανεώσεις
                    </ex-router-link>
                    <ex-router-link v-if="sb_logged_user.trader.is_reseller==0" :to="{ name: 'anamenomena' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
                      Αναμενόμενα
                    </ex-router-link>
                    <ex-router-link v-if="sb_logged_user.trader.is_reseller==0" :to="{ name: 'pvlhthsplhrvmestritoi' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
                      Πληρωμές τρίτων
                    </ex-router-link>
                    <button v-if="sb_logged_user.trader.is_reseller==0" @click.prevent="traders_pvlhths_plhrvmes()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
                      Προς εκκαθάριση
                    </button>
                    <ex-router-link v-if="sb_logged_user.ismainuser<10" :to="{ name: 'tradercard', params: { mode: 3 } }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
                      Καρτέλα
                    </ex-router-link>
                    <ex-router-link :to="{name: 'uploadfiles',params: { fortype: 'pvlhthinvoice', fortypetxt: 'Τιμολόγιο παροχής υπηρεσιών (για την προμήθεια)',forinvoice:1,import_type:1 },}" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
                      Εισαγωγή Τιμολογίου
                    </ex-router-link>
                    <div v-if="sb_logged_user.in_role_as>0">
                      <button class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150" href="#" @click.prevent="return_torole()">
                        <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        Επιστροφή στο ρόλο μου
                      </button>
                    </div>
                    <ActionButton :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
                  </nav>
                </div>
              </div>
            </div>
          </div>
        </transition>
      </div>
    </div>
    <!-- mobile menu PVLHTH end -->
    <!-- desktop PVLHTH start -->
    <div v-if="sb_logged_user.role_type == 4 || sb_logged_user.role_type == 5" class="hidden md:flex">

      <div class="flex-1 flex flex-col pt-5 pb-4 overflow-y-auto bg-gray-800">
        <div class="flex items-center flex-shrink-0 ">
          <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
          <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
        </div>
        <div v-if="sb_logged_user.in_role_as>0" class="flex flex-col items-center border">
          <div class="w-full text-center text-white">Για λογαριασμό: {{ company.vat }}</div>
          <div class="w-full text-center text-white"> {{ company.name }}</div>
        </div>
        <div class="px-3 mt-6 relative inline-block text-left">
          <button type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-white bg-gray-650 hover:bg-black focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
            <span class="flex w-full justify-between items-center">
              <span class="flex min-w-0 items-center justify-between space-x-3">
                <span class="flex-1 flex flex-col min-w-0">
                  <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                  <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                </span>
              </span>
              <!-- Heroicon name: solid/selector -->
            </span>
          </button>
        </div>

        <button @click.prevent="sb_run_as_role()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
          Επίδειξη
        </button>
        <ex-router-link v-if="sb_logged_user.trader.is_reseller==0" :to="{ name: 'pvlhthsregister' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
          Εγγραφή Πελάτη
        </ex-router-link>
        <ex-router-link :to="{ name: 'companies' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
          Εταιρείες
        </ex-router-link>
        <ex-router-link :to="{ name: 'ananevseis' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
          Ανανεώσεις
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.trader.is_reseller==0" :to="{ name: 'anamenomena' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
          Αναμενόμενα
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.trader.is_reseller==0" :to="{ name: 'pvlhthsplhrvmestritoi' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
          Πληρωμές τρίτων
        </ex-router-link>
        <button v-if="sb_logged_user.trader.is_reseller==0" @click.prevent="traders_pvlhths_plhrvmes()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
          Προς εκκαθάριση
        </button>
        <ex-router-link v-if="sb_logged_user.ismainuser<10" :to="{ name: 'tradercard', params: { mode: 3 } }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
          Καρτέλα
        </ex-router-link>

        <ex-router-link :to="{name: 'uploadfiles',params: { fortype: 'pvlhthinvoice', fortypetxt: 'Τιμολόγιο παροχής υπηρεσιών (για την προμήθεια)',forinvoice:1 ,import_type:1},}" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
          Εισαγωγή Τιμολογίου
        </ex-router-link>
        <div v-if="sb_logged_user.in_role_as>0">
          <button class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150" href="#" @click.prevent="return_torole()">
            <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
            Επιστροφή στο ρόλο μου
          </button>
        </div>

        <ActionButton :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
      </div>
    </div>
    <!-- desktop PVLHTH end -->

    <!-- mobile menu ΙΔΙΟΚΤΗΤΗ ΠΟΛΛΩΝ Βοηθός λογιστή start -->
    <div v-if="sb_logged_user.role_type == 6 || sb_logged_user.role_type == 11" class="flex md:hidden">
      <div class="fixed inset-0 flex z-40" v-show="sidebarMobile.open" :class="sidebarMobile.open ? '' : 'pointer-events-none'">
        <transition enter-active-class="transition-opacity ease-linear duration-300" enter-class="opacity-0" enter-to-class="opacity-100" leave-active-class="transition-opacity ease-linear duration-300" leave-class="opacity-100" leave-to-class="opacity-0">
          <div @click="closeSidebar" class="fixed inset-0" v-show="sidebarMobile.open">
            <div class="absolute inset-0 bg-gray-600 opacity-75"></div>
          </div>
        </transition>
        <!-- Off-canvas menu overlay, show/hide based on off-canvas menu state. -->
        <transition enter-active-class="transition ease-in-out duration-300 transform" enter-class="-translate-x-full" enter-to-class="translate-x-0" leave-active-class="transition ease-in-out duration-300 transform" leave-class="translate-x-0" leave-to-class="-translate-x-full">
          <div class="relative flex-1 flex flex-col max-w-xs w-full bg-white" v-show="sidebarMobile.open">
            <div class="absolute top-0 right-0 -mr-14 p-1 bg-gray-800">
              <button :click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar2">
                <Icon name="closemenu" />
              </button>
            </div>
            <div class="flex-1 h-0 pt-5 pb-4 overflow-y-auto bg-gray-800">
              <div class="flex items-center flex-shrink-0 ">
                <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
                <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
              </div>
              <div>
                <!-- normal user  sub menu-->
                <div v-on:mouseleave="userMenuOpen = false" class="border border-gray-200 z-10 mx-3 origin-top absolute right-0 left-0 mt-1 rounded-md shadow-lg ring-1 ring-black ring-opacity-5 divide-y divide-gray-200 focus:outline-none bg-gray-650" role="menu" aria-orientation="vertical" aria-labelledby="options-menu-button" tabindex="-1">
                  <div class="absolute top-0 right-0 -mr-14 p-1">
                    <button :click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar">
                      <Icon name="closemenu" />
                    </button>
                  </div>
                  <nav class="mt-5 px-2 space-y-1">
                    <ex-router-link :to="{ name: 'traders.edit', params: { id: sb_logged_user.trader.id } }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Στοιχεία μου
                    </ex-router-link>
                    <ex-router-link v-if="sb_logged_user.is_erganh_user" :to="{ name: 'acounttraderserganh' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Στοιχεία Εταιρείων για Εργάνη
                    </ex-router-link>
                    <ex-router-link v-if="sb_logged_user.role_type == 5" :to="{ name: 'users' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Βοηθοί λογιστή
                    </ex-router-link>
                    <ex-router-link :to="{ name: 'chfiakhmisuodosia' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Μισθοδοσία όλων
                    </ex-router-link>
                    <ex-router-link v-if="sb_logged_user.role_type == 5" :to="{ name: 'pvlhthsregister' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Εγγραφή πελάτη στο eoraria.gr
                    </ex-router-link>
                    <div v-if="sb_logged_user.in_role_as>0">
                      <button class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150" href="#" @click.prevent="return_torole()">
                        <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        Επιστροφή στο ρόλο μου
                      </button>
                    </div>
                    <ActionButton :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
                  </nav>
                </div>
              </div>
            </div>
          </div>
        </transition>
      </div>
    </div>
    <!-- mobile menu ΙΔΙΟΚΤΗΤΗ ΠΟΛΛΩΝ Βοηθός λογιστή  end -->
    <!-- desktop ΙΔΙΟΚΤΗΤΗ ΠΟΛΛΩΝ start Βοηθός λογιστή -->
    <div v-if="sb_logged_user.role_type == 6 || sb_logged_user.role_type == 11" class="hidden md:flex">

      <div class="flex-1 flex flex-col pt-5 pb-4 overflow-y-auto bg-gray-800">
        <div class="flex items-center flex-shrink-0 ">
          <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
          <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
        </div>
        <div v-if="sb_logged_user.in_role_as>0 " class="flex flex-col items-center border">
          <div class="w-full text-center text-white">Για λογαριασμό: {{ sb_logged_user.trader.vat }}</div>
          <div class="w-full text-center text-white"> {{ sb_logged_user.trader.name }}</div>
        </div>
        <div class="px-3 mt-6 relative inline-block text-left">
          <button type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-white bg-gray-650 hover:bg-black focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
            <span class="flex w-full justify-between items-center">
              <span class="flex min-w-0 items-center justify-between space-x-3">
                <span class="flex-1 flex flex-col min-w-0">
                  <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                  <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                </span>
              </span>
              <!-- Heroicon name: solid/selector -->
            </span>
          </button>
        </div>

        <ex-router-link :to="{ name: 'acounttraderserganh' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
          Στοιχεία Εταιρείων για Εργάνη
        </ex-router-link>
        <div v-if="sb_logged_user.in_role_as>0">
          <button class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150" href="#" @click.prevent="return_torole()">
            <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
            Επιστροφή στο ρόλο μου
          </button>
        </div>
        <ActionButton :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
      </div>
    </div>
    <!-- desktop ΙΔΙΟΚΤΗΤΗ ΠΟΛΛΩΝ end -->

    <!-- mobile menu Λογιστή start -->
    <div v-if="sb_logged_user.role_type == 10 || sb_logged_user.role_type == 12 " class="flex md:hidden">
      <div class="fixed inset-0 flex z-40" v-show="sidebarMobile.open" :class="sidebarMobile.open ? '' : 'pointer-events-none'">
        <transition enter-active-class="transition-opacity ease-linear duration-300" enter-class="opacity-0" enter-to-class="opacity-100" leave-active-class="transition-opacity ease-linear duration-300" leave-class="opacity-100" leave-to-class="opacity-0">
          <div @click="closeSidebar" class="fixed inset-0" v-show="sidebarMobile.open">
            <div class="absolute inset-0 bg-gray-600 opacity-75"></div>
          </div>
        </transition>
        <!-- Off-canvas menu overlay, show/hide based on off-canvas menu state. -->
        <transition enter-active-class="transition ease-in-out duration-300 transform" enter-class="-translate-x-full" enter-to-class="translate-x-0" leave-active-class="transition ease-in-out duration-300 transform" leave-class="translate-x-0" leave-to-class="-translate-x-full">
          <div class="relative flex-1 flex flex-col max-w-xs w-full bg-white" v-show="sidebarMobile.open">
            <div class="absolute top-0 right-0 -mr-14 p-1 bg-gray-800">
              <button :click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar2">
                <Icon name="closemenu" />
              </button>
            </div>
            <div class="flex-1 h-0 pt-5 pb-4 overflow-y-auto bg-gray-800">
              <div class="flex items-center flex-shrink-0 ">
                <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
                <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
              </div>
              <div>
                <!-- normal user  sub menu-->
                <div v-on:mouseleave="userMenuOpen = false" class="border border-gray-200 z-10 mx-3 origin-top absolute right-0 left-0 mt-1 rounded-md shadow-lg ring-1 ring-black ring-opacity-5 divide-y divide-gray-200 focus:outline-none bg-gray-650" role="menu" aria-orientation="vertical" aria-labelledby="options-menu-button" tabindex="-1">
                  <div class="absolute top-0 right-0 -mr-14 p-1">
                    <button :click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar">
                      <Icon name="closemenu" />
                    </button>
                  </div>
                  <nav class="mt-5 px-2 space-y-1">
                    <ex-router-link :to="{ name: 'traders.edit', params: { id: sb_logged_user.trader.id } }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Στοιχεία μου
                    </ex-router-link>
                    <ex-router-link v-if="sb_logged_user.is_taxis_user" :to="{ name: 'acounters.edit', params: { id: sb_logged_user.acounter_id } }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Στοιχεία Taxis
                    </ex-router-link>
                    <ex-router-link v-if="sb_logged_user.is_taxis_user" :to="{ name: 'acounttraders' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Στοιχεία Πελατών για ΦΠΑ
                    </ex-router-link>
                    <ex-router-link v-if="sb_logged_user.is_erganh_user" :to="{ name: 'acounttraderserganh' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Στοιχεία Εταιρείων για Εργάνη
                    </ex-router-link>
                    <ex-router-link :to="{ name: 'users' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Βοηθοί λογιστή
                    </ex-router-link>
                    <ex-router-link v-if="sb_logged_user.is_erganh_user" :to="{ name: 'chfiakhmisuodosia' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Μισθοδοσία όλων
                    </ex-router-link>
                    <ex-router-link v-if="sb_logged_user.is_erganh_user" :to="{ name: 'pvlhthsregister' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Εγγραφή πελάτη στο {{$app_name}}
                    </ex-router-link>
                    <ex-router-link :to="{ name: 'mazikaemails' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
                      Μαζικά emails
                    </ex-router-link>
                    <ex-router-link :to="{ name: 'invoiceslist' ,params:{admin:0,type:'trader'}}" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                      Εκδοθέντα Τιμολόγια
                    </ex-router-link>
                    <div v-if="sb_logged_user.in_role_as>0">
                      <button class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150" href="#" @click.prevent="return_torole()">
                        <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        Επιστροφή στο ρόλο μου
                      </button>
                    </div>
                    <ActionButton :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
                  </nav>
                </div>
              </div>
            </div>
          </div>
        </transition>
      </div>
    </div>
    <!-- mobile menu Λογιστή end -->
    <!-- desktop Λογιστή start -->
    <div v-if="sb_logged_user.role_type == 10 || sb_logged_user.role_type == 12 " class="hidden md:flex">

      <div class="flex-1 flex flex-col pt-5 pb-4 overflow-y-auto bg-gray-800">
        <div class="flex items-center flex-shrink-0 ">
          <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
          <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
        </div>
        <div v-if="sb_logged_user.in_role_as>0 " class="flex flex-col items-center border">
          <div class="w-full text-center text-white">Για λογαριασμό: {{ sb_logged_user.trader.vat }}</div>
          <div class="w-full text-center text-white"> {{ sb_logged_user.trader.name }}</div>
        </div>
        <div class="px-3 mt-6 relative inline-block text-left">
          <button type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-white bg-gray-650 hover:bg-black focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
            <span class="flex w-full justify-between items-center">
              <span class="flex min-w-0 items-center justify-between space-x-3">
                <span class="flex-1 flex flex-col min-w-0">
                  <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                  <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                </span>
              </span>
              <!-- Heroicon name: solid/selector -->
            </span>
          </button>
        </div>
        <div v-if="sb_logged_user.is_in_pause ==1" class="flex-shrink-0 flex p-4">
          <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
            <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
              <span class="">ΣΕ ΔΙΑΚΟΠΗ ΛΕΙΤΤΟΥΡΓΙΑΣ</span>
            </div>
          </div>
        </div>
        <ex-router-link :to="{ name: 'traders.edit', params: { id: sb_logged_user.trader.id } }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
          Στοιχεία μου
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.is_taxis_user" :to="{ name: 'acounters.edit', params: { id: sb_logged_user.acounter_id } }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
          Στοιχεία Taxis
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.is_taxis_user" :to="{ name: 'acounttraders' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
          Στοιχεία Πελατών για ΦΠΑ
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.is_erganh_user" :to="{ name: 'acounttraderserganh' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
          Στοιχεία Εταιρείων για Εργάνη
        </ex-router-link>
        <ex-router-link :to="{ name: 'users' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
          Βοηθοί λογιστή
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.is_erganh_user" :to="{ name: 'chfiakhmisuodosia' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
          Μισθοδοσία όλων
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.is_erganh_user" :to="{ name: 'pvlhthsregister' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
          Εγγραφή πελάτη στο {{$app_name}}
        </ex-router-link>
        <ex-router-link :to="{ name: 'invoiceslist' ,params:{admin:0,type:'trader'}}" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4 hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
          Εκδοθέντα Τιμολόγια
        </ex-router-link>
        <div v-if="sb_logged_user.in_role_as>0">
          <button class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150" href="#" @click.prevent="return_torole()">
            <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
            Επιστροφή στο ρόλο μου
          </button>
        </div>
        <ActionButton :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
      </div>
    </div>
    <!-- desktop ΙΔΙΟΚΤΗΤΗ ΠΟΛΛΩΝ Βοηθός λογιστή  end -->

    <!-- mobile menu Αφεντικού-εργαζομένου start -->
    <div v-if="sb_logged_user.role_type ==7 || sb_logged_user.role_type ==8" class="md:hidden">
      <div class="fixed inset-0 flex z-40" v-show="sidebarMobile.open" :class="sidebarMobile.open ? '' : 'pointer-events-none'">
        <!-- Off-canvas menu overlay, show/hide based on off-canvas menu state. -->
        <transition enter-active-class="transition-opacity ease-linear duration-300" enter-class="opacity-0" enter-to-class="opacity-100" leave-active-class="transition-opacity ease-linear duration-300" leave-class="opacity-100" leave-to-class="opacity-0">
          <div @click="closeSidebar" class="fixed inset-0" v-show="sidebarMobile.open">
            <div class="absolute inset-0 bg-gray-600 opacity-75"></div>
          </div>
        </transition>

        <transition enter-active-class="transition ease-in-out duration-300 transform" enter-class="-translate-x-full" enter-to-class="translate-x-0" leave-active-class="transition ease-in-out duration-300 transform" leave-class="translate-x-0" leave-to-class="-translate-x-full">
          <div class="relative flex-1 flex flex-col max-w-xs w-full bg-gray-800" v-show="sidebarMobile.open">
            <div class="absolute top-0 right-0 -mr-14 p-1 bg-gray-800">
              <button @click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar">
                <Icon name="closemenu" />
              </button>
            </div>
            <div class="flex items-center flex-shrink-0 ">
              <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
              <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
            </div>

            <div class="px-3 mt-6 relative inline-block text-left bg-gray-800">
              <button type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-white bg-gray-650 hover:bg-gray-950 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
                <span class="flex w-full justify-between items-center">
                  <span class="flex min-w-0 items-center justify-between space-x-3">
                    <span class="flex-1 flex flex-col min-w-0">
                      <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                      <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                    </span>
                  </span>
                  <!-- Heroicon name: solid/selector -->
                </span>
              </button>
            </div>
            <ex-router-link v-if="sb_logged_user.id<7" :to="{ name: 'ananevseis' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
              Ανανεώσεις
            </ex-router-link>
            <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'banktransfer.create' ,params: { type: 1 } }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" id="options-menu-item-0">
              Μεταφορές
            </ex-router-link>
            <ex-router-link :to="{ name: 'invoiceslist' ,params:{admin:1}}" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-600 hover:bg-opacity-75 active:bg-gray-700 flex items-center px-2 py-2 text-sm font-medium rounded-md">
              <span class="flex-1">Ιστορικό Τιμολογίων </span>
            </ex-router-link>

            <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'traders' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" id="options-menu-item-0">
              Συνεργάτες
            </ex-router-link>
            <ex-router-link :to="{ name: 'companies' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
              Εταιρείες
            </ex-router-link>
            <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'cashdeskmove' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
              Ταμείο
            </ex-router-link>
            <div v-if="sb_logged_user.in_role_as>0">
              <button class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150" href="#" @click.prevent="return_torole()">
                <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                Επιστροφή στο ρόλο μου
              </button>
            </div>
            <ActionButton :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
          </div>
        </transition>
      </div>
    </div>
    <!-- mobile menu Αφεντικού-εργαζομένου end -->
    <!-- desktop menu Αφεντικού-εργαζομένου start -->
    <div v-if="sb_logged_user.role_type ==7 || sb_logged_user.role_type ==8" class="hidden md:flex md:flex-shrink-0">
      <div class="flex-1 flex flex-col pt-5 pb-4 overflow-y-auto bg-gray-800">
        <div class="flex items-center flex-shrink-0 ">
          <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
          <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
        </div>
        <div class="px-3 mt-6 relative inline-block text-left">
          <button type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-white bg-gray-650 hover:bg-gray-950 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
            <span class="flex w-full justify-between items-center">
              <span class="flex min-w-0 items-center justify-between space-x-3">
                <span class="flex-1 flex flex-col min-w-0">
                  <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                  <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                </span>
              </span>
              <!-- Heroicon name: solid/selector -->
            </span>
          </button>
        </div>

        <ex-router-link :to="{ name: 'contacts', params: { type: 0 } }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" id="options-menu-item-0">
          Απαντήσεις ερωτημάτων
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.id<7" :to="{ name: 'contacts', params: { type: 1 } }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" id="options-menu-item-0">
          Αιτήματα συνεργασίας
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.id<7" :to="{ name: 'ananevseis' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
          Ανανεώσεις
        </ex-router-link>
        <!--
          <ex-router-link :to="{ name: 'tempcompanies' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
          Συστάσεις που έχουν γίνει
        </ex-router-link>
-->
        <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'banktransfer.create' ,params: { type: 1 } }" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" id="options-menu-item-0">
          Μεταφορές
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'subscription.cancel' ,params: { type: 1 } }" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" id="options-menu-item-0">
          Ακυρώσεις
        </ex-router-link>

        <ex-router-link :to="{ name: 'invoiceslist' ,params:{admin:1}}" class="text-gray-100 hover:bg-gray-600 hover:bg-opacity-75 active:bg-gray-700 flex items-center px-2 py-2 text-sm font-medium rounded-md">
          <span class="flex-1">Ιστορικό Τιμολογίων </span>
        </ex-router-link>

        <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'users' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" id="options-menu-item-0">
          Χρήστες
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'traders' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" id="options-menu-item-0">
          Συνεργάτες
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.id<7" :to="{ name: 'mazikaemails' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md">
          Μαζικά emails
        </ex-router-link>

        <ex-router-link :to="{ name: 'companies' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
          Εταιρείες
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'dbcommands' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
          DB commands
        </ex-router-link>
        <button v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" @click.stop="admin_read_erganh()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
          Εισαγωγή από εργάνη
        </button>
        <div v-if="sb_logged_user.in_role_as>0">
          <button class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150" href="#" @click.prevent="return_torole()">
            <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
            Επιστροφή στο ρόλο μου
          </button>
        </div>
        <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'aade' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
          ΑΑΔΕ
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'expenses' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
          Ταμείο Εξόδων
        </ex-router-link>
        <ex-router-link v-if="sb_logged_user.id<7 && sb_logged_user.role_type == 8" :to="{ name: 'cashdeskmove' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1">
          Ταμείο
        </ex-router-link>
        <ActionButton :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>

      </div>
    </div>
    <!-- desktop menu Αφεντικού-εργαζομένου end -->

    <!-- mobile menu ERGANH my eraganh start -->
    <div v-if="sb_logged_user.role_type<=3 && sb_logged_user.domain==0" class="md:hidden">
      <!-- mobile menu -->

      <div class="fixed inset-0 flex z-40" v-show="sidebarMobile.open" :class="sidebarMobile.open ? '' : 'pointer-events-none'">
        <!-- Off-canvas menu overlay, show/hide based on off-canvas menu state. -->
        <transition enter-active-class="transition-opacity ease-linear duration-300" enter-class="opacity-0" enter-to-class="opacity-100" leave-active-class="transition-opacity ease-linear duration-300" leave-class="opacity-100" leave-to-class="opacity-0">
          <div @click="closeSidebar" class="fixed inset-0" v-show="sidebarMobile.open">
            <div class="absolute inset-0 bg-gray-600 opacity-75"></div>
          </div>
        </transition>

        <transition enter-active-class="transition ease-in-out duration-300 transform" enter-class="-translate-x-full" enter-to-class="translate-x-0" leave-active-class="transition ease-in-out duration-300 transform" leave-class="translate-x-0" leave-to-class="-translate-x-full">
          <div class="relative flex-1 flex flex-col max-w-xs w-full bg-gray-800" v-show="sidebarMobile.open">
            <div class="absolute top-0 right-0 -mr-14 p-1 ">
              <button @click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar">
                <Icon name="closemenu" />
              </button>
            </div>
            <div class="flex-1 h-0 pt-5 pb-4 overflow-y-auto ">
              <div class="flex items-center flex-shrink-0 ">
                <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
                <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
              </div>
              <div v-if="new_erganh_messages" class="flex flex-col items-center border">

                <button v-if="new_erganh_message.button && new_erganh_message.button!=''" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700" @click.prevent="shownees" :style="buttonStyle">
                  {{new_erganh_message.button}}
                </button>
                <div v-else class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700" :style="buttonStyle" v-html="new_erganh_message.title+'<br>'+new_erganh_message.message">
                </div>
              </div>
              <div v-if="sb_logged_user.in_role_as>0 " class="flex flex-col items-center border">
                <div class="w-full text-center text-white">Για λογαριασμό: {{ company.vat }}</div>
                <div class="w-full text-center text-white"> {{ company.name }}</div>

              </div>
              <div v-if="sb_logged_user.erganh_kvde_type < 0" class="flex-shrink-0 flex p-4 flex-col">
                <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                  <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                    <span class="">ΔΟΚΙΜΑΣΤΙΚΕΣ ΑΠΟΣΤΟΛΕΣ</span>
                  </div>
                </div>
                <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                  <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                    <span class="">{{timer_interval_count}}</span>
                  </div>
                </div>

                <div v-if="sb_logged_user.return_to_id>0 && demo_afm_ok==false && demo_afm_errors<5" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                  <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                    <span class="">ΑΦΜ:
                      <input type="text" class="" id="demo_afm" value="demo_afm" v-model="demo_afm" @keyup="sb_afmChange($event)" />
                    </span>
                  </div>
                </div>
                <div v-if="sb_logged_user.return_to_id>0 && demo_data  && demo_afm_errors<5" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                  <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                    <span class="">{{demo_data}}
                    </span>
                  </div>
                </div>
                <div v-if="sb_logged_user.return_to_id>0 && demo_afm_errors>=5" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                  <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                    <span class="">Πολλά λανθασμένα A.Φ.Μ
                    </span>
                  </div>
                </div>
              </div>

              <div v-if="sb_logged_user.role_type <= 3">
                <!-- normal user  sub menu-->
                <transition enter-active-class="transition ease-out duration-100" enter-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100" leave-active-class="transition ease-in duration-75" leave-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">
                  <div v-if="userMenuOpen" v-on:mouseleave="userMenuOpen = false" class="border border-gray-200 z-10 mx-3 origin-top absolute right-0 left-0 mt-1 rounded-md shadow-lg ring-1 ring-black ring-opacity-5 divide-y divide-gray-200 focus:outline-none bg-gray-650" role="menu" aria-orientation="vertical" aria-labelledby="options-menu-button" tabindex="-1">
                    <div class="absolute top-0 right-0 -mr-14 p-1">
                      <button @click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar">
                        <Icon name="closemenu" />
                      </button>
                    </div>
                    <div>
                      <ex-router-link v-if="sb_logged_user.role_type != 1" :to="{ name: 'submenu' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4" role="menuitem" tabindex="-1" id="options-menu-item-0" :class="{ 'pi_bg_lhjh text-gray-500   pointer-events-none': sb_logged_user.has_pay == 0 }">
                        <Icon name="othertasks" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        Λοιπές λειτουργίες
                      </ex-router-link>
                      <ex-router-link v-if="sb_logged_user.role_type != 1" :to="{ name: 'contactinapp' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4" role="menuitem" tabindex="-1" :class="{ 'pi_bg_lhjh text-gray-500   pointer-events-none': sb_logged_user.has_pay == 0 }">
                        <Icon name="communication" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        Επικοινωνία
                      </ex-router-link>
                      <ActionButton v-if="ask_erganh == false" :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
                    </div>
                  </div>
                </transition>
              </div>
              <!-- normal user sub menu button-->
              <nav class="mt-5 px-2 space-y-1">
                <div v-if="sb_logged_user.role_type <= 3" class="bg-gray-800">
                  <!-- normal user  button open menu -->
                  <button @click="userMenuOpen = !userMenuOpen" type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-gray-700 bg-gray-650 hover:bg-blue-100 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
                    <span class="flex w-full justify-between items-center">
                      <span class="flex min-w-0 items-center justify-between space-x-3">
                        <span class="flex-1 flex flex-col min-w-0">
                          <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                          <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                        </span>
                      </span>
                      <!-- Heroicon name: solid/selector -->
                      <Icon name="selector" class="flex-shrink-0 h-5 w-5 text-gray-400 group-hover:svg-pi-hover" />
                    </span>
                  </button>
                </div>
                <div v-else>
                  <!-- other  user  no sub menu button-->
                  <div class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-gray-700 bg-gray-650 hover:bg-blue-100 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
                    <span class="flex w-full justify-between items-center">
                      <span class="flex min-w-0 items-center justify-between space-x-3">
                        <span class="flex-1 flex flex-col min-w-0">
                          <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                          <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                        </span>
                      </span>
                    </span>
                  </div>
                </div>
                <div v-if="sb_logged_user.role_type <= 3">
                  <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1 && handleLinkShow(2)" :tooltip="getTooltipOptions(2)" :canclick="handleLinkClick(2)" :to="{  name: 'replacevresmet' }" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{ 'pi_bg_lhjh text-gray-500': handleLinkClick(2)==false}">
                    <Icon name="menu_forma" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Αποστολή μεταβολών ψηφιακού χρόνου
                  </ex-router-link>

                  <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1 && handleLinkShow(2)" :tooltip="getTooltipOptions(2)" :canclick="handleLinkClick(2)" :to="{ name: 'chfiakhmetfile' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_arxeio" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Μεταβαλλόμενο με αρχείο
                  </ex-router-link>
                  <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1 && handleLinkShow(2)" :tooltip="getTooltipOptions(2)" :canclick="handleLinkClick(2)" :to="{ name: 'replacevresmet' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_forma" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Μεταβαλλόμενο ατομικό με φόρμα
                  </ex-router-link>
                  <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1 && handleLinkShow(2)" :tooltip="getTooltipOptions(2)" :canclick="handleLinkClick(2)" :to="{ name: 'chfiakhstaufile' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_arxeio" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Σταθερό με αρχείο
                  </ex-router-link>
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'replacevresstau' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_forma" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Σταθερό ατομικό με φόρμα
                  </router-link>

                  <ex-router-link v-if="4==5 && sb_logged_user.role_type != 1" :to="{ name: 'employees' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh text-gray-500   pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_employees" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Εργαζόμενοι
                  </ex-router-link>
                  <ex-router-link v-if="ask_erganh == false && sb_logged_user.role_type != 1 && handleLinkShow(2)" :tooltip="getTooltipOptions(2)" :canclick="handleLinkClick(2)" :to="{ name: 'timetableschfiakh' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh text-gray-500': handleLinkClick(2)==false}">
                    <Icon name="menu_sendektakta" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Έλεγχος ψηφιακού ωραρίου
                  </ex-router-link>

                  <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type >= 1" :to="{ name: 'chfiakhmisuodosia' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh text-gray-500': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_misuodosia" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Μισθοδοσία
                  </ex-router-link>

                  <ex-router-link v-if="handleLinkShow(1) && company.has_chfiakh_organvsh==1" :tooltip="getTooltipOptions(1)" :canclick="handleLinkClick(1)" :to="{ name: 'tsekadoros' }" class="text-gray-100 hover:bg-gray-600 hover:bg-opacity-75 active:bg-gray-700 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh text-gray-500':handleLinkClick(1)==false}">
                    <Icon name="menu_tsekadoros" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    <span class="flex-1"> Υπεύθυνος Παρουσιών</span>
                  </ex-router-link>

                  <ex-router-link v-if="handleLinkShow(3)" :tooltip="getTooltipOptions(3)" :canclick="handleLinkClick(3)" :to="{ name: 'chfiakhcard' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh text-gray-500': handleLinkClick(3)==false}">
                    <Icon name="menu_tsekadoros" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Ψηφιακή Κάρτα
                  </ex-router-link>
                </div>
                <div v-if="sb_logged_user.in_role_as>0">
                  <button class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150" href="#" @click.prevent="return_torole()">
                    <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Επιστροφή στο ρόλο μου
                  </button>
                </div>
              </nav>
            </div>
            <div v-if="sb_logged_user.role_type <= 3 && company.has_chfiakh_organvsh==0" class="bg-red-600 p-4">
              Δεν έχετε Ψηφιακή οργάνωση ή δεν έχετε κανένα εργαζόμενο
            </div>
            <div v-if="sb_logged_user.role_type <= 3" class="bg-gray-800 p-4">

              <a href="#" class="flex-shrink-0 group block w-full focus:outline-none">
                <div class="flex items-center">
                  <div v-if="subscription.state == 'warn'" class="flex-shrink-0 flex w-full relative ">
                    <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-white">
                      <span class="">Κατάσταση συνδρομής</span>
                      <div class="">
                        <span>{{ subscription.description }}</span>
                        <Icon name="my_alarm" class="text-red-500 h-6 w-6 absolute right-3 top-50" />
                      </div>
                    </div>
                  </div>
                  <div v-if="subscription.state == 'error'" class="flex-shrink-0 w-full flex relative">
                    <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-white">
                      <span class="">Κατάσταση συνδρομής</span>
                      <div class="">
                        <span>{{ subscription.description }}</span>
                        <Icon name="my_alarm" class="text-red-500 h-6 w-6 absolute right-3 top-50" />
                      </div>
                    </div>
                  </div>
                </div>
              </a>
              <div v-if="subscription.state == 'warn' ||subscription.state == 'error' " class="py-1 bg-red-50" role="none" :class="{ 'bg-red-150': subscription.state == 'error' }">
                <ex-router-link v-if="sb_logged_user.in_role_as<=1" :to="{ name: 'payments' }" class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                  <Icon name="refresh_sub" class="mr-3 h-6 w-6 text-gray-400 group-hover:svg-pi-hover group-focus:text-gray-500 transition ease-in-out duration-150" />

                  Ανανέωση συνδρομής
                </ex-router-link>
              </div>
            </div>
          </div>
        </transition>
        <div class="flex-shrink-0 w-14">
          <!-- Force sidebar to shrink to fit close icon -->
        </div>
      </div>
    </div>
    <!-- mobile menu my ERGANH my eraganh end -->
    <!-- desktop menu ERGANH my eraganh start -->
    <div v-if="sb_logged_user.role_type<=3 && sb_logged_user.domain==0" class="hidden md:flex md:flex-shrink-0">
      <!--desctop menu -->
      <div class="flex flex-col w-64">
        <!-- Sidebar component, swap this element with another sidebar if you like -->
        <div class="flex flex-col h-0 flex-1 bg-white">
          <div class="flex-1 flex flex-col pt-5 pb-4 overflow-y-auto bg-gray-800">
            <div class="flex items-center flex-shrink-0 ">
              <img v-if="sb_logged_user.domain==0" class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο6" />
              <img v-else class="w-auto p-2 rounded bg-gray-500" src="/images/logo1.png" alt="Λογότυπο6" />
            </div>
            <div v-if="new_erganh_messages" class="flex flex-col items-center border">
              <button v-if="new_erganh_message.button && new_erganh_message.button!=''" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700" @click.prevent="shownees" :style="buttonStyle">
                {{new_erganh_message.button}}
              </button>
              <div v-else class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700" :style="buttonStyle" v-html="new_erganh_message.title+'<br>'+new_erganh_message.message">
              </div>
            </div>
            <div v-if="sb_logged_user.in_role_as>0 && sb_logged_user.erganh_kvde_type>=0" class="flex flex-col items-center border">
              <div class="w-full text-center text-white">Για λογαριασμό: {{ company.vat }}</div>
              <div class="w-full text-center text-white"> {{ company.name }}</div>
            </div>
            <div v-if="sb_logged_user.erganh_kvde_type < 0" class="flex-shrink-0 flex p-4 flex-col">
              <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">ΔΟΚΙΜΑΣΤΙΚΕΣ ΑΠΟΣΤΟΛΕΣ</span>
                </div>
              </div>
              <div v-if="timer_interval_count>=55" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">λήξη επίδειξης σε {{60-timer_interval_count}} λεπτά</span>
                </div>
              </div>
              <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div v-if="sb_logged_user.return_to_id>0 && demo_afm_ok==false  && demo_afm_errors<5" class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">ΑΦΜ πελάτη που κάνουμε επίδειξη:
                    <input type="text" class="" id="demo_afm" value="demo_afm" v-model="demo_afm" @keyup="sb_afmChange($event)" />
                  </span>
                </div>
              </div>
              <div v-if="sb_logged_user.return_to_id>0 && demo_data  && demo_afm_errors<5" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">{{demo_data}}
                  </span>
                </div>
              </div>
              <div v-if="sb_logged_user.return_to_id>0 && demo_afm_errors>=5" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">Πολλά λανθασμένα A.Φ.Μ
                  </span>
                </div>
              </div>
            </div>
            <div v-if="sb_logged_user.is_in_pause ==1" class="flex-shrink-0 flex p-4">
              <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">ΣΕ ΔΙΑΚΟΠΗ ΛΕΙΤΤΟΥΡΓΙΑΣ</span>
                </div>
              </div>
            </div>

            <div class="px-3 mt-6 relative inline-block text-left">
              <div v-if="sb_logged_user.role_type <= 3">
                <!-- normal user start -->
                <div>
                  <!--button -->
                  <button @click="userMenuOpen = !userMenuOpen" type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-white bg-gray-650 hover:bg-gray-950 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" :class="{ 'rounded-b-none bg-gray-950': userMenuOpen }" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
                    <span class="flex w-full justify-between items-center">
                      <span class="flex min-w-0 items-center justify-between space-x-3">
                        <span class="flex-1 flex flex-col min-w-0">
                          <span class="text-white text-sm font-medium truncate">{{
                              sb_logged_user.name
                            }}</span>
                          <span class="text-white text-sm font-medium truncate">{{
                              sb_logged_user.role_text
                            }}</span>
                        </span>
                      </span>
                      <!-- Heroicon name: solid/selector -->
                      <Icon name="selector" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    </span>
                  </button>
                </div>
                <!--sub menu start -->
                <transition enter-active-class="transition ease-out duration-100" enter-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100" leave-active-class="transition ease-in duration-75" leave-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">
                  <div v-if="userMenuOpen" v-on:mouseleave="userMenuOpen = false" class="absolute bg-gray-600 left-0 mx-3 origin-top right-0 rounded-b-md z-10" role="menu" aria-orientation="vertical" aria-labelledby="options-menu-button" tabindex="-1">
                    <div class="py-4 px-1 space-y-1" role="none">
                      <ex-router-link v-if="sb_logged_user.role_type != 1" :to="{ name: 'submenu' }" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" id="options-menu-item-0" :class="{ 'pi_bg_lhjh text-gray-500   pointer-events-none': sb_logged_user.has_pay == 0,}" @click.native="hide_mobile_menu()">
                        <Icon name="othertasks" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        <span class="flex-1"> Λοιπές λειτουργίες </span>
                      </ex-router-link>
                      <ex-router-link v-if="sb_logged_user.role_type == 3" :to="{ name: 'contactinapp' }" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" :class="{ 'pi_bg_lhjh text-gray-500   pointer-events-none': sb_logged_user.has_pay == 0, }" @click.native="hide_mobile_menu()">
                        <Icon name="communication" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        <span class="flex-1"> Επικοινωνία </span>
                      </ex-router-link>

                      <ActionButton v-if="ask_erganh == false" :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
                    </div>
                  </div>
                </transition>

                <!-- menu start -->
                <div class="mt-5 flex-1 space-y-1">
                  <div v-if="(is_in_tsekadoro==true || is_in_chfikh_karta==true) && company.tsekadoros_enabled_scan==1 && company.teskadoros_type_of_scan>0" class="w-full bg-white">
                    <div v-if="tsekadoros_branche_id>0" class="pt-2 pb-2 pl-2 pr-2">
                      <QRCode :do_html="company.qr_with_html==1" :need_init="parseInt(company.qr_with_capitals)" :a1="company.id" :a2="parseInt(tsekadoros_branche_id)" :a3="company.vat.slice(-2) + ''" :a4="client_ip" :a5="is_in_chfikh_karta"></QRCode>
                    </div>
                    <div v-else>Επιλέξτε υποκατάστημα για να φανεί το QR του</div>
                  </div>
                  <ex-router-link v-if="sb_logged_user.role_type != 1" :to="{ name: 'employees' }" class="text-gray-100 hover:bg-gray-600 hover:bg-opacity-75 active:bg-gray-700 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{ 'pi_bg_lhjh text-gray-500   pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_employees" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    <span class="flex-1"> Εργαζόμενοι </span>
                  </ex-router-link>
                  <div>
                    <!--button -->
                    <button @click="chfiakhMenuOpen = !chfiakhMenuOpen" type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-white bg-gray-650 hover:bg-gray-950 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" :class="{ 'rounded-b-none bg-gray-950': userMenuOpen }" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
                      <span class="flex w-full justify-between items-center">
                        <span class="flex min-w-0 items-center justify-between space-x-3">
                          <span class="flex-1 flex flex-col min-w-0">
                            Ψηφιακή οργάνωση
                          </span>
                        </span>
                        <!-- Heroicon name: solid/selector -->
                        <Icon name="selector" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                      </span>
                    </button>
                  </div>
                  <!--sub Ψηφιακή οργάνωση menu start -->
                  <transition enter-active-class="transition ease-out duration-100" enter-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100" leave-active-class="transition ease-in duration-75" leave-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">
                    <div v-if="chfiakhMenuOpen" v-on:mouseleave="chfiakhMenuOpen = false" class="absolute bg-gray-600 left-0 mx-3 origin-top right-0 rounded-b-md z-10" role="menu" aria-orientation="vertical" aria-labelledby="options-menu-button" tabindex="-1">
                      <div class="py-4 px-1 space-y-1" role="none">
                        <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1 && handleLinkShow(2)" :tooltip="getTooltipOptions(2)" :canclick="handleLinkClick(2)" :to="{ name: 'chfiakhmetfile' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                          <Icon name="menu_arxeio" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                          Μεταβαλλόμενο με αρχείο
                        </ex-router-link>
                        <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1 && handleLinkShow(2)" :tooltip="getTooltipOptions(2)" :canclick="handleLinkClick(2)" :to="{ name: 'replacevresmet' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                          <Icon name="menu_forma" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                          Μεταβαλλόμενο ατομικό με φόρμα
                        </ex-router-link>
                        <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1 && handleLinkShow(2)" :tooltip="getTooltipOptions(2)" :canclick="handleLinkClick(2)" :to="{ name: 'chfiakhstaufile' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                          <Icon name="menu_arxeio" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                          Σταθερό με αρχείο
                        </ex-router-link>
                        <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1 && handleLinkShow(2)" :tooltip="getTooltipOptions(2)" :canclick="handleLinkClick(2)" :to="{ name: 'replacevresstau' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                          <Icon name="menu_forma" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                          Σταθερό ατομικό με φόρμα
                        </ex-router-link>
                        <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1 && handleLinkShow(2)" :tooltip="getTooltipOptions(2)" :canclick="handleLinkClick(2)" :to="{ name: 'timetableschfiakh' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                          <Icon name="menu_elegxos" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                          Έλεγχος ψηφιακού ωραρίου
                        </ex-router-link>

                      </div>
                    </div>
                  </transition>

                  <ex-router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type >= 1 && handleLinkShow(7)" :tooltip="getTooltipOptions(7)" :canclick="handleLinkClick(7)" :to="{ name: 'chfiakhmisuodosia' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh text-gray-500': handleLinkClick(7)==false}">
                    <Icon name="menu_misuodosia" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Μισθοδοσία
                  </ex-router-link>

                  <ex-router-link v-if="handleLinkShow(1) && company.has_chfiakh_organvsh==1" :tooltip="getTooltipOptions(1)" :canclick="handleLinkClick(1)" :to="{ name: 'tsekadoros' }" class="text-gray-100 hover:bg-gray-600 hover:bg-opacity-75 active:bg-gray-700 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh text-gray-500':handleLinkClick(1)==false}">
                    <Icon name="menu_tsekadoros" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    <span class="flex-1"> Υπεύθυνος Παρουσιών</span>
                  </ex-router-link>
                  <ex-router-link v-if="handleLinkShow(3)" :tooltip="getTooltipOptions(3)" :canclick="handleLinkClick(3)" :to="{ name: 'chfiakhcard' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh text-gray-500': handleLinkClick(3)==false}">
                    <Icon name="menu_tsekadoros" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Ψηφιακή Κάρτα
                  </ex-router-link>

                  <button v-if="sb_logged_user.in_role_as>0" @click.prevent="return_torole()" class="text-gray-100 hover:bg-gray-600 hover:bg-opacity-75 active:bg-gray-700 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh text-gray-500  ': sb_logged_user.has_pay == 0}">
                    <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    <span class="flex-1">Επιστροφή στο ρόλο μου </span>
                  </button>
                  <ActionButton v-if="ask_erganh == false" :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
                </div>
                <!-- menu end -->
              </div>
              <!-- normal user end -->

            </div>
          </div>
        </div>

        <div v-if="ask_erganh == true" class="flex-shrink-0 flex border-t border-gray-200 relative bg-green-50">
          <div class="py-2 px-3.5 w-full flex-col text-sm leading-5 font-medium text-black">
            <span class="">ΕΙΣΑΓΩΓΗ ΑΠΟ ΕΡΓΑΝΗ</span>
            <div class="">
              <label class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">{{read_results_text1}}</label>
              <label class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">{{read_results_text2}}</label>
              <label class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">{{read_results_text3}}</label>
              <label class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">{{read_results_text4}}</label>
            </div>
          </div>
        </div>
        <div v-if="sb_logged_user.role_type <= 3 && company.has_chfiakh_organvsh==0" class="bg-red-600 p-4">
          Δεν έχετε Ψηφιακή οργάνωση ή δεν έχετε κανένα εργαζόμενο
        </div>
        <div v-if="sb_logged_user.role_type <= 3" class="bg-gray-800 p-4">
          <div v-if="subscription.state == 'warn'" class="flex-shrink-0 w-full flex relative">
            <div class="py-2 px-3.5 w-full flex-col text-sm leading-5 font-medium text-white">
              <span class="">Κατάσταση συνδρομής</span>
              <div class="">
                <span>{{ subscription.description }}</span>
                <Icon name="my_alarm" class="text-red-500 h-6 w-6 absolute right-3 top-50" />
              </div>
            </div>
          </div>
          <div v-if="subscription.state == 'error'" class="flex-shrink-0 flex w-full relative">
            <div class="py-2 px-3.5 w-full flex-col text-sm leading-5 font-medium text-white">
              <span class="">Κατάσταση συνδρομής</span>
              <div class="">
                <span>{{ subscription.description }}</span>
                <Icon name="my_alarm" class="text-red-500 h-6 w-6 absolute right-3 top-50" />
              </div>
            </div>
          </div>
          <div v-if="subscription.state == 'warn' ||subscription.state == 'error' " class="py-1 bg-red-50" role="none" :class="{ 'bg-red-150': subscription.state == 'error' }">
            <ex-router-link v-if="sb_logged_user.in_role_as<=1" :to="{ name: 'payments' }" class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
              <Icon name="refresh_sub" class="mr-3 h-6 w-6 text-gray-400 group-hover:svg-pi-hover group-focus:text-gray-500 transition ease-in-out duration-150" />
              Ανανέωση συνδρομής
            </ex-router-link>
          </div>
        </div>
      </div>
      <!--desctop menu end -->
    </div>
    <!-- desktop menu ERGANH my eraganh end -->
    <!-- mobile menu ERGANH eoraria start -->
    <div v-if="sb_logged_user.role_type<=3 && sb_logged_user.domain==1" class="md:hidden">
      <!-- mobile menu -->
      <div>xxxxxxxxxx{{sb_logged_user.domain}}</div>
      <div class="fixed inset-0 flex z-40" v-show="sidebarMobile.open" :class="sidebarMobile.open ? '' : 'pointer-events-none'">
        <!-- Off-canvas menu overlay, show/hide based on off-canvas menu state. -->
        <transition enter-active-class="transition-opacity ease-linear duration-300" enter-class="opacity-0" enter-to-class="opacity-100" leave-active-class="transition-opacity ease-linear duration-300" leave-class="opacity-100" leave-to-class="opacity-0">
          <div @click="closeSidebar" class="fixed inset-0" v-show="sidebarMobile.open">
            <div class="absolute inset-0 bg-gray-600 opacity-75"></div>
          </div>
        </transition>

        <transition enter-active-class="transition ease-in-out duration-300 transform" enter-class="-translate-x-full" enter-to-class="translate-x-0" leave-active-class="transition ease-in-out duration-300 transform" leave-class="translate-x-0" leave-to-class="-translate-x-full">
          <div class="relative flex-1 flex flex-col max-w-xs w-full bg-gray-800" v-show="sidebarMobile.open">
            <div class="absolute top-0 right-0 -mr-14 p-1 ">
              <button @click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar">
                <Icon name="closemenu" />
              </button>
            </div>
            <div class="flex-1 h-0 pt-5 pb-4 overflow-y-auto ">
              <div class="flex items-center flex-shrink-0 ">
                <img class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο" />
              </div>
              <div v-if="new_erganh_messages" class="flex flex-col items-center border">
                <button class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700" @click.prevent="shownees" :style="buttonStyle">
                  {{new_erganh_message.button}}
                </button>
              </div>
              <div v-if="sb_logged_user.in_role_as>0 " class="flex flex-col items-center border">
                <div class="w-full text-center text-white">Για λογαριασμό: {{ company.vat }}</div>
                <div class="w-full text-center text-white"> {{ company.name }}</div>

              </div>
              <div v-if="sb_logged_user.erganh_kvde_type < 0" class="flex-shrink-0 flex p-4 flex-col">
                <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                  <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                    <span class="">ΔΟΚΙΜΑΣΤΙΚΕΣ ΑΠΟΣΤΟΛΕΣ</span>
                  </div>
                </div>
                <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                  <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                    <span class="">{{timer_interval_count}}</span>
                  </div>
                </div>

                <div v-if="sb_logged_user.return_to_id>0 && demo_afm_ok==false && demo_afm_errors<5" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                  <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                    <span class="">ΑΦΜ:
                      <input type="text" class="" id="demo_afm" value="demo_afm" v-model="demo_afm" @keyup="sb_afmChange($event)" />
                    </span>
                  </div>
                </div>
                <div v-if="sb_logged_user.return_to_id>0 && demo_data  && demo_afm_errors<5" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                  <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                    <span class="">{{demo_data}}
                    </span>
                  </div>
                </div>
                <div v-if="sb_logged_user.return_to_id>0 && demo_afm_errors>=5" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                  <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                    <span class="">Πολλά λανθασμένα A.Φ.Μ
                    </span>
                  </div>
                </div>
              </div>

              <div v-if="sb_logged_user.role_type >= 1113">
                <!-- normal user  sub menu-->
                <transition enter-active-class="transition ease-out duration-100" enter-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100" leave-active-class="transition ease-in duration-75" leave-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">
                  <div v-if="userMenuOpen" v-on:mouseleave="userMenuOpen = false" class="border border-gray-200 z-10 mx-3 origin-top absolute right-0 left-0 mt-1 rounded-md shadow-lg ring-1 ring-black ring-opacity-5 divide-y divide-gray-200 focus:outline-none bg-gray-650" role="menu" aria-orientation="vertical" aria-labelledby="options-menu-button" tabindex="-1">
                    <div class="absolute top-0 right-0 -mr-14 p-1">
                      <button @click="closeSidebar" class="flex items-center justify-center h-12 w-12 rounded-full focus:outline-none focus:bg-gray-600" aria-label="Close sidebar">
                        <Icon name="closemenu" />
                      </button>
                    </div>
                    <div>
                      <router-link v-if="sb_logged_user.role_type != 1" :to="{ name: 'submenu' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4" role="menuitem" tabindex="-1" id="options-menu-item-0" :class="{ 'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0 }">
                        <Icon name="othertasks" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        Λοιπές λειτουργίες
                      </router-link>
                      <router-link v-if="sb_logged_user.role_type != 1" :to="{ name: 'contactinapp' }" @click.native="hide_mobile_menu()" class="group flex items-center text-white py-2 px-4" role="menuitem" tabindex="-1" :class="{ 'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0 }">
                        <Icon name="communication" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        Επικοινωνία
                      </router-link>
                      <ActionButton v-if="ask_erganh == false" :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
                    </div>
                  </div>
                </transition>
              </div>
              <!-- normal user sub menu button-->
              <nav class="mt-5 px-2 space-y-1">
                <div v-if="sb_logged_user.role_type <= 3" class="bg-gray-800">
                  <!-- normal user  button open menu -->
                  <button @click="userMenuOpen = !userMenuOpen" type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-gray-700 bg-gray-650 hover:bg-blue-100 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
                    <span class="flex w-full justify-between items-center">
                      <span class="flex min-w-0 items-center justify-between space-x-3">
                        <span class="flex-1 flex flex-col min-w-0">
                          <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                          <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                        </span>
                      </span>
                      <!-- Heroicon name: solid/selector -->
                      <Icon name="selector" class="flex-shrink-0 h-5 w-5 text-gray-400 group-hover:svg-pi-hover" />
                    </span>
                  </button>
                </div>
                <div v-else>
                  <!-- other  user  no sub menu button-->
                  <div class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-gray-700 bg-gray-650 hover:bg-blue-100 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
                    <span class="flex w-full justify-between items-center">
                      <span class="flex min-w-0 items-center justify-between space-x-3">
                        <span class="flex-1 flex flex-col min-w-0">
                          <span class="text-white text-sm font-medium truncate">{{sb_logged_user.name}}</span>
                          <span class="text-white text-sm font-medium truncate">{{sb_logged_user.role_text}}</span>
                        </span>
                      </span>
                    </span>
                  </div>
                </div>
                <div v-if="sb_logged_user.role_type <= 3">
                  <router-link v-if="sb_logged_user.role_type != 1" :to="{ name: 'employees' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_employees" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Εργαζόμενοι
                  </router-link>
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'chfiakhmetfile' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_arxeio" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Μεταβαλλόμενο με αρχείο
                  </router-link>
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'replacevresmet' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_forma" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Μεταβαλλόμενο ατομικό με φόρμα
                  </router-link>
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'chfiakhstaufile' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_arxeio" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Σταθερό με αρχείο
                  </router-link>
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'replacevresstau' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_forma" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Σταθερό ατομικό με φόρμα
                  </router-link>
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'timetableschfiakh' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_elegxos" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Έλεγχος ψηφιακού ωραρίου
                  </router-link>

                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'chfiakhmisuodosia' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_misuodosia" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Μισθοδοσία
                    <Icon v-if="application__of_customer==10" name="menu_locked" class="pl-1 flex-shrink-0 mr-1.5 h-5 w-5 text-various-yellow" />

                  </router-link>
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'xxxxxxx' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_ypervries" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Υπερωρίες
                  </router-link>

                  <router-link v-if="ask_erganh == false" :to="{ name: 'chfiakhcard' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_misuodosia" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Ψηφιακή κάρτα
                  </router-link>
                  <!--
                  <button @click="show_messages" v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_notes" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Σημειώσεις/Παρατηρήσεις
                  </button>
                  -->
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'contactinapp' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="communication" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Επικοινωνία
                  </router-link>
                  <a v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" @click="show_odhgies(true)" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="submenu_manual" class="mr-3 flex-shrink-0 h-6 w-6 text-gray-100" />

                    Βοήθεια
                  </a>

                </div>
                <div v-if="sb_logged_user.in_role_as>0">
                  <button class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150" href="#" @click.prevent="return_torole()">
                    <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Επιστροφή στο ρόλο μου
                  </button>
                </div>
              </nav>
            </div>
            <div v-if="sb_logged_user.role_type <= 3 && company.has_chfiakh_organvsh==0" class="bg-red-600 p-4">
              Δεν έχετε Ψηφιακή οργάνωση ή δεν έχετε κανένα εργαζόμενο
            </div>
            <div v-if="sb_logged_user.role_type <= 3" class="bg-gray-800 p-4">

              <a href="#" class="flex-shrink-0 group block w-full focus:outline-none">
                <div class="flex items-center">
                  <div v-if="subscription.state == 'warn'" class="flex-shrink-0 flex w-full relative ">
                    <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-white">
                      <span class="">Κατάσταση συνδρομής</span>
                      <div class="">
                        <span>{{ subscription.description }}</span>
                        <Icon name="my_alarm" class="text-red-500 h-6 w-6 absolute right-3 top-50" />
                      </div>
                    </div>
                  </div>
                  <div v-if="subscription.state == 'error'" class="flex-shrink-0 w-full flex relative">
                    <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-white">
                      <span class="">Κατάσταση συνδρομής</span>
                      <div class="">
                        <span>{{ subscription.description }}</span>
                        <Icon name="my_alarm" class="text-red-500 h-6 w-6 absolute right-3 top-50" />
                      </div>
                    </div>
                  </div>
                </div>
              </a>
              <div v-if="subscription.state == 'warn' ||subscription.state == 'error' " class="py-1 bg-red-50" role="none" :class="{ 'bg-red-150': subscription.state == 'error' }">
                <router-link v-if="sb_logged_user.in_role_as<=1" :to="{ name: 'payments' }" class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
                  <Icon name="refresh_sub" class="mr-3 h-6 w-6 text-gray-400 group-hover:svg-pi-hover group-focus:text-gray-500 transition ease-in-out duration-150" />

                  Ανανέωση συνδρομής
                </router-link>
              </div>
            </div>
          </div>
        </transition>
        <div class="flex-shrink-0 w-14">
          <!-- Force sidebar to shrink to fit close icon -->
        </div>
      </div>
    </div>
    <!-- mobile menu ERGANH eoraria end -->
    <!-- desktop menu ERGANH eoraria start -->
    <div v-if="sb_logged_user.role_type<=3 && sb_logged_user.domain==1" class="hidden md:flex md:flex-shrink-0">
      <!--desctop menu -->
      <div class="flex flex-col w-64">
        <!-- Sidebar component, swap this element with another sidebar if you like -->
        <div class="flex flex-col h-0 flex-1 bg-white">
          <div class="flex-1 flex flex-col pt-5 pb-4 overflow-y-auto bg-gray-800">
            <div class="flex items-center flex-shrink-0 ">
              <img class="w-auto p-2 rounded bg-gray-500" src="/images/logo.png" alt="Λογότυπο" />
            </div>
            <div v-if="new_erganh_messages" class="flex flex-col items-center border">
              <button class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700" @click.prevent="shownees" :style="buttonStyle">
                {{new_erganh_message.button}}
              </button>
            </div>
            <div v-if="sb_logged_user.in_role_as>0 && sb_logged_user.erganh_kvde_type>=0" class="flex flex-col items-center border">
              <div class="w-full text-center text-white">Για λογαριασμό: {{ company.vat }}</div>
              <div class="w-full text-center text-white"> {{ company.name }}</div>
            </div>
            <div v-if="sb_logged_user.erganh_kvde_type < 0" class="flex-shrink-0 flex p-4 flex-col">
              <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">ΔΟΚΙΜΑΣΤΙΚΕΣ ΑΠΟΣΤΟΛΕΣ</span>
                </div>
              </div>
              <div v-if="timer_interval_count>=55" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">λήξη επίδειξης σε {{60-timer_interval_count}} λεπτά</span>
                </div>
              </div>
              <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div v-if="sb_logged_user.return_to_id>0 && demo_afm_ok==false  && demo_afm_errors<5" class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">ΑΦΜ πελάτη που κάνουμε επίδειξη:
                    <input type="text" class="" id="demo_afm" value="demo_afm" v-model="demo_afm" @keyup="sb_afmChange($event)" />
                  </span>
                </div>
              </div>
              <div v-if="sb_logged_user.return_to_id>0 && demo_data  && demo_afm_errors<5" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">{{demo_data}}
                  </span>
                </div>
              </div>
              <div v-if="sb_logged_user.return_to_id>0 && demo_afm_errors>=5" class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">Πολλά λανθασμένα A.Φ.Μ
                  </span>
                </div>
              </div>
            </div>
            <div v-if="sb_logged_user.is_in_pause ==1" class="flex-shrink-0 flex p-4">
              <div class="flex-shrink-0 w-full flex border-t border-gray-200 relative bg-red-700">
                <div class="py-2 px-3.5 flex-col text-sm leading-5 w-full font-medium text-black ">
                  <span class="">ΣΕ ΔΙΑΚΟΠΗ ΛΕΙΤΤΟΥΡΓΙΑΣ</span>
                </div>
              </div>
            </div>

            <div class="px-3 mt-6 relative inline-block text-left">
              <div v-if="sb_logged_user.role_type <= 3">
                <!-- normal user start -->
                <div>
                  <!--button -->
                  <button @click="userMenuOpen = !userMenuOpen" type="button" class="group w-full rounded-md px-3.5 py-2 text-sm text-left font-medium text-white bg-gray-650 hover:bg-gray-950 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-purple-500" :class="{ 'rounded-b-none bg-gray-950': userMenuOpen }" id="options-menu-button" aria-expanded="false" aria-haspopup="true">
                    <span class="flex w-full justify-between items-center">
                      <span class="flex min-w-0 items-center justify-between space-x-3">
                        <span class="flex-1 flex flex-col min-w-0">
                          <span class="text-white text-sm font-medium truncate">{{
                              sb_logged_user.name
                            }}</span>
                          <span class="text-white text-sm font-medium truncate">{{
                              sb_logged_user.role_text
                            }}</span>
                        </span>
                      </span>
                      <!-- Heroicon name: solid/selector -->
                      <Icon name="selector" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    </span>
                  </button>
                </div>
                <!--sub menu start -->
                <transition enter-active-class="transition ease-out duration-100" enter-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100" leave-active-class="transition ease-in duration-75" leave-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">
                  <div v-if="userMenuOpen" v-on:mouseleave="userMenuOpen = false" class="absolute bg-gray-600 left-0 mx-3 origin-top right-0 rounded-b-md z-10" role="menu" aria-orientation="vertical" aria-labelledby="options-menu-button" tabindex="-1">
                    <div class="py-4 px-1 space-y-1" role="none">
                      <router-link v-if="sb_logged_user.role_type != 1" :to="{ name: 'submenu' }" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" id="options-menu-item-0" :class="{ 'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0,}" @click.native="hide_mobile_menu()">
                        <Icon name="othertasks" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        <span class="flex-1"> Λοιπές λειτουργίες </span>
                      </router-link>
                      <router-link v-if="sb_logged_user.role_type == 3" :to="{ name: 'contactinapp' }" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" role="menuitem" tabindex="-1" :class="{ 'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0, }" @click.native="hide_mobile_menu()">
                        <Icon name="communication" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                        <span class="flex-1"> Επικοινωνία </span>
                      </router-link>

                      <ActionButton v-if="ask_erganh == false" :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
                    </div>
                  </div>
                </transition>

                <!-- menu start -->
                <div class="mt-5 flex-1 space-y-1">
                  <router-link v-if="sb_logged_user.role_type != 1" :to="{ name: 'employees' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_employees" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    Εργαζόμενοι
                  </router-link>
                  <fieldset class="border">
                    <legend class="flex text-center text-gray-100">
                      <Icon name="menu_sendektakta" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />Ψηφιακή οργάνωση
                    </legend>
                    <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'chfiakhmetfile' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                      <Icon name="menu_arxeio" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                      Μεταβαλλόμενο με αρχείο
                    </router-link>
                    <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'replacevresmet' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                      <Icon name="menu_forma" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                      Μεταβαλλόμενο ατομικό με φόρμα
                    </router-link>
                    <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'chfiakhstaufile' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                      <Icon name="menu_arxeio" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                      Σταθερό με αρχείο
                    </router-link>
                    <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'replacevresstau' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                      <Icon name="menu_forma" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                      Σταθερό ατομικό με φόρμα
                    </router-link>
                    <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'timetableschfiakh' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                      <Icon name="menu_elegxos" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                      Έλεγχος ψηφιακού ωραρίου
                    </router-link>
                  </fieldset>
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'chfiakhmisuodosia' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_misuodosia" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Μισθοδοσία
                    <Icon v-if="application__of_customer==10" name="menu_locked" class="pl-1 flex-shrink-0 mr-1.5 h-5 w-5 text-various-yellow" />
                  </router-link>
                  <fieldset v-if="sb_logged_user.role_type >= 0" class="border">
                    <legend class="flex text-center text-gray-100">
                      <Icon name="menu_sendektakta" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />Ψηφιακή κάρτα
                    </legend>
                    <router-link v-if="ask_erganh == false" :to="{ name: 'chfiakhcard' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                      <Icon name="menu_misuodosia" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                      Ενημέρωση
                    </router-link>

                  </fieldset>
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'xxxxxxxx' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_ypervries" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Υπερωρίες
                    <Icon v-if="application_of_customer==10" name="menu_locked" class="pl-1 flex-shrink-0 mr-1.5 h-5 w-5 text-various-yellow" />
                  </router-link>
                  <!--
                    <button @click="show_messages" v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="menu_notes" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Σημειώσεις/Παρατηρήσεις
                  </button>
-->
                  <router-link v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" :to="{ name: 'contactinapp' }" @click.native="hide_mobile_menu()" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="communication" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />

                    Επικοινωνία
                  </router-link>
                  <a v-if="company.has_chfiakh_organvsh==1 && ask_erganh == false && sb_logged_user.role_type != 1" @click="show_odhgies(true)" class="text-gray-100 hover:bg-gray-700 hover:bg-opacity-75 active:bg-gray-800 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh pointer-events-none': sb_logged_user.has_pay == 0}">
                    <Icon name="submenu_manual" class="mr-3 flex-shrink-0 h-6 w-6 text-gray-100" />

                    Βοήθεια
                  </a>
                  <button v-if="sb_logged_user.in_role_as>0" @click.prevent="return_torole()" class="text-gray-100 hover:bg-gray-600 hover:bg-opacity-75 active:bg-gray-700 flex items-center px-2 py-2 text-sm font-medium rounded-md" :class="{'pi_bg_lhjh': sb_logged_user.has_pay == 0}">
                    <Icon name="returntorole" class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-100" />
                    <span class="flex-1">Επιστροφή στο ρόλο μου </span>
                  </button>
                  <ActionButton v-if="ask_erganh == false" :onClick="sendLogout" type="menu" icon="disconnect">Αποσύνδεση</ActionButton>
                </div>
                <!-- menu end -->
              </div>
              <!-- normal user end -->

            </div>
          </div>
        </div>

        <div v-if="ask_erganh == true" class="flex-shrink-0 flex border-t border-gray-200 relative bg-green-50">
          <div class="py-2 px-3.5 w-full flex-col text-sm leading-5 font-medium text-black">
            <span class="">ΕΙΣΑΓΩΓΗ ΑΠΟ ΕΡΓΑΝΗ</span>
            <div class="">
              <label class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">{{read_results_text1}}</label>
              <label class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">{{read_results_text2}}</label>
              <label class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">{{read_results_text3}}</label>
              <label class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">{{read_results_text4}}</label>
            </div>
          </div>
        </div>
        <div v-if="sb_logged_user.role_type <= 3 && company.has_chfiakh_organvsh==0" class="bg-red-600 p-4">
          Δεν έχετε Ψηφιακή οργάνωση ή δεν έχετε κανένα εργαζόμενο
        </div>
        <div v-if="sb_logged_user.role_type <= 3" class="bg-gray-800 p-4">
          <div v-if="subscription.state == 'warn'" class="flex-shrink-0 w-full flex relative">
            <div class="py-2 px-3.5 w-full flex-col text-sm leading-5 font-medium text-white">
              <span class="">Κατάσταση συνδρομής</span>
              <div class="">
                <span>{{ subscription.description }}</span>
                <Icon name="my_alarm" class="text-red-500 h-6 w-6 absolute right-3 top-50" />
              </div>
            </div>
          </div>
          <div v-if="subscription.state == 'error'" class="flex-shrink-0 flex w-full relative">
            <div class="py-2 px-3.5 w-full flex-col text-sm leading-5 font-medium text-white">
              <span class="">Κατάσταση συνδρομής</span>
              <div class="">
                <span>{{ subscription.description }}</span>
                <Icon name="my_alarm" class="text-red-500 h-6 w-6 absolute right-3 top-50" />
              </div>
            </div>
          </div>
          <div v-if="subscription.state == 'warn' ||subscription.state == 'error' " class="py-1 bg-red-50" role="none" :class="{ 'bg-red-150': subscription.state == 'error' }">
            <router-link v-if="sb_logged_user.in_role_as<=1" :to="{ name: 'payments' }" class="group flex items-center px-2 py-2 text-sm leading-5 font-medium text-gray-600 rounded-md hover:text-gray-900 hover:bg-gray-50 focus:outline-none focus:text-gray-900 focus:bg-gray-50 transition ease-in-out duration-150">
              <Icon name="refresh_sub" class="mr-3 h-6 w-6 text-gray-400 group-hover:svg-pi-hover group-focus:text-gray-500 transition ease-in-out duration-150" />
              Ανανέωση συνδρομής
            </router-link>
          </div>
        </div>
      </div>
      <!--desctop menu end -->
    </div>
    <!-- desktop menu ERGANH eoraria end -->
  </div>
</template>

<script>
import { mapState, mapActions, mapMutations } from "vuex";
import AnalogDifClock from './AnalogDifClock.vue';
import QRCode from './DynamicQrCode.vue';
import { SIDEBAR_CANCLICK_MENU } from '../externals.js'
import { SIDEBAR_TOOLTIP_TEXT } from '../externals.js'
export default {
  components: { AnalogDifClock, QRCode, },
  open: false,
  data: function () {
    return {
      demo_afm_errors: 0,
      demo_afm: '',
      demo_afm_ok: false,
      demo_data: null,
      branch: {},
      userMenuOpen: false,
      chfiakhMenuOpen: false,
      subscription: {
        state: "normal",
        description: "Κανονική",
      },
      timer_interval: null,
      timer_interval_count: 0,
      flash_mode: 0,

    };
  },
  computed: {
    ...mapState({
      ask_erganh: (state) => state.Sidebar.ask_erganh,
      client_ip: (state) => state.Sidebar.client_ip,
      company: (state) => state.Sidebar.company,
      app_name: (state) => state.Sidebar.app_name,
      application_of_customer: (state) => state.Sidebar.application_of_customer,
      company_has_chfiakh_karta: (state) => state.Sidebar.company_has_chfiakh_karta,
      new_erganh_messages: (state) => state.Sidebar.new_erganh_messages,
      new_erganh_message: (state) => state.Sidebar.new_erganh_message,
      is_in_tsekadoro: (state) => state.Sidebar.is_in_tsekadoro,
      is_in_chfikh_karta: (state) => state.Sidebar.is_in_chfikh_karta,
      tsekadoros_branche_id: (state) => state.Sidebar.tsekadoros_branche_id,
      is_employee: (state) => state.Sidebar.is_employee,
      for_employee_id: (state) => state.Sidebar.for_employee_id,

      sb_logged_user: (state) => state.Sidebar.sb_logged_user,
      messages_visible: (state) => state.Sidebar.messages_visible,

      read_results_text1: (state) => state.Sidebar.read_results_text1,
      read_results_text2: (state) => state.Sidebar.read_results_text2,
      read_results_text3: (state) => state.Sidebar.read_results_text3,
      read_results_text4: (state) => state.Sidebar.read_results_text4,
      sidebarMobile: (state) => state.Sidebar,
    }),
    buttonStyle() {
      if (this.flash_mode == 0) return this.new_erganh_message.style1;
      return this.new_erganh_message.style2;
    },
  },

  created() {
    this.unsubscribe = this.$store.subscribe((mutation, state) => {
      if (mutation.type === "UPDATE_SB_LOGGED_USER") {
        if (!this.sb_logged_user) {
          return;
        }
        const daysLeft = parseInt(this.sb_logged_user.days_to_pay);

        if (daysLeft <= 5 && this.sb_logged_user.has_pay != 0) {
          this.subscription.state = "warn";
          switch (daysLeft) {
            case 0:
              this.subscription.description = "Λήγει σήμερα";
              break;
            case 1:
              this.subscription.description = "Λήγει αύριο";
              break;
            default:
              this.subscription.description = "Λήγει σε " + daysLeft + " μέρες";
              break;
          }
        }
        if (this.sb_logged_user.has_pay == 0) {
          this.subscription.description = "Έχει λήξει";
          this.subscription.state = "error";
        }
      }
    });
    var self = this;
    this.FETCH_SB_LOGGED_USER("?sb_init=1").then(data => {
      if (self.sb_logged_user.erganh_kvde_type < 0) {
        if (self.sb_logged_user.return_to_id > 0) {
          self.strat_epideijh_timer();
        }
      }
      if (this.sb_logged_user.redirect && this.sb_logged_user.redirect != "") {
        if (this.$route.name != this.sb_logged_user.redirect) {
          this.$router.push(this.sb_logged_user.redirect);
        }
      }
      if (this.new_erganh_messages) this.flashnees()
    });
  },

  methods: {
    ...mapActions([
      "CLOSE_SIDEBAR",
      "FETCH_SB_LOGGED_USER",
      "FETCH_LOGOUT_USER",
      "FETCH_REGISTER_USER",
      "FETCH_SHOW_READ_ERGANH",
      "SHOW_GENERAL_DIALOG",
      "SHOW_ODHGIES",
      "RETURN_TO_ROLE",
      "FETCH_SB_VALIDATE_VAT",
      "COMPANIES_RUN_AS",
      "DEMO_TIMEOUT_LOGOUT"

    ]),
    ...mapActions(["SHOW_MESSAGES"]),
    ...mapMutations(["UPDATE_SB_LOGGED_USER", "UPDATE_SB_READ_STATUS", "UPDATE_SB_READ_STATUS_TEXT"]),
    getTooltipOptions(roleType) {
      var data = [roleType, this.sb_logged_user, this.company], ret = "";
      return SIDEBAR_TOOLTIP_TEXT(data);
    },
    handleLinkShow(roleType) {
      if (this.company.hide_unused_menus == 0) return true;
      var data = [roleType, this.sb_logged_user, this.company], ret;
      ret = SIDEBAR_CANCLICK_MENU(data);
      return ret;
    },
    handleLinkClick(roleType) {
      var data = [roleType, this.sb_logged_user, this.company], ret;
      var data = [roleType, this.sb_logged_user, this.company,]
      return (SIDEBAR_CANCLICK_MENU(data));
    },
    strat_epideijh_timer() {
      var self = this;
      self.timer_interval_count = 0;
      self.timer_interval = setInterval(() => {
        self.timer_interval_count++;
        if (self.timer_interval_count >= 60) {
          clearInterval(self.timer_interval)
          self.timer_interval = null;
          self.DEMO_TIMEOUT_LOGOUT(0)
          self.return_torole();
        }
        if (self.timer_interval_count == 55) {
          self.DEMO_TIMEOUT_LOGOUT(280)
        }
      }, 60000)

    },
    sb_afmChange(evt) {
      if (evt.keyCode == 27) {
        this.demo_afm = "";
        this.demo_data = null;
        return;
      }
      if (evt.keyCode != 13) {
        return;
      }
      if (this.demo_afm_ok == false) {
        var vat = this.demo_afm, ln = vat.length;
        if (ln != 9) return;
        this.demo_data = '...';
        var data = "?uid=" + this.sb_logged_user.id + "&vat=" + vat;
        this.FETCH_SB_VALIDATE_VAT(data).then(response => {
          if (response) {
            this.demo_data = response.ans;
            this.demo_afm_ok = response.ok;
            if (!response.ok) this.demo_afm_errors++;
          }
        }

        )
      }
    },
    traders_pvlhths_plhrvmes() {
      this.$router.push({ name: "pvlhthsplhrvmes", params: { id: this.sb_logged_user.trader.id } }).catch(error => {
        if (error.name != "NavigationDuplicated") {
          throw error;
        }
      });

    },
    sb_do_register() {
      this.userMenuOpen = false;
      this.open = false;

      this.CLOSE_SIDEBAR();
      this.FETCH_REGISTER_USER(this).then(response => {
        //        window.open("https://www.codegrepper.com/code-examples/javascript/vue+js+redirect+to+external+url+new+tab", '_blank');
        var page = response.page;
        var route = this.$router.resolve({ path: page })
        window.open(route.href, '_blank');
        if (response) {
          this.$router.push(response.page).then(() => {
            this.$router.go();
          });
        }
      });

      //pierganh.loc/register
    },

    sb_run_as_role() {
      var self = this;

      var data = [this, 1, -99, ''];

      this.COMPANIES_RUN_AS(data);
      this.strat_epideijh_timer();
      return;
    },
    return_torole() {
      if (this.timer_interval) {
        clearInterval(this.timer_interval)
        this.timer_interval = null;
      }
      this.FETCH_SB_LOGGED_USER("?sb_return=" + this.sb_logged_user.return_to_id).then(
        () => {
          if (this.$route.name != this.sb_logged_user.redirect)
            this.$router.push(this.sb_logged_user.redirect);
          this.hide_mobile_menu();
        }
      );
    },
    test_mazika_emails() {
    },
    show_symbaseis_analytika(is_for_lauh) {
      if (this.sb_logged_user.role_type == 1) {
        this.sb_logged_user.symbaseis_alarm = 0;
        return;
      }
      if (this.$route.name == "timetableschfiakh") {
        this.$router.go({ path: "/timetableschfiakh", query: { lauh: is_for_lauh } })
          .catch(error => {
            if (error.name != "NavigationDuplicated") {
              throw error;
            }
          });
      }
      else {
        this.$router.push({ name: "timetableschfiakh", params: { lauh: is_for_lauh } }).catch(error => {
          if (error.name != "NavigationDuplicated") {
            throw error;
          }
        });
      }
    },
    show_odhgies(moblie) {
      this.SHOW_ODHGIES();
    },
    sendLogout() {
      this.userMenuOpen = false;
      this.open = false;
      if (this.timer_interval) {
        clearInterval(this.timer_interval)
        this.timer_interval = null;
      }
      this.CLOSE_SIDEBAR();
      this.FETCH_LOGOUT_USER(this).then(() => {
        this.$router.push("web/login").then(() => {
          this.$router.go();
        });
      });
    },
    closeSidebar: function () {
      //      this.open = false;
      //      this.userMenuOpen = false;
      this.CLOSE_SIDEBAR();
    },
    set_ask_erganh(v) {
      this.UPDATE_SB_READ_STATUS(v);
    },
    flashnees() {
      var toggleSidebar_button = document.getElementById("toggleSidebar_button_id");
      var self = this;

      self.flash_mode = 0
      self.flashtimer = setInterval(() => {
        if (self.flash_mode == 0) {
          self.flash_mode = 1
        }
        else {
          self.flash_mode = 0;
        }
        if (toggleSidebar_button) {
          if (this.flash_mode == 0) toggleSidebar_button.style.backgroundColor = self.new_erganh_message.mobile_style1;
          else toggleSidebar_button.style.backgroundColor = self.new_erganh_message.mobile_style2;

        }


      }, this.new_erganh_message.flash_time_ms)
    },
    shownees() {
      var type = this.new_erganh_message.type;
      var acontent = this.new_erganh_message.message.split("<br>");
      var title = this.new_erganh_message.title;
      if (!title || title == "") title = "Νέες δυνατότητες";
      this.$dialog({
        title: title,
        content: acontent,
        delay: 0, //options, close after 20s
        btns: [
          {
            label: "OK",
            color: "#09f",
          },
        ],
        error_count: 0,
      });
      return;

    },
    readErganh() {
      if (this.ask_erganh == true) {
        var acontent = [];
        acontent.push("'Εχετε ζητήσει ήδη εισαγωγή από ΕΡΓΑΝΗ που δεν έχει ολοκληρωθεί");
        acontent.push("Εσεις μπορείτε να συνεχίσετε να εργάζεστε ");
        acontent.push("και θα ενημερωθείτε μόλις τελειώσει με μήνυμα");
        this.$dialog({
          title: "Εισαγωγή στοιχείων από ΕΡΓΑΝΗ",
          content: acontent,
          delay: 0, //options, close after 20s
          btns: [
            {
              label: "OK",
              color: "#09f",
            },
          ],
          error_count: 1,
        });
        return;
      }
      this.userMenuOpen = false;
      this.open = false;
      this.CLOSE_SIDEBAR();
      this.FETCH_SHOW_READ_ERGANH(this);
    },
    admin_read_erganh() {
      this.open = false;
      this.CLOSE_SIDEBAR();
      this.hide_mobile_menu()
      this.FETCH_SHOW_READ_ERGANH(this);
    },
    hide_mobile_menu() {
      this.userMenuOpen = false;
      this.open = false;
      this.CLOSE_SIDEBAR();
    },
  },
  beforeDestroy() {
    this.unsubscribe();
  },
};
</script>

<style lang="scss" scoped>
.ex-router-link-active {
  @apply bg-gray-900 text-white;
}
</style>