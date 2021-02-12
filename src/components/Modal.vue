<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="w-modal" :class="{ sale: theme === 'sale' }">
            <slot>default content, shows if we don't pass default slot data</slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['theme'],
        methods: {
            closeModal() {
                this.$emit('close')
            }
        }
    }
</script>

<style scoped>
    .w-modal {
        width: 400px;
        padding: 20px;   
        margin: 100px auto;
        background: white;
        border-radius: 10px;    
    }
    .backdrop {
       top: 0;
       position: fixed;
       background: rgba(0, 0, 0, 0.5);
       width: 100%;
       height: 100%;
    }
    h1 {
       color: #038ecf;
       border: none;
       padding: 0;
    }
    .sale {
       background: crimson;
       color: white;
    }
    .sale h1 {
       color: rgb(255, 255, 255);
       border-bottom: 1px dotted white;
    }
    .actions {
       text-align: center;
       margin: 30px 0 10px 0;
    }
    .actions a {
       color: rgb(117, 151, 141)!important;
       padding: 5px 20px;
       border: 1px dotted #eee;
       border-radius: 4px;
       text-decoration: none;
       margin: 10px; 
    }
</style>