<template>
  <div class="main">
    <div class="app-container">
      <div class="heading">
        <h2 class="heading-text">To - Do List</h2>
      </div>
      <div class="create-task">
        <div class="input-container">
          <input
            type="text"
            placeholder="Create Task"
            class="input-text-box"
            v-model="createTask"
            @keyup.enter="create"
          />
        </div>
        <button class="create-btn" @click="create">
          <img src="../assets/create.png" alt="create" class="create-icon" />
        </button>
      </div>
      <div class="list-container">
        <div class="allDone" v-if="allDone">
          Huraay!!<br />All Tasks Are Completed.
        </div>
        <div class="container-empty" v-if="tasks.length === 0">
          <div class="image">Please Add Some Tasks In The List !!</div>
        </div>
        <div class="list-iterator" v-for="(task, index) in tasks" :key="index">
          <ul class="list" id="done">
            <li>{{ task }}</li>
          </ul>
          <button class="remove" @click="remove(index)">
            <img src="../assets/remove.png" alt="remove" class="remove-icon" />
          </button>
          <button class="done" id="btn" @click="done(index)">
            <img src="../assets/correct.png" alt="remove" class="done-icon" />
          </button>
        </div>
      </div>
      <div class="total-count">
        <div class="count">{{ counter + "/" + tasks.length }}</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "homePage",
  data() {
    return {
      createTask: "",
      tasks: [],
      counter: 0,
      allDone: false,
    };
  },
  methods: {
    create() {
      if (this.createTask != "") {
        this.tasks.push(this.createTask);
        this.createTask = "";
      } else {
        alert("please add some task first");
      }
    },
    done(index) {
      this.counter++;
      console.log("printing countetr value", this.counter);
      let ele = document.querySelectorAll("#done");
      let btn = document.querySelectorAll("#btn");
      for (let i = 0; i < ele.length; i++) {
        if (i === index) {
          ele[i].style.background = "green";
          ele[i].style.color = "white";
          btn[i].disabled = true;
          btn[i].style.background = "black";
        }

        if (this.counter === this.tasks.length) {
          this.allDone = true;
        }
      }
    },
    remove(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>
<style scoped>
.main {
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid black;
  width: 100%;
  height: 100vh;
}

.app-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  border: none;
  border-radius: 7px;
  width: 25%;
  height: 70%;
  box-shadow: 0px 0px 10px 0px #80808096;
  background-color: whitesmoke;
}

.heading {
  border: none;
  width: 95%;
  height: 6vh;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 1%;
  border-radius: 5px;
  margin-top: 3%;
  box-shadow: 0px 0px 10px 0px #80808096;
  background-color: white;
}

.heading-text {
  font-size: 20px;
  font-family: helvetica;
  color: blue;
}

.create-task {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 78%;
  height: 8%;
  margin-top: 10%;
}

.input-container {
  display: flex;
  justify-content: center;
  align-items: center;
  border: none;
  border-radius: 5px;
  box-shadow: 0px 0px 10px 0px grey;
  width: 70%;
  height: 100%;
  overflow: hidden;
}

.input-text-box {
  width: 100%;
  height: 100%;
  text-align: center;
  font-size: 15px;
  font-family: helvetica;
  border: none;
}

.create-btn {
  width: 25%;
  height: 100%;
  border-radius: 5px;
  border: none;
  box-shadow: 0px 0px 10px 0px grey;
  background-color: white;
  color: white;
  font-size: 13px;
  font-family: helvetica;
  display: flex;
  justify-content: center;
  align-items: center;
}

.create-icon {
  width: 60%;
  height: 80%;
}

.create-btn:active {
  background-color: blue;
}

.list-iterator {
  display: flex;
  justify-content: space-between;
  width: 95%;
  height: 10%;
  margin-top: 2%;
}

.list-container {
  width: 77%;
  height: 60%;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  overflow: auto;
  margin-top: 5%;
  border: none;
  box-shadow: 0px 0px 10px 0px grey;
}

.list {
  display: flex;
  justify-content: center;
  align-items: center;
  list-style: none;
  margin: 0px;
  padding: 0px;
  border-radius: 3px;
  width: 80%;
  height: 100%;
  font-size: 15px;
  font-family: helvetica;
  border: none;
  box-shadow: 0px 0px 10px 0px grey;
  background-color: white;
}

.remove {
  border: none;
  box-shadow: 0px 0px 10px 0px grey;
  width: 15%;
  height: 100%;
  border-radius: 3px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
}

.remove-icon {
  width: 100%;
  height: 100%;
}
.done {
  border: none;
  box-shadow: 0px 0px 10px 0px grey;
  width: 15%;
  height: 100%;
  border-radius: 3px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
}
.done-icon {
  width: 100%;
  height: 79%;
}

.remove:active {
  background-color: red;
}
.done:active {
  background: blue;
}
.container-empty {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
}
.total-count {
  display: flex;
  justify-content: center;
  align-items: center;
  border: none;
  width: 76%;
  height: 6%;
  border-radius: 5px;
  background: whitesmoke;
  box-shadow: 0px 0px 10px 0px grey;
  margin-top: 7%;
}
.count {
  font-size: 20px;
  font-family: helvetica;
}
.allDone {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  border: none;
  width: 19%;
  height: 42%;
  border-radius: 7px;
  background: #0000008f;
  font-size: 28px;
  font-family: helvetica;
  color: white;
}
</style>
