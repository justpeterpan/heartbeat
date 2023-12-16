<!--
// v0 by Vercel.
// https://v0.dev/t/RdBQBFdGZft
-->
<template>
  <ClientOnly>
    <div class="flex flex-col justify-center gap-2 h-screen m-2">
      <div
        class="rounded-lg border bg-card text-card-foreground shadow-sm"
        data-v0-t="card"
      >
        <div class="flex flex-col space-y-1.5 p-6">
          <h3 class="text-2xl font-semibold leading-none tracking-tight">
            ❤️ Beat
          </h3>
          <p class="text-sm font-light text-neutral-400">
            Record your blood pressure, pulse, date, and time
          </p>
        </div>
        <div class="p-6">
          <form class="space-y-4">
            <div class="grid grid-cols-2 gap-4">
              <div class="space-y-2">
                <label
                  class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
                  for="systolic"
                >
                  Systolic </label
                ><input
                  v-model="form.systolic"
                  class="flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50"
                  id="systolic"
                  placeholder="Enter systolic blood pressure"
                  type="number"
                />
              </div>
              <div class="space-y-2">
                <label
                  class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
                  for="diastolic"
                >
                  Diastolic </label
                ><input
                  v-model="form.diastolic"
                  class="flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50"
                  id="diastolic"
                  placeholder="Enter diastolic blood pressure"
                  type="number"
                />
              </div>
            </div>
            <div class="space-y-2">
              <label
                class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
                for="pulse"
              >
                Pulse Rate </label
              ><input
                v-model="form.pulse"
                class="flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50"
                id="pulse"
                placeholder="Enter pulse rate"
                type="number"
              />
            </div>
            <div class="grid grid-cols-2 gap-4">
              <div class="space-y-2">
                <label
                  class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
                  for="date"
                >
                  Date </label
                ><input
                  v-model="form.date"
                  class="flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50"
                  id="date"
                  placeholder="Select date"
                  type="date"
                />
              </div>
              <div class="space-y-2">
                <label
                  class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
                  for="time"
                >
                  Time </label
                ><input
                  v-model="form.time"
                  class="flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50"
                  id="time"
                  placeholder="Select time"
                  type="time"
                />
              </div>
            </div>
          </form>
        </div>
        <div class="flex items-center p-6">
          <button class="mr-auto bg-white text-black">Reset</button>
          <button
            class="inline-flex items-center justify-center rounded-md text-sm font-medium ring-offset-background focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 h-10 px-4 py-2 ml-2 bg-black hover:bg-gray-800 transition-all duration-200 text-white shadow-lg"
            @click="save"
          >
            <span class="button_top"> Save </span>
          </button>
        </div>
      </div>

      <div v-if="entries.length">
        <div
          class="rounded-lg border bg-card text-card-foreground shadow-sm"
          data-v0-t="card"
        >
          <div class="flex flex-col space-y-1.5 p-6">
            <h3 class="text-2xl font-semibold leading-none tracking-tight">
              Saved Entries
            </h3>
          </div>
          <div class="p-6 overflow-x-auto">
            <table class="min-w-full divide-y divide-gray-200">
              <caption class="hidden">
                Description of the table
              </caption>
              <thead>
                <tr>
                  <th
                    class="px-6 py-3 bg-gray-50 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                  >
                    Date
                  </th>
                  <th
                    class="px-6 py-3 bg-gray-50 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                  >
                    Time
                  </th>
                  <th
                    class="px-6 py-3 bg-gray-50 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                  >
                    Systolic
                  </th>
                  <th
                    class="px-6 py-3 bg-gray-50 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                  >
                    Diastolic
                  </th>
                  <th
                    class="px-6 py-3 bg-gray-50 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                  >
                    Pulse
                  </th>
                </tr>
              </thead>
              <tbody class="bg-white divide-y divide-gray-200">
                <tr v-for="(entry, index) in entries" :key="index">
                  <td class="px-6 py-4 whitespace-nowrap">{{ entry.date }}</td>
                  <td class="px-6 py-4 whitespace-nowrap">{{ entry.time }}</td>
                  <td class="px-6 py-4 whitespace-nowrap">
                    {{ entry.systolic }}
                  </td>
                  <td class="px-6 py-4 whitespace-nowrap">
                    {{ entry.diastolic }}
                  </td>
                  <td class="px-6 py-4 whitespace-nowrap">{{ entry.pulse }}</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </ClientOnly>
</template>

<script setup lang="ts">
import { useStorage } from '@vueuse/core'

interface Entry {
  date: string
  time: string
  systolic: string
  diastolic: string
  pulse: string
}

const state = useStorage<Set<Entry>>('beat', new Set())

const form = reactive({
  date: '',
  time: '',
  systolic: '',
  diastolic: '',
  pulse: '',
})

const save = () => {
  state.value.add(form)
}

const entries = computed(() => {
  return [...state.value]
})
</script>
