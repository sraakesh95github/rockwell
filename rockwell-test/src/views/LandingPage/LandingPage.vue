<template>
    <div>
      <div class="searchContainer">
        <cv-search v-model="searchString"></cv-search>
        <cv-button @click="getItemsList">GO</cv-button>
      </div>

      <div id="list_resources">
        <list-resources :resources="listItems"></list-resources>
      </div>
    </div>
</template>

<script>
import ListResources from '/src/components/Resources/ListResources.vue'

export default {
  components: {
    ListResources
  },
  data() {
    return {
      searchString: '',
      // resources: [
      //   {
      //     id: "1",
      //     name: "Watson X",
      //     content: {
      //       "id": "1234",
      //       "summary": "IBM's recent AI platform",
      //       "link": "https://www.ibm.com/cloud/watson-discovery"
      //     }
      //   },
      //   {
      //     id: "2",
      //     name: "GPT-3",
      //     content: {
      //       "id": "2345",
      //       "summary": "OpenAI's world renowned platform",
      //       "link": "https://openai.com/blog/gpt-3-apps"
      //     }
      //   },
      //   {
      //     id: "3",
      //     name: "GPT-4",
      //     content: {
      //       "id": "3456",
      //       "summary": "OpenAI's latest world renowned platform",
      //       "link": "https://openai.com/blog/gpt-4-apps"
      //     }
      //   }
      // ]
      resources: []
    }
  },
  computed: {
    listItems() {
      return this.resources;
    }
  },
  methods: {
    getItemsList() {
      console.log("searchString: " + this.searchString)
      fetch('http://127.0.0.1:8000/items?search_string=' + this.searchString)
      .then((response) => {
        if(response.ok) {
          return response.json();
        }
      })
      .then((data) => {
        const results = [];
        let documentContent = data['selection']
        for (let i=0; i<documentContent.length; i++) {
          results.push({
            id: documentContent[i].id.toString(),
            name: documentContent[i].name,
            summary: documentContent[i].summary,
            ER_keywords: documentContent[i].ER_keywords,
            link: documentContent[i].link,
            category: documentContent[i].category,
          })
        }
        console.log("Results: ");
        console.log(results);
        this.resources = results;
      })
      }
    }
  }
</script>

<style scoped>
div.list_resources {
  margin: 0;
  width: 80%;
}

div {
  margin: auto;
  width: 80%;
}

.searchBar {
  padding-left: 0%;
  padding-right: 0%;
}

/* .goButton {

} */

.searchContainer {
  display: flex;
  padding-bottom: 50px;
}
</style>