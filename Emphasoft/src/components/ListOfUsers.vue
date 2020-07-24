<template>
  <div class="content_users_list">
    <table class="list_table" border="1">
      <tr>
        <th>
          <div>
            <span>ID</span>
            <button v-on:click="$emit('sortById')">sort by id</button>
          </div>
        </th>
        <th>
          <div>
            <span>UserName</span>
            <button v-on:click="$emit('sortByUsername')">sort by username</button>
          </div>
        </th>
        <th>
          <div>
            <span>First name</span>
          </div>
        </th>
        <th>
          <div>
            <span>Last name</span>
          </div>
        </th>
      </tr>
      <tr v-for="item of dataUsers" :key="item.index">
        <th class="content_users_list_id">{{item.id}}</th>
        <th class="content_users_list_username">{{item.username}}</th>
        <th>{{item.first_name}}</th>
        <th>{{item.last_name}}</th>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  props: ["dataUsers"],
  data() {
    return {
      usernameSort: false,
      idSort: false,
    };
  },
  methods: {},
};
</script>

<style>
.content_users_list {
  width: 100%;
  margin-top: 1%;
  display: flex;
  justify-content: center;
}
.list_table {
  width: 100%;
  font-family: "Trebuchet MS", Arial, Helvetica, sans-serif;
  font-size: 12px;
  border-collapse: collapse;
}
.content_users_list_id {
  width: 7%;
}
.content_users_list_username {
  width: 14%;
}
.list_table td,
.list_table th {
  border: 1px solid #ddd;
  padding: 8px;
}

.list_table tr:nth-child(even) {
  background-color: #383a59;
}

.list_table tr:hover {
  background-color: #6272a4;
}

.list_table th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  color: white;
}
</style>