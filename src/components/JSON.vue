<!-- <template>
    <div>
      <vue-json-pretty :data="{ key: 'value' }" :editable="true"/>
    </div>
  </template>
  
  <script>
  import VueJsonPretty from 'vue-json-pretty';
  import 'vue-json-pretty/lib/styles.css';
  
  export default {
    components: {
      VueJsonPretty,
    },
  };
  </script> -->

  <template>
    <div>
      <!-- El contenedor para el editor JSON -->
      <div ref="jsonEditorContainer" style="width: 100%; height: 400px;"></div>
    </div>
  </template>
  
  <script>
  import { ref, onMounted } from 'vue';
  import JSONEditor from 'jsoneditor';
  import 'jsoneditor/dist/jsoneditor.min.css';
  
  export default {
    setup() {
      const jsonEditorContainer = ref(null);
      let editor = null;
  
      const initialJson = {
        "Array": [1, 2, 3],
        "Boolean": true,
        "Null": null,
        "Number": 123,
        "Object": {"a": "b", "c": "d"},
        "String": "Hello World"
      };
  
      onMounted(() => {
        // Crear el editor dentro del contenedor cuando el componente está montado
        editor = new JSONEditor(jsonEditorContainer.value, {
          mode: 'tree', // Puedes cambiar a 'code', 'view', 'text' o 'tree'
        });
  
        // Establecer el JSON inicial
        editor.set(initialJson);
      });
  
      return {
        jsonEditorContainer,
      };
    }
  };
  </script>
  
  <style>
  /* Asegúrate de que el contenedor tenga suficiente espacio para mostrar el editor */
  div[ref="jsonEditorContainer"] {
    width: 100%;
    height: 400px;
  }
  </style>
  