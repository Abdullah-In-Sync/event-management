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
      <tbody v-for="event in events">
        <td>{{ event.name }}</td>
        <td>{{ event.eventName }}</td>
        <td>{{ event.startDate }}</td>
        <td>{{ event.endDate }}</td>
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
      name: "",
      eventName: "",
      startDate: "",
      endDate: "",
      events: [],
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

      if (this.events.length > 1) {
       
        this.events.push({
          name: this.nkame,
          eventName: this.eventName,
          startDate: this.startDate,
          endDate: this.endDate,
        });

         this.events.sort((a, b) => {
          return new Date(a.startDate) - new Date(b.tartDate);
        });
        console.log(this.events);
      } else {
        this.events.push({
          name: this.name,
          eventName: this.eventName,
          startDate: this.startDate,
          endDate: this.endDate,
        });
      }
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
  padding: 20px;
  margin: 10px;
}
</style>
