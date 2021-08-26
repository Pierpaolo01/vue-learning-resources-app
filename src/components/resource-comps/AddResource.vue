<template>

    <base-dialog v-if="invalidData" title="Invalid Input" @close="confirmError">
        <template #default> 
            <p>Unfortunatly, at least one input value is invalid</p>
            <p>Please check all inputs</p>
        </template>
        <template #actions>
            <base-button @click="confirmError"> Okay </base-button>
        </template>
    </base-dialog>
    <base-card>
        <form @submit.prevent="submitResource">
            <div class="form-control">
                <label for="title">Title</label>
                <input id="title" name="title" type="text" ref="inTitle">
            </div>
            <div class="form-control">
                <label for="description">description</label>
                <textarea name="description" id="description" rows="3" ref="inDescr"></textarea>
            </div>
             <div class="form-control">
                <label for="link">URL</label>
                <input id="link" name="link" type="url" ref="inUrl">
            </div>
            <div>
                <base-button type="submit" > Add Resource </base-button>
            </div>

        </form>
    </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
export default {
  components: { BaseButton },
    inject: ['addedResource'],
    data(){
        return{

            invalidData: false,
            
        }
    },
    methods: {
        submitResource(){
            const title = this.$refs.inTitle.value;
            const description = this.$refs.inDescr.value;
            const link = this.$refs.inUrl.value;
            
            if(title.trim() === '' || description.trim() === '' || link.trim() === ''){
                this.invalidData = true;
                return;
            }

            this.addedResource(title, description, link);
        },
        confirmError(){
            this.invalidData = false;
        }
    }
}
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>