<template>
  <div class="blog-card">
    <div v-show="editPost" class="icons">
      <div class="icon">
        <Edit class="edit" />
      </div>
      <div class="icon">
        <Delete class="delete" />
      </div>
    </div>
    <img
      :src="require(`../assets/blogCards/${post.blogCoverPhoto}.jpg`)"
      alt=""
    />
    <div class="info">
      <h4>{{ post.blogTitle }}</h4>
      <h6>Posted on:{{ post.blogDate }}</h6>
      <router-link class="link" to="#"
        >View The Post<Arrow class="arrow"
      /></router-link>
    </div>
  </div>
</template>

<script>
import Arrow from "../assets/Icons/arrow-right-light.svg";
import Edit from "../assets/Icons/edit-regular.svg";
import Delete from "../assets/Icons/trash-regular.svg";
export default {
  components: {
    Arrow,
    Edit,
    Delete,
  },
  props: ["post"],
  computed: {
    editPost() {
      return this.$store.state.editPost;
    },
  },
};
</script>

<style lang="scss" scoped>
.blog-card {
  position: relative;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  border-radius: 8px;
  background-color: #fff;
  min-height: 420px;
  transition: 0.5s ease all;
  &:hover {
    transform: rotateZ(-1deg) scale(1.1);
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1) 0 2px 4px -1px
      rgba(0, 0, 0, 0.06);
  }
  .icons {
    display: flex;
    position: absolute;
    top: 10px;
    right: 10px;
    z-index: 90;

    .icon {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 35px;
      height: 35px;
      border-radius: 50%;
      background-color: #fff;
      transition: 0.5s ease all;
      &:hover {
        background-color: #303030;
        .edit,
        .delete {
          fill: #fff;
        }
      }
      &:nth-child(1) {
        margin-right: 8px;
      }
      .edit,
      .delete {
        pointer-events: none;
        width: 20px;
        height: 20px;
      }
    }
  }
  img {
    display: block;
    border-radius: 8px 8px 0 0;
    z-index: 1;
    width: 100%;
    min-height: 200px;
    object-fit: cover;
  }
  .info {
    display: flex;
    flex-direction: column;
    height: 100%;
    z-index: 3;
    padding: 32px 15px;
    color: #000;
    h4 {
      padding-bottom: 8px;
      font-size: 20px;
      font-weight: 300;
    }
    h6 {
      padding-bottom: 16px;
      font-size: 12px;
      font-weight: 400;
    }
    .link {
      display: inline-flex;
      align-items: center;
      margin-top: auto;
      padding-top: 20px;
      font-size: 12px;
      padding-top: 20px;
      font-weight: 500;
      transition: 0.5s ease-in all;
      &:hover {
        color: rgba(48, 48, 48, 0.8);
      }
      .arrow {
        width: 10px;
      }
    }
  }
}
</style>