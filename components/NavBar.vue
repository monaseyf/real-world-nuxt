 <<template>
     <div class="nav">
         <nuxt-link to="/" class="brand">
            Real World Events
         </nuxt-link>
         <nav>
             <nuxt-link to="/">List</nuxt-link> |
             <nuxt-link to="/event/create"> Create</nuxt-link>
         </nav>
     </div>
 </template>

 <style>
 .nav{
     display: flex;
     justify-content: space-around;
 }
 .nav a {
     color: #5db15b;
     font-size: 3rem;
 }
 </style>