<template>
<v-container>
  <v-layout row justify-center>
    <v-flex class="xs12 ma-5">
      <v-card>
        <v-list two-line subheader>
          <v-container>
            <v-subheader class="headline">
              {{ new Date() | date }}
            </v-subheader>
            <v-spacer></v-spacer>
            <p class="text-sm-right">У вас <b>{{ todos.length }}</b> задач.</p>
            <v-flex class="xs12">
              <v-text-field
                  label="Введите название задачи"
                  clearable
                  id="newTodo"
                  name="newTodo"
                  v-model="todoTitle"
              ></v-text-field>
            </v-flex>
          </v-container>
          <v-container>
            <v-layout justify-center>
              <v-subheader v-if="todos.length === 0">У вас 0 задач. Добавьте новую.</v-subheader>
              <v-subheader v-else>Ваши задачи:</v-subheader>
            </v-layout>
            <v-spacer></v-spacer>
            <div
                v-for="(task, key) in todos"
                :key="key"
            >
              <v-list-item>
                <v-list-item-action>
                  <v-checkbox>

                  </v-checkbox>
                </v-list-item-action>
              </v-list-item>
            </div>

          </v-container>
        </v-list>
      </v-card>
    </v-flex>
  </v-layout>
</v-container>
</template>

<script>
export default {
  data: () => ({
    todoTitle: '',
    todos: []
  }),
  filters: {
    capitalize(value) {
      return value.toString().charAt(0).toUpperCase() + value.slice(1)
    },
    date(value) {
      return new Intl.DateTimeFormat('ru-RU', {
        year: 'numeric',
        month: 'long',
        day: '2-digit'
      }).format(new Date(value))
    }
  }
}
</script>
