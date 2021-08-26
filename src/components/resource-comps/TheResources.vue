<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resources')" :mode="storedResBtnMode"> Stored Resources </base-button>
        <base-button @click="setSelectedTab('add-resource')" :mode="addResBtnMode"> Add Resources </base-button>
    </base-card>

    <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource";

export default {
    components: {
        StoredResources,
        AddResource,
    },
    data(){
        return{ 
            selectedTab: 'stored-resources',
            storedResources: [{
                id: 'official-guide',
                title: 'Official Guide',
                description: 'The offcialVue.JS guide',
                link: 'https://vuejs.org',
        },
        {
                id: 'google',
                title: 'google',
                description: 'The offcialVue.JS guide',
                link: 'https://google.com',
        }],
        }
    },
    provide() {
        return{
            resources: this.storedResources,
            addedResource: this.addedResource,
        }
    },
    methods: {
        setSelectedTab(tab){
            this.selectedTab = tab; 
        },
        addedResource(title, descr, url){
            const newResource = {
                id: new Date().toISOString,
                title: title,
                description: descr,
                link: url,
            };
            this.storedResources.unshift(newResource);
            this.selectedTab = 'stored-resources';
        }
    },
    computed: {
        storedResBtnMode() {
            return this.selectedTab === 'stored-resources' ? null : 'flat';
        },
        addResBtnMode() {
            return this.selectedTab === 'add-resource' ? null : 'flat';
        },
    }
}
</script>