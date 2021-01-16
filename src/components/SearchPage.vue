<template>
  <div id="app">
    <v-app id="inspire">
      <v-form v-model="valid" ref="form" lazy-validation>

        <v-row>
          <v-col cols="12" sm="2" md="2.8">
            <v-text-field v-model="employeeId" label="社員ID" outlined clearable></v-text-field>
          </v-col>
          <v-col cols="12" sm="2" md="2.8">
            <v-text-field v-model="name" label="名前" outlined clearable></v-text-field>
          </v-col>
          <v-col cols="12" sm="2" md="2.8">
            <v-text-field v-model="frigana" label="フリガナ" outlined clearable></v-text-field>
          </v-col>
          <v-col cols="12" sm="2" md="2.8">
            <v-text-field v-model="enteringDate" label="入社年月日" outlined clearable></v-text-field>
          </v-col>
        </v-row>

        <v-row>
          <v-col cols="12" sm="2" md="2.8">
            <v-text-field v-model="certificationName" label="資格" outlined clearable></v-text-field>
          </v-col>
          <v-col cols="12" sm="2" md="2.8">
            <v-text-field v-model="getDate" label="取得日付" outlined clearable></v-text-field>
          </v-col>
          <v-col cols="12" sm="2" md="2.8">
            <v-text-field v-model="encourageDate" label="奨励金日付" outlined clearable></v-text-field>
          </v-col>
          <v-col cols="12" sm="2" md="2.8">
            <v-btn color="primary" dark class="mb-2" @click="search()">
                検索
              </v-btn>

              <v-btn color="primary" dark class="mb-2" @click="newItem()">
                新規
              </v-btn>
          </v-col>
        </v-row>
                                  
        <v-data-table
          :headers="headers"
          :items="desserts"
          sort-by="calories"
          class="elevation-1"
        >
          <template v-slot:top>
            <v-toolbar flat>
              <v-toolbar-title>社員資格</v-toolbar-title>
              <v-divider class="mx-4" inset vertical></v-divider>
              <v-spacer></v-spacer>

              <v-dialog v-model="dialogDelete" max-width="500px">
                <v-card>
                  <v-card-title class="headline"
                    >Are you sure you want to delete this item?</v-card-title
                  >
                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="blue darken-1" text @click="closeDelete"
                      >Cancel</v-btn
                    >
                    <v-btn color="blue darken-1" text @click="deleteItemConfirm"
                      >OK</v-btn
                    >
                    <v-spacer></v-spacer>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-toolbar>
          </template>
          <template v-slot:item.actions="{ item }">
            <v-icon small class="mr-2" @click="editItem(item)">
              mdi-pencil
            </v-icon>
            <v-icon small @click="deleteItem(item)">
              mdi-delete
            </v-icon>
          </template>
          <template v-slot:no-data>
            <v-btn color="primary" @click="initialize">
              Reset
            </v-btn>
          </template>
        </v-data-table>
      </v-form>
    </v-app>
  </div>
</template>
<script src="./js/searchPage.js"></script>
