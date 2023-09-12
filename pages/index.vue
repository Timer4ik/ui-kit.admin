<template>
  <UiCard padding="4">
    <UiStack
        flex-direction="column"
        gap="3"
    >
      <UiStack>
        <UiTypography
            fontSize="6"
            fontWeight="bold"
        >
          Пример ui элементов
        </UiTypography>

      </UiStack>

      <UiTabs>
        <UiTabsItem active>Первый таб</UiTabsItem>
        <UiTabsItem>Второй таб</UiTabsItem>
        <UiTabsItem>Второй таб</UiTabsItem>
        <UiTabsItem>Второй таб</UiTabsItem>
        <UiTabsItem>Второй таб</UiTabsItem>
        <UiTabsItem>Второй таб</UiTabsItem>
      </UiTabs>


      <UiGrid
          columns="1-1"
          gap="5"
          margin-bottom="5"
      >

        <!-- ======================================= -->

        <UiStack
            flex-direction="column"
            gap="3"
        >
          <UiControl
              label="Это input без валидации"
              message="Некоторое сообение снизу"
          >
            <UiField
                v-model="inputValue"
                placeholder="Привет"
            />
            <template #rightIcon>
              <IconsSearch style="cursor: pointer" />
            </template>
          </UiControl>

          <UiControl
              label="Это select без валидации"
              message="Обязательное поле*"
              :rightIcon="IconsSearch"
          >
            <UiSelect
                v-model:selectedItem="selectedItem"
                :options="items"
            />
          </UiControl>

          <UiControl
              label="Это multiple select без валидации"
              message="Некоторое сообение снизу"
              :rightIcon="IconsSearch"
          >
            <UiMSelect
                v-model:selectedItems="selectedItems"
                :options="items"
            />
          </UiControl>

          <UiControl message="Это чекбокс">
            <UiCheckbox
                v-model:model-value="isCheck"
                :label="isCheck ? 'выбрано' : 'не выбрано'"
            />
          </UiControl>

          <UiControl
              label="Загрузите файл"
              message="Файл не может превышать 2 мб"
          >
            <UiFileLoader model-value="" />
          </UiControl>

          <UiControl
              label="Выберите дату"
              message="Какой нибудь коммент"
          >
            <UiDatePicker v-model="date" />
          </UiControl>

          <UiControl
              label="textarea"
              message="textarea"
          >
            <UiTextarea
                placeholder="Введите текст"
                :rows="2"
                v-model:model-value="inputValue"
            />
          </UiControl>
        </UiStack>

        <!-- ======================================= -->

        <UiStack
            flex-direction="column"
            gap="3"
        >
          <VFormField
              name="email"
              placeholder="Введите email"
              label="Это input без валидации"
              message="Введите email"
              rules="email"
              :rightIcon="IconsSearch"
          />

          <VFormSelect
              label="Это select с валидацией"
              message="Обязательное поле*"
              name="aboba"
              :options="items"
              :selectedItem="selectedItem"
              rules="required"
              :rightIcon="IconsSearch"
          />

          <VFormMSelect
              label="Это multiple select с валидацией"
              message="Обязательное поле*"
              name="aboba"
              :options="items"
              :selectedItems="selectedItems"
              rules="required"
              :rightIcon="IconsSearch"
          />

          <VFormCheckbox
              name="checkbox"
              rules="required"
              label="Чекбокс"
              message="Тут у нас чекбокс"
          />

          <VFormFileLoader
              label="Загрузите файл"
              message="Файл не может превышать 2 мб"
              name="file"
              rules="required"
          />

          <VFormDatepicker
              label="Выберите дату"
              message="Дата"
              name="date"
              rules="required"
          />

          <VFormTextarea
              placeholder="Введите текст"
              label="Введите текст"
              message="Дата"
              name="date"
              rules="required"
          />
        </UiStack>
      </UiGrid>

      <UiStack
          flex-direction="column"
          gap="3"
      >
        <UiControl
            label="Загрузите фото"
            message="Максимальный размер фото 2 мб"
        >
          <UiPhotoLoader v-model:model-value="file" />
        </UiControl>
        <VFormPhotoLoader
            rules="required"
            name="photo"
            label="Загрузите фото"
            message="Максимальный размер фото 2 мб"
        />
      </UiStack>

      <UiStack
          flex-direction="column"
          gap="3"
      >
        <UiTypography
            fontSize="6"
            fontWeight="bold"
        >
          Пример лоадера
        </UiTypography>
        <UiLoader />
      </UiStack>
    </UiStack>

    <UiStack
        flex-direction="column"
        gap="3"
    >
      <UiDropdownMenu
          :isShow="isActiveDrop"
          @blur="isActiveDrop = false"
          @focus="isActiveDrop = true"
      >
        <template #body>
          <UiButton>Открыть</UiButton>
        </template>
        <template #drop>
          <div @click.stop>
            <UiTypography  >Кликай на меня</UiTypography>
          </div>
        </template>
      </UiDropdownMenu>

      <UiTable>
        <template #header>
          
        </template>
        <template #thead>
          <th></th>
          <th>
            <div>ID</div>
          </th>
          <th>
            <div>Заголовок</div>
          </th>
          <th>
            <div>Выполнено?</div>
          </th>
        </template>
        <template #tbody>
          <tr v-for="item in todoList">
            <td>
              <UiAutoDropdown>
                <template #body>
                  <div style="cursor: pointer;width: 25px;height: 25px;">
                    <UiTableMenuIcon />
                  </div>
                </template>
                <template #drop>
                  <div>
                    <div>Привет</div>
                  </div>
                  <div>
                    <div>Привет</div>
                  </div>
                  <div>
                    <div>Привет</div>
                  </div>
                </template>
              </UiAutoDropdown>
            </td>
            <td>
              <div>{{ item.id }}</div>
            </td>
            <td>
              <div>{{ item.title }}</div>
            </td>
            <td>
              <UiCheckbox
                  disabled
                  :model-value="item.completed"
              />
            </td>
          </tr>
        </template>
      </UiTable>

    </UiStack>



    <!-- <UiStack margin-bottom="5">
      <UiTypography
          fontSize="6"
          fontWeight="bold"
      >
        Здесь всякие загрузчики
      </UiTypography>
    </UiStack> -->
  </UiCard>
</template>

<script setup lang="ts">
import IconsSearch from "@/components/icons/search.vue";

const isActiveDrop = ref(false)
const inputValue = ref("");
const isCheck = ref(false);
const date = ref(new Date());
const items: {
  id: number
  value: string
  item: any
}[] = [
    { id: 1, item: 1, value: "1" },
    { id: 2, item: 2, value: "2" },
    { id: 3, item: 3, value: "3" },
  ];
const selectedItem = ref(null);
const selectedItems = ref([]);

const file = ref<string>("null");

interface Todo {
  id: number
  title: string
  completed: boolean
}

const todoList: Todo[] = [
  {
    id: 0,
    title: "hello",
    completed: false
  },
  {
    id: 1,
    title: "hello",
    completed: false
  },
  {
    id: 2,
    title: "hello",
    completed: false
  },
  {
    id: 3,
    title: "hello",
    completed: false
  },
]
</script>
