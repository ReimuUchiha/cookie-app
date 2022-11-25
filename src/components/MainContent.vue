<script setup lang="ts">
import { type Ref, ref } from "vue";

let UserInputTime: string;
let UserInputDate: string;
let UserInputName: string;

let currentDate = new Date();

let time =
  currentDate.getHours() +
  ":" +
  currentDate.getMinutes() +
  ":" +
  currentDate.getSeconds();

let cDay = currentDate.getDate();
let cMonth = currentDate.getMonth() + 1;
let cYear = currentDate.getFullYear();
let CurrentDayMonthYear: string = cDay + "." + cMonth + "." + cYear;

const myRowsRef: Ref<{ time: string; date: string; name: string }[]> = ref(
  getList()
);

const myRows = myRowsRef.value;

let paginationLimit: number = 10;
let pageCount = Math.ceil(myRows.length / paginationLimit);
let PagesArray: Ref<number[]> = ref(Array.from(Array(pageCount).keys()));

let currentPage: Ref<number> = ref(0);

let transferData: Ref<{ time: string; date: string; name: string }[]> = ref([]);

function getList() {
  let currentList = localStorage.getItem("UserInput");

  if (currentList == null) {
    return [];
  } else {
    const parsed2 = JSON.parse(currentList);
    return parsed2;
  }
}

function addRow() {
  if (UserInputDate == null) {
    UserInputDate = CurrentDayMonthYear;
  }
  if (UserInputTime == null) {
    UserInputTime = time;
  }

  myRowsRef.value.push({
    time: UserInputTime,
    date: UserInputDate,
    name: UserInputName,
  });

  const parsed = JSON.stringify(myRowsRef.value);
  localStorage.setItem("UserInput", parsed);

  shortList(currentPage.value);
  PageCalculation();
}

function deleteItem(index: number) {
  if (confirm("Bist du dir sicher, dass du diesen Eintrag löschen willst?")) {
    myRows.splice(index, 1);

    localStorage.setItem("UserInput", JSON.stringify(myRows));
    shortList(currentPage.value);
    PageCalculation();
  } else {
    return;
  }
}

function shortList(PageCounter: number) {
  transferData.value = [];
  let myRowsReversed: { time: string; date: string; name: string }[] = [
    ...myRows,
  ];
  myRowsReversed.reverse();

  for (
    let CountTen = PageCounter * 10;
    CountTen < PageCounter * 10 + 10;
    CountTen++
  ) {
    const temporaryData = myRowsReversed[CountTen];

    if (temporaryData != null) {
      transferData.value.push(temporaryData);
    }
  }
}

function PageCalculation() {
  paginationLimit = 10;
  pageCount = Math.ceil(myRows.length / paginationLimit);
  PagesArray.value = Array.from(Array(pageCount).keys());
}

function setCurrentPage(newPage: number) {
  currentPage.value = newPage;
  shortList(currentPage.value);
}

shortList(0);
</script>

<template>
  <div class="CenterBlock">
    <div class="InputContainer">
      <input placeholder="Zeit" v-model="UserInputTime" />
      <input placeholder="Datum" v-model="UserInputDate" />
      <input placeholder="Name" v-model="UserInputName" />
      <button @click="addRow">Add new entry</button>
    </div>

    <table class="ZeitDatumName">
      <tr>
        <th>Zeit</th>
        <th>Datum</th>
        <th>Name</th>
      </tr>
      <tr v-for="(row, index) in transferData" :key="'mainEntry' + index">
        <td class="center">
          {{ row.time }}
        </td>
        <td class="center">
          {{ row.date }}
        </td>
        <td class="center">
          {{ row.name }}
        </td>
        <td class="deleto">
          <button @click="deleteItem(index)">x</button>
        </td>
      </tr>
    </table>

    <button
      v-for="page in PagesArray"
      :key="page"
      @click="setCurrentPage(page)"
      :class="page == currentPage ? 'red' : 'green'"
    >
      {{ page + 1 }}
    </button>

    <!-- ? inline-if, : inline-else  -->
  </div>
</template>

<style>
@keyframes background-pan {
  from {
    background-position: 0% center;
  }

  to {
    background-position: -200% center;
  }
}
body {
  font-family: Sans-Serif;

  animation: background-pan 10s linear infinite;
  background-image: linear-gradient(
    to right,
    #7df9ff,
    #0892d0,
    #1dcfb8,
    #7df9ff
  );
  background-size: 200%;
}

th {
  text-align: left;
}

td {
  text-align: left;
  border: 1px solid black;
}

.deleto {
  text-align: right;
}

.CenterBlock {
  background-color: #ffffff;

  box-shadow: 20px 20px 5px rgba(0, 0, 0, 0.185);
  height: 70vh;
  width: 80vw;
  margin: 20px auto 20px auto;
}

.red {
  background-color: rgb(245, 94, 94);
}

.green {
  background-color: rgb(114, 207, 114);
}

.InputContainer {
  width: 90vh;
}

.ZeitDatumName {
  width: 90%;

  background: white;
  border: 1px solid black;
  margin: 40px 20px 20px 20px;
}
</style>
