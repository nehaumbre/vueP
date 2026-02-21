<script setup>
//   import SampleComponent1 from './components/SampleComponent1.vue';
// import SampleComponent2 from './components/SampleComponent2.vue';
// import MyComponent from './components/MyComponent.vue';
// import attrBindings from './components/attrBindings.vue';
// import GlobalStyle from './components/GlobalStyle.vue';
// import LocalStyle from './components/LocalStyle.vue';
// import CombinedStyle from './components/CombinedStyle.vue';
// import ModuleStyle from './components/ModuleStyle.vue';
// import MyEvent from './components/MyEvent.vue';

// import MyReactiveComponent from './components/MyReactiveComponent.vue';
// import MyRefComponent from './components/MyRefComponent.vue';
// import ComputedProperties from './components/ComputedProperties.vue';
// import ConditionalRender from './components/ConditionalRender.vue';
// import vfor from './components/vfor.vue';
// import vModel from './components/v-model.vue';
// import prop from './components/staticProp.vue';
// import DynamicProps from './components/DynamicProps.vue';
// import propValidation from './components/propValidation.vue';
// import ComplexProps from './components/ComplexProps.vue';
// import CustomValidatorProps from './components/CustomValidatorProps.vue';
// import ComponentEvent from './components/ComponentEvent.vue';
// import FormComponent from './components/FormComponent.vue';
// import Slots from './components/Slots.vue';
// import FallbackSlot from './components/FallbackSlot.vue';
// import NamedSlot from "./components/NamedSlot.vue";
// import DefaultSlot from "./components/DefaultSlot.vue";
import SchoolComponent from './components/ProvideAndInject/SchoolComponent.vue';
import PractiseComponent from './components/ProvideAndInject/PractiseComponent.vue';

// import { ref } from 'vue';
import { provide } from 'vue';
// provide('studentName','alex')
// provide('studentAge',20)
// provide('studentLocation',['Earth','IDK'])
// const count = ref(0)
// const firstname = ref('John')
// const lastname = ref('Doe')
// const myFavoriteNumber = ref(7)
// const studentName = 'alex'
// const  studentAge = 20
// const studentLocation = ['Earth', 'IDK']
// const formHandler = (username, email, password)=>{ console.log(`username:${username} email: ${email} password: ${password}`);}
// provide array
provide('friends',['alex','john','jordan','Kim','sarah'])
//provide object
provide('games', {
  id: 1,
  title: 'Epic Adventure Game',
  genre: ['Action', 'Adventure', 'RPG'],
  platform: ['PC', 'PlayStation', 'Xbox', 'Nintendo Switch'],
  releaseDate: '2022-03-15',
  developer: {
    name: 'Awesome Game Studios',
    location: 'San Francisco, CA',
    teamSize: 50
  }
})

// Using Provide With Array Of Objects
provide('moreGames', [
  {
    title: 'Space Explorer',
    genre: 'Sci-Fi',
    platform: 'PC',
    releaseDate: '2023-05-20'
  },
  {
    title: 'Fantasy Quest',
    genre: 'Fantasy',
    platform: 'PlayStation',
    releaseDate: '2023-07-10'
  },
  {
    title: 'Inception',
    director: 'Christopher Nolan',
    genre: 'Sci-Fi',
    releaseDate: '2010-07-16'
  },
  {
    title: 'The Shawshank Redemption',
    director: 'Frank Darabont',
    genre: 'Drama',
    releaseDate: '1994-09-23'
  }
])
</script>

<template>
  <!-- <MyComponent/> -->
  <!-- <attrBindings/> -->
  <!-- <GlobalStyle/>
  <LocalStyle/>
  <CombinedStyle/>
  <ModuleStyle/> -->
  <!-- <MyEvent/> -->
  <!-- <MyReactiveComponent/> -->
  <!-- <MyRefComponent/> -->
  <!-- <ComputedProperties/> -->
  <!-- <ConditionalRender/> -->
  <!-- <vfor/> -->
  <!-- <v-model/> -->
  <!-- <prop name="john doe"/> -->
  <!-- <DynamicProps :myFavoriteNumber="myFavoriteNumber" :firstname="firstname" :lastname="lastname"/> -->
  <!-- <propValidation  :fullname="'zee'" :age="50"/> -->
  <!-- <ComplexProps :friends = "['alex', 'john', 'kris','sarah']" :userinfo ="{name:'alex', age: 30, location: ['earth','IDK']}" /> -->
  <!-- <CustomValidatorProps :name="'John'" :age="2" :password="'id'" /> -->
  <!-- <h1>Count: {{ count }}</h1> -->
  <!-- <ComponentEvent @incrementCounter="count++"/> -->
  <!-- <FormComponent @userinfo = "formHandler"/> -->
  <!-- <Slots>
    <h1>content 1</h1>
    <h2>content 2</h2>
  </Slots> -->
  <!-- <FallbackSlot></FallbackSlot> -->
  <!-- <FallbackSlot><p>
    Fallback doesnt apply here because content is provided 
    </p></FallbackSlot> -->
  <!-- <NamedSlot>
    
    #two
    <template v-slot:one>
      <h1>This content goes to slot "one"</h1>
    </template>
    <template #two>
      <h1>This content goes to slot "two"</h1>
    </template>
  </NamedSlot>
  <hr> -->
  <!-- <DefaultSlot>
    <template #default>
      <h1>This is some random default content</h1>
    </template>
  </DefaultSlot> -->
  <!-- <SchoolComponent :studentName="studentName" :studentAge="studentAge" :studentLocation="studentLocation"/> -->
  <!-- <SchoolComponent/> -->
  <PractiseComponent/>
</template>

<style scoped></style>
