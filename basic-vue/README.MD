# Vue 3 Basic

- Vue instance merupakan sebuah object yang berisi instance vue untuk memanipulasi element html, css dan juga javascript
- Untuk membuat vue instance menggunakan syntax berikut `Vue.createApp()`
- Vue instance biasanya hanya disisipkan pada 1 element div dengan id `app` dan pada element div itulah kita bisa bekerja dengan vue
- Vue Object direpresentasikan dengan curly braces yang ada didalam kurung `createApp({})`
- Vue object biasanya berisi data, methods, dan props
- Untuk menggunakan variable yang sudah di deklarasikan di Vue Object (data) kita bisa mengaksesnya dari element html dengan menggunakan mustache syntax `{{variable}}` exp. `{{greeting}}`
- Vue JS Directive : merupakan cara menghubungkan element HTML dan juga Javascript yang sudah dibuat di Vue
- `v-model` merupakan directive yang digunakan untuk menyisipkan variable mustache didalam element html
- `v-if`, `v-else-if`, `v-else` directive yang digunakan untuk memanipulasi element html berdasarkan kondisi (conditional statement) dan hanya akan membuat element (render) html jika bernilai true (truethy)
- `v-show` juga mirip dengan `v-if` karena akan menampilkan element html berdasarkan kondisi boolean, namun ada sedikit perbedaan dengan `v-if` dimana `v-show` akan selalu membuat element (render) html meskipun kondisinya bernilai false (falsy) tapi secara display akan dibuat tidak tampil (display:none)
- `v-cloak` directive yang digunakan untuk menyembunyikan semua element html dari rendering proses sampai dengan aplikasi vue dalam kondisi siap, sehingga kita tidak akan melihat variable raw ataupun element html raw yang didefinisikan dalam vue instance pada saat meload aplikasi, tapi hanya akan melihat element ataupun variable final ketika aplikasi vue sudah siap
- `v-cloak` penggunaanya disisipkan pada div yang berisi id app dan juga harus menggunakan style default `display:none`
- Event : merupakan kejadian yang terjadi di browser, seperti Mouse Event, Keyboard Event, atau yang lain
- `v-on` merupakan directive yang digunakan untuk menangkap Event (custom event, ataupun browser event), syntax penggunaannya adalah sebagai berikut `v-on:event="handle"` exp `v-on:click="setVisible"` `v-on` juga memiliki shorthand ataupun syntax yang lebih singkat yaitu `@event="handle"` dimana `v-on` digantikan oleh `@` exp `@click="setVisible"`
- methods : merupakan properties yang ada pada vue instance object yang biasanya digunakan untuk mendeklarasikan function/method
- Component : secara fungsi kurang lebih sama dengan instance object vue (memiliki data, props dan method) tapi lebih biasa digunakan sebagai html template yang akan direlasikan dengan structur DOM di file HTML
- Membuat component bisa menggunakan perintah `app.component(componentName, object)` exp `app.component('login-form', {})`
- Untuk menggunakan component lain didalam sebuah component kita harus melakukan pendaftaran component yang diinginkan (Register Component) pada component yang membutuhkan dengan property `components:[namaComponent]` exp. `components:['custom-input']`
- Untuk transfer data dari component induk ke component child kita bisa menggunakan syntax `v-bind:property="value"` exp `v-bind:label="emailLabel"` diikuti dengan pendeklarasian properti `props` pada component child dengan menggunakan syntax `props:['list of property']`
- `v-bind` juga mempunya shorthand yaitu dengan menggunakan syntax `:property="value`" exp `:label="emailLabel"`
- Mengakses dan menggunakan value pada component induk dari component child bisa menggunakan syntax `v-model` pada component induk kemudian diikuti oleh pendekrasian property `computed: {}` pada component child serta pendeklarasian `modelValue` pada list `props` component child dimana `modelValue` akan diambil dari syntax `v-model` yang dibuat di element html component child
- Penggunaan method getter and setter pada property `computed` digunakan untuk mendapatkan nilai dan juga mengisi nilai pada component child syntax yg digunakan adalah `get(){}` dan juga `set(value){this.$emit(eventName, value)}` exp. `set(value){this.$emit('update="modelValue", value')}
- Kenapa kita membutuhkan pemodelan untuk variable di component child? Karena pada dasarnya props yang kita kirimkan dari component induk ke child tidak bisa diubah (immutable) maka dari itu ketika kita membutuhkan untuk memanipulasi data di component child, maka kita harus menggunakan pemodelan variable yang kita lakukan diatas
- Loops atau perulangan juga ada pada Vue.JS yang di deklarasikan oleh syntax `v-for="(value, index) in arrays" v-bind:key="index"` biasanya disisipkan pada element html atau component exp. `<custom-input v-for="(input, index) in inputs" v-bind:key"index" v-model="input.value" v-bind:label="input.label" v-bind:type="input.type"/>`
- Life Cycle Hooks atau Component Life Cycle Hooks merupakan function atau method yang ada pada siklus pembuatan component, siklus siklus itu diantaranya adalah `beforeCreated`, `created`, `beforeMount`, `mounted`, `beforeUpdate`, `updated`, `beforeDestroy`/`beforeUnmount`, `destroy`/`unmounted`
- Lebih lengkap silakan cek diagram siklus hidup hook dari sebuah component pada link berikut ![Life-Cycle-Hooks](https://vuejs.org/assets/lifecycle.16e4c08e.png)
- Penggunaan Life Cycle Hooks biasanya sangat penting untuk beberapa use-case berikut :
    - Mengecek apakah user terotorisasi atau tidak sebelum memuat component
    - Melakukan API Calls ketika hook created/mounted (untuk mengambil data)
    - Membuat atau menghilangkan events dari component
    - Mengambil atau menghilangkan data dari component