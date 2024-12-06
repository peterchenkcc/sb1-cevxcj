<template>
  <Page>
    <ActionBar>
      <GridLayout columns="auto, *" class="w-full">
        <Label col="0" text="🚢" class="text-2xl ml-2"/>
        <Label col="1" text="Cruise Booking" class="font-bold text-lg"/>
      </GridLayout>
    </ActionBar>

    <ScrollView>
      <StackLayout class="p-4">
        <!-- Search Section -->
        <StackLayout class="bg-white rounded-lg p-4 shadow-sm mb-4">
          <Label text="Find Your Dream Cruise" class="text-xl font-bold mb-2 text-blue-600"/>
          <TextField hint="Where to?" class="mb-2 p-3 border rounded"/>
          <TextField hint="When?" class="mb-2 p-3 border rounded"/>
          <Button text="Search Cruises" class="bg-blue-500 text-white font-bold p-3 rounded"/>
        </StackLayout>

        <!-- Featured Deals -->
        <Label text="Featured Deals" class="text-lg font-bold mb-2"/>
        <ScrollView orientation="horizontal" class="mb-4">
          <StackLayout orientation="horizontal">
            <StackLayout v-for="(deal, index) in featuredDeals" :key="index" 
                        class="mr-4 bg-white rounded-lg shadow-sm" width="300">
              <Image :src="deal.image" stretch="aspectFill" height="150" class="rounded-t-lg"/>
              <StackLayout class="p-3">
                <Label :text="deal.destination" class="font-bold"/>
                <Label :text="deal.duration" class="text-gray-500"/>
                <Label :text="'From $' + deal.price" class="text-blue-600 font-bold"/>
              </StackLayout>
            </StackLayout>
          </StackLayout>
        </ScrollView>

        <!-- Popular Destinations -->
        <Label text="Popular Destinations" class="text-lg font-bold mb-2"/>
        <GridLayout rows="auto, auto" columns="*, *" class="mb-4">
          <StackLayout v-for="(dest, index) in popularDestinations" :key="index"
                      :row="Math.floor(index/2)" :col="index%2"
                      class="m-1 bg-white rounded-lg shadow-sm">
            <Image :src="dest.image" stretch="aspectFill" height="100" class="rounded-t-lg"/>
            <Label :text="dest.name" class="p-2 font-bold text-center"/>
          </StackLayout>
        </GridLayout>
      </StackLayout>
    </ScrollView>
  </Page>
</template>

<script lang="ts">
import Vue from "nativescript-vue";

export default Vue.extend({
  data() {
    return {
      featuredDeals: [
        {
          destination: "Caribbean Paradise",
          duration: "7 Days",
          price: "599",
          image: "~/images/caribbean.jpg"
        },
        {
          destination: "Mediterranean Dream",
          duration: "10 Days",
          price: "899",
          image: "~/images/mediterranean.jpg"
        },
        {
          destination: "Alaska Adventure",
          duration: "8 Days",
          price: "799",
          image: "~/images/alaska.jpg"
        }
      ],
      popularDestinations: [
        { name: "Caribbean", image: "~/images/caribbean.jpg" },
        { name: "Mediterranean", image: "~/images/mediterranean.jpg" },
        { name: "Alaska", image: "~/images/alaska.jpg" },
        { name: "Hawaii", image: "~/images/hawaii.jpg" }
      ]
    };
  }
});
</script>

<style lang="scss" scoped>
.shadow-sm {
  elevation: 2;
}
</style>
</template>