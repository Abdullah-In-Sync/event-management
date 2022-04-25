<template>
  <div class="block p-6 rounded-lg shadow-lg bg-white max-w-sm">
    <form>
      <div class="form-group mb-6">
        <label for="name" class="form-label inline-block mb-2 text-gray-700"
          >Name</label
        >
        <input
          type="text"
          v-model="name"
          class="
            form-control
            block
            w-full
            px-3
            py-1.5
            text-base
            font-normal
            text-gray-700
            bg-white bg-clip-padding
            border border-solid border-gray-300
            rounded
            transition
            ease-in-out
            m-0
            focus:text-gray-700
            focus:bg-white
            focus:border-blue-600
            focus:outline-none
          "
          id="name"
          aria-describedby="emailHelp"
          placeholder="Enter name"
        />
        <label
          for="Event-Name"
          class="form-label inline-block mb-2 text-gray-700"
          >Event Name</label
        >
        <input
          type="text"
          v-model="eventName"
          class="
            form-control
            block
            w-full
            px-3
            py-1.5
            text-base
            font-normal
            text-gray-700
            bg-white bg-clip-padding
            border border-solid border-gray-300
            rounded
            transition
            ease-in-out
            m-0
            focus:text-gray-700
            focus:bg-white
            focus:border-blue-600
            focus:outline-none
          "
          id="Event-Name"
          aria-describedby="emailHelp"
          placeholder="Enter Event Name"
        />

        <label
          for="start-time"
          class="form-label inline-block mb-2 text-gray-700"
          >Start Date</label
        >
        <input
          type="datetime-local"
          v-model="startDate"
          class="
            form-control
            block
            w-full
            px-3
            py-1.5
            text-base
            font-normal
            text-gray-700
            bg-white bg-clip-padding
            border border-solid border-gray-300
            rounded
            transition
            ease-in-out
            m-0
            focus:text-gray-700
            focus:bg-white
            focus:border-blue-600
            focus:outline-none
          "
          id="start-time"
          aria-describedby="emailHelp"
          placeholder="Enter Event start date"
        />

        <label
          for="start-time"
          class="form-label inline-block mb-2 text-gray-700"
          >End Date</label
        >
        <input
          type="datetime-local"
          v-model="endDate"
          class="
            form-control
            block
            w-full
            px-3
            py-1.5
            text-base
            font-normal
            text-gray-700
            bg-white bg-clip-padding
            border border-solid border-gray-300
            rounded
            transition
            ease-in-out
            m-0
            focus:text-gray-700
            focus:bg-white
            focus:border-blue-600
            focus:outline-none
          "
          id="start-time"
          aria-describedby="emailHelp"
          placeholder="Enter Event end date"
        />
      </div>

      <button
        @click="addEvent"
        class="
          px-6
          py-2.5
          bg-blue-600
          text-white
          font-medium
          text-xs
          leading-tight
          uppercase
          rounded
          shadow-md
          hover:bg-blue-700 hover:shadow-lg
          focus:bg-blue-700 focus:shadow-lg focus:outline-none focus:ring-0
          active:bg-blue-800 active:shadow-lg
          transition
          duration-150
          ease-in-out
        "
      >
        Submit
      </button>
    </form>
  </div>

  <div class="table">
    <table>
      <tr>
        <th>Name</th>
        <th>Event Name</th>

        <th>Start Date</th>

        <th>End Date</th>
      </tr>
      <tbody v-for="event in events" :key="this.id">
        <td>{{ event.name }}</td>
        <td>{{ event.eventName }}</td>
        <td>{{ dateConvert(event.startDate) }}</td>
        <td>{{ dateConvert(event.endDate) }}</td>
      </tbody>
    </table>
  </div>
</template>

<script>
// import Registeration from "./components/registeration.vue";
// import EventList from "./components/EventList.vue";

// import { arrayBuffer } from "stream/consumers"

export default {
  name: "App",
  components: {
    // Registeration,
    // EventList,
  },
  data() {
    return {
      q: 0,
      name: "",
      eventName: "",
      startDate: "",
      endDate: "",
      events: [],
      conflict: [],
      newElementIndex: null,
    };
  },
  //   computed: {
  //     sortedItems: function() {
  //         this.events.sort( ( a, b) => {
  //             return new Date(a.startDate) - new Date(b.endDate);
  //         });
  //         return this.events;
  //     }
  // },
  methods: {
    addEvent(e) {
      e.preventDefault();

      this.events.push({
        id: this.q,
        name: this.name,
        eventName: this.eventName,
        startDate: new Date(this.startDate),
        endDate: new Date(this.endDate),
      });
   

      this.events.sort((a, b) => {
        return new Date(a.startDate) - new Date(b.startDate);
      });
      console.log(this.events);

      // find index
      this.newElementIndex = (() => {
        for (let i = 0; i < this.events.length; i++) {
          if (this.events[i].id === this.q) {
            return i;
          }
        }
      })();
      console.log(this.newElementIndex);

      //upper conflict
      if(this.newElementIndex>0){
        for (let i = this.newElementIndex-1; i <= 0; i++) {
          let startDateOfNewEvents = new Date(this.events[this.newElementIndex].startDate);
          console.log("strtDatNw:",startDateOfNewEvents);
          let endDateOfUpperEvents  = new Date(this.events[i].endDate);
          console.log("endDtupr:",endDateOfUpperEvents);
          if(endDateOfUpperEvents>startDateOfNewEvents){
            this.conflict.push(this.events[i])
            console.log("conflict:",this.events[i]);
            console.log("conArr:",conflict);
          }
          
          
        }






      }
      

      this.q++;
    },
    dateConvert(a) {
      return new Date(a).toLocaleString();
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
th {
  padding: 50px;
  margin: 10px;
  border-right: 2px solid black;
}
</style>
