<template>
  <div class="board-completion-btn">
    <Checkbox v-model="showProgress"
              :disabled="isDisabled"
              size="small"
    >
      <span>Show progress</span>
    </Checkbox>
  </div>
</template>

<script>
  export default {
    name: 'ShowProgressBtn',
    props: ['isDisabled'],
    computed: {
      showProgress: {
        get () {
          return this.$store.state.boards.activeBoard.showProgress
        },
        set (val) {
          this.$store.dispatch('switchShowProgress', {boardId: this.$store.state.boards.activeBoard.id, val})
          this.$bus.$emit('focusOnAddItem');
        }
      }
    }
  }
</script>

<style scoped>
  .board-completion-btn {
    user-select: none;
  }
</style>
