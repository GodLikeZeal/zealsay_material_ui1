<template>
  <div class="con">
    <v-data-table
      :headers="headers"
      :items="desserts"
      class="elevation-1"
    >
      <template
        slot="items"
        slot-scope="props"
      >
        <td>{{ props.item.username }}</td>
        <td>{{ props.item.name }}</td>
        <td >{{ props.item.email }}</td>
        <td >{{ props.item.age }}</td>
        <td >{{ props.item.sex==0?'男':'女' }}</td>
        <td >{{ props.item.status }}</td>
      </template>
    </v-data-table>
  </div>
</template>
<script>
import { getUserList } from "@/api/user";

export default {
  data() {
    return {
      headers: [
        {
          text: "用户名",
          value: "username"
        },
        { text: "姓名", value: "name" },
        { text: "邮箱", value: "email" },
        { text: "年龄", value: "age" },
        { text: "性别", value: "sex" },
        { text: "status", value: "status" }
      ],
      desserts: [
      ]
    };
  },
  created() {
    getUserList().then(res => {
      this.desserts = res.data.records;
    });
  },
  methods: {}
};
</script>
<style lang="less" scoped>
.con{
    padding: 0 20px;
}
</style>

