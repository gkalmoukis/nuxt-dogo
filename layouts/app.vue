<template>
<div>
    <b-navbar toggleable="sm" type="light" variant="light">
        <b-navbar-brand href="/">
             <img src="~/static/load.gif" alt="Kitten">
        </b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav>
                <b-nav-item href="/">Υπολογισμός</b-nav-item>
            </b-navbar-nav>

            <b-navbar-nav class="ml-auto">            
            </b-navbar-nav>        

        </b-collapse>
    
    </b-navbar>

    <b-container>
        <Nuxt />
    </b-container>
    
    <footer class="py-4 flex-shrink-0">
        <div class="container text-center">
            {{new Date().getFullYear()}} &copy; <a href="https://gkalmoukis.com" target="_blank" class="text-muted">Giorgos Kalmoukis</a>
        </div>
    </footer>

</div>
</template>

<style>
:root{
  --white : white;
  --primary-purple : hsl(268, 100%, 50%);
  --secondary-purple :  hsl(268, 30%, 50%);
  --dark-purple : hsl(268, 100%, 20%);
  --input-border: #8b8a8b;
  --input-focus-h: 245;
  --input-focus-s: 100%;
  --input-focus-l: 42%;
}

/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}
</style>