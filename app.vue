<template>
  <div class="min-h-screen bg-gradient-to-br from-blue-100 to-indigo-200 flex flex-col items-center justify-center p-4">
    <div class="bg-white shadow-2xl rounded-lg overflow-hidden max-w-4xl w-full">
      <header class="bg-indigo-600 text-white p-6 flex items-center justify-between">
        <div>
          <h1 class="text-3xl font-bold">{{ cvData.name }}</h1>
          <p class="mt-2 text-indigo-200">{{ cvData.title }}</p>
        </div>
        <img :src="cvData.imageUrl" :alt="cvData.name" class="w-24 h-24 rounded-full border-4 border-white"/>
      </header>
      
      <main class="p-6">
        <section class="mb-6">
          <h2 class="text-2xl font-semibold text-indigo-600 mb-3">Tentang Saya</h2>
          <p class="text-gray-700">{{ cvData.about }}</p>
        </section>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <section>
            <h2 class="text-2xl font-semibold text-indigo-600 mb-3 flex items-center">
              <GraduationCap class="mr-2" /> Pendidikan
            </h2>
            <ul class="list-disc list-inside text-gray-700">
              <li v-for="(edu, index) in cvData.education" :key="index">{{ edu }}</li>
            </ul>
          </section>
          
          <section>
            <h2 class="text-2xl font-semibold text-indigo-600 mb-3 flex items-center">
              <Briefcase class="mr-2" /> Pengalaman & Keterampilan
            </h2>
            <ul class="list-disc list-inside text-gray-700">
              <li v-for="(skill, index) in cvData.skills" :key="index">{{ skill }}</li>
            </ul>
          </section>
        </div>
      </main>
      
      <footer class="bg-gray-100 p-6">
        <div class="flex flex-wrap justify-center gap-4 text-gray-600">
          <span class="flex items-center"><Mail class="mr-2" /> {{ cvData.contact.email }}</span>
          <span class="flex items-center"><Phone class="mr-2" /> {{ cvData.contact.phone }}</span>
          <span class="flex items-center"><Github class="mr-2"/> {{ cvData.contact.Github }}</span>
        </div>
      </footer>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import { GraduationCap, Briefcase, Mail, Github, Phone } from 'lucide-vue-next'

export default {
  components: {
    GraduationCap,
    Briefcase,
    Mail,
    Github,
    Phone
  },
  setup() {
    const cvData = ref({
      name: "Dandi Bagus Saputra",
      title: "Mahasiswa Teknologi Informasi",
      imageUrl: "https://shorturl.at/Qf4cu",
      about: "Halo! Saya Dandi Bagus Saputra, Lahir Pada 20 November 2004, berasal dari Kabupaten Blitar. Saya adalah anak pertama dari 2 bersaudara dan saat ini sedang menjalani kuliah di Universitas Brawijaya. Saya memiliki passion dalam bidang teknologi informasi dan selalu bersemangat untuk belajar hal-hal baru.",
      education: [
        "Alumni SMA Negeri 1 Talun",
        "Mahasiswa Prodi Teknologi Informasi Fakultas Vokasi"
      ],
      skills: [
        "Pemrograman dalam bahasa C++ dan JavaScript",
        "Pengalaman dalam pengembangan web",
        "Kemampuan analisis dan pemecahan masalah"
      ],
      contact: {
        email: "dandibagus7a@gmail.com",
        phone: "081334888503",
        Github: "https://github.com/A-Antithesis"
      }
    })

    return {
      cvData
    }
  }
}
</script>