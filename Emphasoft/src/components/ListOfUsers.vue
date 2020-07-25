<template>
  <div class="content_users_list">
    <table class="list_table" border="1">
      <thead class="list_table_header">
        <tr>
          <td>
            <div class="table_sort">
              <span class="list_table_id">ID</span>
              <button class="table_sort_btn" v-on:click="$emit('sortById')">
                <img class="table_sort_icon" src="./../assets/icons8-sort-26.png" />
              </button>
            </div>
          </td>
          <td>
            <div class="table_sort">
              <span class="list_table_username">UserName</span>
              <button class="table_sort_btn" v-on:click="$emit('sortByUsername')">
                <img class="table_sort_icon" src="./../assets/icons8-sort-26.png" />
              </button>
            </div>
          </td>
          <td>
            <span class="list_table_firstName">First name</span>
          </td>
          <td>
            <span class="list_table_lastName">Last name</span>
          </td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item of dataUsers" :key="item.index">
          <th class="table_user_id">
            <span>{{item.id}}</span>
          </th>
          <th class="table_user_username">
            <span>{{item.username}}</span>
          </th>
          <th>
            <span class="table_user_firstName">{{item.first_name}}</span>
          </th>
          <th>
            <span class="table_user_lastName">{{item.last_name}}</span>
          </th>
        </tr>
      </tbody>
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
.table_sort_btn {
  width: 14px;
  height: 14px;
  background-color: transparent;
  border: none;
}

.table_sort_btn:focus {
  outline: none;
}

.table_sort_icon {
  width: 12px;
  height: 13px;
}

.table_sort {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.list_table {
  width: 100%;
  font-family: "Trebuchet MS", Arial, Helvetica, sans-serif;
  font-size: 12px;
  border-collapse: collapse;
}

.list_table_header {
  background-color: #6272a4;
}

@media only screen and (max-width: 1310px) {
  /* Force table to not be like tables anymore */
  table,
  thead,
  tbody,
  th,
  td,
  tr {
    display: block;
  }

  /* Hide table headers (but not display: none;, for accessibility)
  thead tr {
    position: absolute;
    top: -9999px;
    left: -9999px;
  } */

  tr {
    border: 1px solid #ccc;
  }

  td {
    /* Behave  like a "row" */
    border: none;
    border-bottom: 1px solid #eee;
    position: relative;
    padding-left: 50%;
    text-align: start;
  }

  td:before {
    /* Now like a table header */
    position: absolute;
    /* Top/left values mimic padding */
    top: 6px;
    left: 6px;
    width: 45%;
    padding-right: 10px;
    white-space: nowrap;
  }

  /*
	Label the data
	*/
  th:nth-of-type(1):before {
    content: "ID: ";
  }
  th:nth-of-type(2):before {
    content: "Username: ";
  }
  th:nth-of-type(3):before {
    content: "First name: ";
  }
  th:nth-of-type(4):before {
    content: "Last name: ";
  }
}
.list_table td,
.list_table th {
  border: 1px solid #ddd;
  padding: 8px;
  word-wrap: break-word;
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