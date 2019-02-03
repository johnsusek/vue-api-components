<template>
  <div class="hello">
    <api url="/comments" @success="x => comments = x" />
    <api url="/albums" @success="x => albums = x" />
    <api url="/photos" @success="x => photos = x" />
    <api url="/todos" @success="x => todos = x" />
    <api url="/users" @success="x => users = x" />

    <el-form :model="newUser">
      <el-form-item label="name" prop="name">
        <el-input v-model="newUser.name" />
      </el-form-item>
      <el-form-item label="email">
        <el-input v-model="newUser.email" />
      </el-form-item>
      <el-form-item label="website">
        <el-input v-model="newUser.website" />
      </el-form-item>
      <el-form-item label="username">
        <el-input v-model="newUser.username" />
      </el-form-item>
      <el-form-item label="phone">
        <el-input v-model="newUser.phone" />
      </el-form-item>

      <api url="/users" method="post" :data="newUser">
        <el-button slot-scope="api" @click="api.action">
          Add user
        </el-button>
      </api>
    </el-form>

    <api
      url="/posts"
      :params="{ userId: selectedUserId }"
      @start="loading = true"
      @end="loading = false"
      @success="x => posts = x">
      <el-select
        v-model="selectedUserId"
        slot-scope="api"
        placeholder="Select user"
        filterable
        @change="api.action">
        <el-option v-for="user in users" :key="user.id" :value="user.id" :label="user.name" />
      </el-select>
    </api>

    <el-table v-loading="loading" :data="posts">
      <el-table-column label="id" prop="id" width="80" />
      <el-table-column label="userId" prop="userId" width="80" />
      <el-table-column label="title" prop="title" />
      <el-table-column label="body" prop="body" />
    </el-table>
  </div>
</template>

<script>
import Api from '@/components/Api.vue';

export default {
  name: 'HelloWorld',

  components: {
    Api
  },

  data() {
    return {
      newUser: {},
      loading: false,
      posts: null,
      comments: null,
      albums: null,
      photos: null,
      todos: null,
      users: null,
      selectedUserId: null
    };
  }
};
</script>
