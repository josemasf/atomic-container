---
theme: ./
layout: intro
---

# Atomic containers for C# Devs

José María Santos 

<template v-slot:icon>
  <div class="flex justify-center w-full h-full ">    
    <logos-c-sharp class="w-full h-full" />  
    <logos-vue class="w-full h-full" />  
  </div>  
</template>



---

# Hola <mdi-hand-wave class="text-3xl text-yellow-400 animate-bounce "/>, Soy Jose


<div class="flex justify-center">
  <div class="flex flex-col md:flex-row md:max-w-md rounded-lg bg-white shadow-lg">
    <img class=" w-full h-96 md:h-auto object-cover md:w-48 rounded-t-lg md:rounded-none md:rounded-l-lg" src="https://avatars.githubusercontent.com/u/24436751?v=4" alt="" />
    <div class="p-6 flex flex-col justify-start">
      <h5 class="text-gray-900 text-xl text-center font-medium mb-2">Registros en Github</h5>
      <p class="text-gray-700 text-base mb-4">
        <img src="https://github-readme-stats.vercel.app/api/top-langs?username=josemasf&show_icons=true&locale=en&layout=compact" alt="josemasf" />
      </p>      
    </div>
  </div>
</div>



<div class="grid grid-cols-4 gap-4 mt-2 ">
  <div>
    <EnterpriseAtom image="/logos/logo-vista.png" name="Vistalegre Solutions" :from="2007" :to="2017"  />    
  </div>
  <div>
    <EnterpriseAtom image="/logos/logo-ofg.png" name="OFG" :from="2017" :to="2018"  />    
  </div>
  <div>
    <EnterpriseAtom image="/logos/logo-inno.png" name="Innovation strategies" :from="2018" :to="2023"  />    
  </div>
  <div>
    <EnterpriseAtom image="/logos/logo-aida.png" name="Aida" :from="2023" :to="0"  />    
  </div>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
layout: order-paper
---

<div class="grid grid-cols-4 gap-4 text-white mt-10">
  <OrderPaperItem icon="atom" title="Atomic Desing" body="Patrón de diseño para diseñadores gráficos"/>
  <OrderPaperItem icon="csharp" title="Componentes para Backender" body="Coceptos de componentes para programadores C#"/>
  <OrderPaperItem icon="foldercogoutline" title="Responsabilidades" body="Atomic Containers en profundidad"/>
  <OrderPaperItem icon="test-tube" title="Testing" body="Test unitarios, integración y E2E ¿dónde?"/>
</div>


---
layout: two-thirds
---

# Atomic Design

<template v-slot:first-col>

<img src="/imgs/atomic-design.png" />

</template>

<template v-slot:second-col>
  Atomic Design es un sistema de diseño. 

  Los sistemas de diseño nos permiten crear mejores productos y de una forma más rápida y coordinada. De hecho, permite que los elementos de diseño sean reutilizables y al mismo tiempo escalables.
</template>

<!--
### Átomos
Los átomos son los componentes básicos de toda la materia. Cada elemento tiene propiedades distintas y no se pueden desglosar más sin perder su significado. Estos son los bloques de construcción más pequeños de su proyecto

### Moléculas
Las moléculas son un grupo de átomos ensamblados para adquirir nuevas propiedades o para completar una función.

### Organismos
Los organismos son un poco más complejos y forman porciones más grandes de nuestro producto.
-->

---

# Contenedores y Vistas

### Contenedores

Responsables del acceso a datos, ya sea desde un gestor de estado o directamente al proveedor de datos. En caso de acceder directamente, se debe delegar esta responsabilidad de acceso en una capa de servicio

### Vistas

Responsables de presentar y orquestar a los contenedores en la pantalla.

---

# Dos contenedores una vista 

<MainView />

---

# Component para C# Dev

Los cuatro principios básicos de la programación orientada a objetos son:

- Abstracción.
- Encapsulación.
- Herencia.
- Polimorfismo.

---
layout: two-thirds
---

# Abstracción

<template v-slot:first-col>
```ts
/// InputAtom.vue
<template>
  <input
    type="text"
    :value="title"
    @input="$emit('update:value', $event.target.value)"
  />
</template>

<script setup>
    defineProps(['title'])
    defineEmits(['update:value'])
</script>

```
</template>

<template v-slot:second-col>
  Input Atom
  <input-atom/>
</template>

<!--
Modelar los atributos e interacciones pertinentes de las entidades como clases para definir una representación abstracta de un sistema.
-->

---
layout: two-thirds
---

# Encapsulación

<template v-slot:first-col>
```ts
  <template>
    <div class="p-5 bg-dark border-rounded">
      <button @click="increment">Púlasame {{ count }}</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  const count = ref(0);
  
  function increment() {
    count.value++;
  }
  </script>

```
</template>

<template v-slot:second-col>
  Buton Atom
  <button-atom />
</template>

<!--
Ocultar el estado interno y la funcionalidad de un objeto y permitir solo el acceso a través de un conjunto público de funciones.
-->

---
layout: two-thirds
---

# Herencia


<template v-slot:first-col>
```ts
// InputCounterMolecule.vue
<template>
    {{ myText }}
    <input-atom :text="myText" @update:value="myText = $event" />  
    <button-atom />    
</template>
  
<script setup>
    import { ref } from 'vue'

    import InputAtom from './InputAtom.vue';
    import ButtonAtom from './ButtonAtom.vue';  

    const myText= ref('');
</script>
```
</template>

<template v-slot:second-col>  
  <InputCounterMolecule />
</template>


<!--
Capacidad de crear nuevas abstracciones basadas en abstracciones existentes.
-->

---
layout: two-thirds
---

# Polimorfismo

<template v-slot:first-col>
```ts
// InputCounterMolecule2.vue
<template>
    {{ textNumber }}
    <input-atom :text="myText" @update:value="myText = $event" />  
    <button-atom @increment="myNumber = $event" />    
</template>
  
<script setup>
    import { ref,computed } from 'vue'
    import ButtonAtom from './ButtonAtom.vue';  

    const myText= ref('');
    const myNumber= ref(0);
    const textNumber= computed(() => myText.value + ' ' + myNumber.value);
   
</script>
```
</template>

<template v-slot:second-col>  
<InputCounterMolecule2/>
</template>


<!--
Capacidad de implementar propiedades o métodos heredados de maneras diferentes en varias abstracciones.
-->

---

# Testing

<table class="table-auto bg-dark">
  <thead class="text-center bg-gray-700">
    <tr>
      <th class="px-4 py-2">Área</th>
      <th class="px-4 py-2">Tipo de test</th>
      <th class="px-4 py-2">¿Mocks?</th>
    </tr>
  </thead>
  <tbody>
    <tr >
      <td class="px-4 py-2">Atomos</td>
      <td class="px-4 py-2">Unit tests</td>
      <td class="px-4 py-2">No</td>
    </tr>
    <tr>
      <td class="px-4 py-2">Moléculas</td>
      <td class="px-4 py-2">Unit tests</td>
      <td class="px-4 py-2">No</td>
    </tr>
    <tr>
      <td class="px-4 py-2">Organismos</td>
      <td class="px-4 py-2">Unit tests</td>
      <td class="px-4 py-2">No</td>
    </tr>
    <tr class="bg-blue-800">
      <td class="px-4 py-2">Contenedores</td>
      <td class="px-4 py-2">Integration tests</td>
      <td class="px-4 py-2">Sí, servidor (api o cuestiones de datetime)</td>
    </tr>
    <tr class="bg-blue-800">
      <td class="px-4 py-2">Vistas</td>
      <td class="px-4 py-2">Integration tests</td>
      <td class="px-4 py-2">Sí, servidor (api o cuestiones de datetime)</td>
    </tr>
    <tr class="bg-red-800">
      <td class="px-4 py-2">App.vue</td>
      <td class="px-4 py-2">End-to-end tests</td>
      <td class="px-4 py-2">No</td>
    </tr>
  </tbody>
</table>

---

# Evolución

- Simplificar Átomos, Moléculas y Organismos en Celulas y Organismos

<div class="flex justify-center items-center mb-5">
  <img src="/public/imgs/cell.png" class="h-50" />
  <img src="/public/imgs/heart.png" class="h-50" />
</div>

- Eliminar test de contenedores y detectar si se usan en los test de vistas

---
layout: center
class: "text-center"
---

# Learn More

[Documentations](https://sli.dev) / [GitHub Repo](https://github.com/slidevjs/slidev)
