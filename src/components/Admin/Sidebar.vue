<template>
  <div class="relative">
    <!-- Mobile Toggle Button -->
    <button
      @click="toggleSidebar"
      class="fixed z-50 p-2 text-white rounded-lg md:hidden top-4 left-4 bg-emerald-600 hover:bg-emerald-700 focus:outline-none"
      aria-label="Toggle Menu"
    >
      <i :class="['fas', isSidebarOpen ? 'fa-times' : 'fa-bars']"></i>
    </button>

    <!-- Sidebar -->
    <aside
      class="fixed inset-y-0 left-0 z-40 flex flex-col h-full transition-transform duration-300 transform bg-gray-50 border-r md:translate-x-0"
      :class="[
        isSidebarOpen ? 'translate-x-0' : '-translate-x-full',
        'w-64 xl:w-72',
      ]"
    >
      <!-- Logo Section -->
      <div class="p-4 space-y-4">
       
        <h2 class="text-lg font-bold text-center text-gray-800">
          Congrès NDOGBATJECK
        </h2>
        <div
          class="w-24 h-1 mx-auto rounded-full bg-gradient-to-r from-emerald-500 to-green-500"
        ></div>
      </div>

      <!-- Navigation -->
      <nav class="flex-1 px-4 pb-4 mt-5 overflow-y-auto">
        <ul class="space-y-4">
          <!-- Dashboard de Suivi -->
          <li>
            <h3
              class="px-2 font-semibold text-gray-700 uppercase cursor-pointer flex items-center space-x-2"
              @click="toggleSection('dashboard')"
            >
             <i class="fas fa-tachometer-alt"></i>
              <span>Dashboard de Suivi</span>
            </h3>
            <ul v-if="sectionsOpen.dashboard" class="space-y-2">
              <li v-for="item in dashboardItems" :key="item.path">
                <router-link
                  :to="item.path"
                  class="flex items-center px-4 py-3 space-x-3 transition-colors duration-200 rounded-lg group hover:bg-emerald-50"
                  :class="{
                    'bg-emerald-100 text-emerald-600': $route.path === item.path,
                  }"
                >
                  <div
                    class="flex items-center justify-center w-10 h-10 transition-colors duration-200 rounded-lg"
                    :class="[
                      $route.path === item.path
                        ? 'bg-emerald-200'
                        : 'bg-gray-100 group-hover:bg-emerald-100',
                    ]"
                  >
                    <i :class="[item.icon, 'text-lg']"></i>
                  </div>
                  <span class="font-medium">{{ item.name }}</span>
                </router-link>
              </li>
            </ul>
          </li>
          <!-- Administration Contenus -->
          <li>
            <h3
             class="px-2 font-semibold text-gray-700 uppercase cursor-pointer flex items-center space-x-2"
              @click="toggleSection('adminContenu')"
            >
               <i class="fas fa-folder-open"></i>
              <span>Administration Contenus</span>
            </h3>
            <ul v-if="sectionsOpen.adminContenu" class="space-y-2">
                <li v-for="item in adminContenuItems" :key="item.path">
                 <router-link
                  :to="item.path"
                  class="flex items-center px-4 py-3 space-x-3 transition-colors duration-200 rounded-lg group hover:bg-emerald-50"
                    :class="{
                      'bg-emerald-100 text-emerald-600': $route.path === item.path,
                    }"
                >
                  <div
                    class="flex items-center justify-center w-10 h-10 transition-colors duration-200 rounded-lg"
                    :class="[
                      $route.path === item.path
                        ? 'bg-emerald-200'
                        : 'bg-gray-100 group-hover:bg-emerald-100',
                    ]"
                  >
                    <i :class="[item.icon, 'text-lg']"></i>
                  </div>
                    <span class="font-medium">{{ item.name }}</span>
                  </router-link>
                </li>
              </ul>
          </li>
          <!-- Administration de base -->
          <li>
            <h3
              class="px-2 font-semibold text-gray-700 uppercase cursor-pointer flex items-center space-x-2"
              @click="toggleSection('adminBase')"
            >
              <i class="fas fa-cog"></i>
              <span>Administration de base</span>
            </h3>
            <ul v-if="sectionsOpen.adminBase" class="space-y-2">
              <li v-for="item in adminBaseItems" :key="item.path">
                <router-link
                  :to="item.path"
                  class="flex items-center px-4 py-3 space-x-3 transition-colors duration-200 rounded-lg group hover:bg-emerald-50"
                  :class="{
                    'bg-emerald-100 text-emerald-600': $route.path === item.path,
                  }"
                >
                  <div
                    class="flex items-center justify-center w-10 h-10 transition-colors duration-200 rounded-lg"
                    :class="[
                      $route.path === item.path
                        ? 'bg-emerald-200'
                        : 'bg-gray-100 group-hover:bg-emerald-100',
                    ]"
                  >
                    <i :class="[item.icon, 'text-lg']"></i>
                  </div>
                  <span class="font-medium">{{ item.name }}</span>
                </router-link>
              </li>
            </ul>
          </li>
            <!-- Participants -->
             <li>
               <h3
                 class="px-2 font-semibold text-gray-700 uppercase cursor-pointer flex items-center space-x-2"
                 @click="toggleSection('participants')"
                >
                   <i class="fas fa-users"></i>
                 <span>Participants</span>
                </h3>
               <ul v-if="sectionsOpen.participants" class="space-y-2">
                <li v-for="item in participantItems" :key="item.path">
                    <router-link
                        :to="item.path"
                        class="flex items-center px-4 py-3 space-x-3 transition-colors duration-200 rounded-lg group hover:bg-emerald-50"
                          :class="{
                            'bg-emerald-100 text-emerald-600': $route.path === item.path,
                          }"
                    >
                       <div
                       class="flex items-center justify-center w-10 h-10 transition-colors duration-200 rounded-lg"
                       :class="[
                          $route.path === item.path
                            ? 'bg-emerald-200'
                             : 'bg-gray-100 group-hover:bg-emerald-100',
                       ]"
                    >
                        <i :class="[item.icon, 'text-lg']"></i>
                     </div>
                     <span class="font-medium">{{ item.name }}</span>
                    </router-link>
                   </li>
               </ul>
            </li>
            <!-- Sponsors -->
            <li>
                <h3
                    class="px-2 font-semibold text-gray-700 uppercase cursor-pointer flex items-center space-x-2"
                    @click="toggleSection('sponsors')"
                >
                     <i class="fas fa-hand-holding-heart"></i>
                    <span>Sponsors</span>
                </h3>
                <ul v-if="sectionsOpen.sponsors" class="space-y-2">
                    <li v-for="item in sponsorItems" :key="item.path">
                        <router-link
                            :to="item.path"
                            class="flex items-center px-4 py-3 space-x-3 transition-colors duration-200 rounded-lg group hover:bg-emerald-50"
                              :class="{
                                'bg-emerald-100 text-emerald-600': $route.path === item.path,
                              }"
                        >
                           <div
                                class="flex items-center justify-center w-10 h-10 transition-colors duration-200 rounded-lg"
                                :class="[
                                    $route.path === item.path
                                      ? 'bg-emerald-200'
                                      : 'bg-gray-100 group-hover:bg-emerald-100',
                                ]"
                            >
                                <i :class="[item.icon, 'text-lg']"></i>
                             </div>
                            <span class="font-medium">{{ item.name }}</span>
                        </router-link>
                    </li>
                </ul>
            </li>
             <!-- Contacts -->
            <li>
              <h3
                 class="px-2 font-semibold text-gray-700 uppercase cursor-pointer flex items-center space-x-2"
                 @click="toggleSection('contacts')"
                >
                <i class="fas fa-envelope"></i>
                <span>Contacts</span>
              </h3>
               <ul v-if="sectionsOpen.contacts" class="space-y-2">
                <li v-for="item in contactItems" :key="item.path">
                    <router-link
                        :to="item.path"
                        class="flex items-center px-4 py-3 space-x-3 transition-colors duration-200 rounded-lg group hover:bg-emerald-50"
                          :class="{
                            'bg-emerald-100 text-emerald-600': $route.path === item.path,
                          }"
                    >
                      <div
                        class="flex items-center justify-center w-10 h-10 transition-colors duration-200 rounded-lg"
                       :class="[
                            $route.path === item.path
                               ? 'bg-emerald-200'
                             : 'bg-gray-100 group-hover:bg-emerald-100',
                        ]"
                      >
                       <i :class="[item.icon, 'text-lg']"></i>
                      </div>
                    <span class="font-medium">{{ item.name }}</span>
                   </router-link>
                 </li>
               </ul>
            </li>
        </ul>
      </nav>

      <!-- Version Info -->
      <div class="p-4 mx-4 mb-4 rounded-lg bg-emerald-50">
        <p class="text-sm font-medium text-gray-600">Version</p>
        <p class="text-xs text-gray-500">v1.0.0</p>
      </div>
    </aside>

    <!-- Overlay -->
    <div
      v-show="isSidebarOpen"
      class="fixed inset-0 z-30 bg-black bg-opacity-50 md:hidden"
      @click="toggleSidebar"
    ></div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();
const isSidebarOpen = ref(false);

const sectionsOpen = ref({
    dashboard: true,
    adminContenu: false,
    adminBase: false,
    participants: false,
    sponsors: false,
    contacts: false
});

const dashboardItems = ref([
  {
    name: "Tableau de bord",
    path: "/Admin/dashboard",
    icon: "fas fa-chart-line",
  },
]);

const adminContenuItems = ref([
    {
      name: "Hymne",
      path: "/Admin/hymne",
      icon: "fas fa-music",
    },
    {
      name: "Pays",
      path: "/Admin/pays",
      icon: "fas fa-globe",
    },
    {
      name: "Ville",
      path: "/Admin/villes",
      icon: "fas fa-map-marker-alt",
    },
    {
     name: "Villages",
      path: "/Admin/villages",
      icon: "fas fa-tree",
    },
    {
        name: "Activités",
        path: "/Admin/activites",
        icon: "fas fa-tasks",
    },
]);

const adminBaseItems = ref([
    {
        name: "Paramètres visuels",
        path: "/Admin/visual-settings",
        icon: "fas fa-palette",
    },
    {
        name: "Configurations système",
        path: "/Admin/system-settings",
        icon: "fas fa-cogs",
    },
]);

const participantItems = ref([
  {
    name: "Liste des participants",
    path: "/Admin/participants",
    icon: "fas fa-users",
  },
   {
    name: "Ajouter un participant",
     path: "/Admin/participants/create",
     icon: "fas fa-user-plus",
    },
]);

const sponsorItems = ref([
    {
        name: "Liste des sponsors",
        path: "/Admin/sponsors",
         icon: "fas fa-hand-holding-heart",
     },
    {
        name: "Ajouter un sponsor",
        path: "/Admin/sponsors/create",
         icon: "fas fa-user-plus",
    },
]);
const contactItems = ref([
    {
        name: "Liste des contacts",
        path: "/Admin/contacts",
        icon: "fas fa-envelope",
    },
]);

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value;
};


const toggleSection = (sectionName) => {
  sectionsOpen.value = {
      ...sectionsOpen.value,
      [sectionName]: !sectionsOpen.value[sectionName],
  };
};


watch(
  () => route.path,
  () => {
    isSidebarOpen.value = false;
  }
);
</script>