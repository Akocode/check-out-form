<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div class="modal" role="dialog" aria-labelledby="modalTitle" aria-describedby="modalDescription">
        <header class="modal-header" id="modalTitle">
          <slot name="header">
            Summary Of Details Provided
            <!-- <button type="button" class="btn-close" @click="close" aria-label="Close modal">
              x
            </button> -->
          </slot>
        </header>
        <section class="modal-body" id="modalDescription">
          <slot name="body">
              <div class="content">
                <p>Full Name: <b>{{Selectedtitle}} {{first_name}} {{last_name}}</b> </p>
                <p>Contact Address: <b>Lagos,Nigeria</b> </p>
                <p>Contact Number: <b>{{number}}</b> </p>
                <p>Email Address: <b>{{email}}</b> </p>
              </div>
          </slot>
        </section>
        <footer class="modal-footer">
          <slot name="footer">
            <div class="btn-save">
                <button type="button" class="btn-green" @click="close" aria-label="Close modal">
                Close
                </button>
                <button type="button" class="btn-green" @click="save" aria-label="Save modal">
                Save
                </button>
            </div>
          </slot>
        </footer>
      </div>
    </div>
  </transition>
</template>
<script>
export default {
    name: "Modal",
    props: {
      first_name: String,
      last_name: String,
      number: String,
      Selectedtitle: String,
    },
    methods: {
        close(){
            this.$emit('close');
        },

        save(){
            this.$emit('save');
        }
    },
}
</script>
<style scoped>
  .modal-backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.3);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal {
    background: #FFFFFF;
    box-shadow: 2px 2px 20px 1px;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
  }

  /* .modal-footer  */
  .modal-header{
    padding: 10px;
    display: flex;
  }

  .modal-header {
    border-bottom: 1px solid #eeeeee;
    color: #4AAE9B;
    justify-content: space-between;
  }

  .modal-footer {
    border-top: 1px solid #eeeeee;
    /* justify-content: space-around; */
    /* justify-content: space-between; */
  }

  .modal-body {
    position: relative;
    padding: 20px 10px;
  }

  /* .btn-close {
    border: none;
    font-size: 20px;
    padding: 20px;
    cursor: pointer;
    font-weight: bold;
    color: #4AAE9B;
    background: transparent;
  } */

  .btn-green {
    color: white;
    background: #4AAE9B;
    border: 1px solid #4AAE9B;
    border-radius: 2px;
  }
  .content{
      display: flex;
      flex-direction: column;
  }

  .btn-save{
      display: flex;
      justify-content: space-between;
      margin: 10px;
  }
</style>