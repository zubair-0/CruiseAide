<template>
  <v-app dark>
    <v-navigation-drawer
      persistent
      :mini-variant="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      fixed
      app
    >
      <v-list>
        <v-list-tile
          value="true"
          v-for="item in items"
          :key="item.title"
          @click="item.call"
          v-bind:disabled="item.disabled"
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      app
      :clipped-left="clipped"
      :scroll-off-screen=false
    >
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon v-html="miniVariant ? 'chevron_right' : 'chevron_left'"></v-icon>
      </v-btn>
      <v-btn icon @click.stop="clipped = !clipped">
        <v-icon>web</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-menu bottom offset-y>
        <v-btn slot="activator"><v-icon left dark>add_box</v-icon>Add</v-btn>
        <v-list>
          <v-list-tile v-for="adder in adders" :key="adder.title" @click="adder.call">
            <v-list-tile-title><v-icon left dark class="mr-2" v-html="adder.icon"></v-icon>{{ adder.title }}</v-list-tile-title>
          </v-list-tile>
        </v-list>
      </v-menu>
      <v-toolbar-items v-for="button in buttons" :key="button.title">
        <v-btn v-on:click="button.call" flat><v-icon left dark v-html="button.icon"></v-icon>{{button.title}}</v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-content v-if="homePage"> <!-- Insert Main Content here -->
      <section>
        <v-parallax :src="require('@/assets/center.jpg')" height="550">
          <v-layout
            column
            align-center
            justify-center
            class="white--text"
          >
            <img :src="require('@/assets/logo.png')" alt="Vuetify.js">
            <h1 class="white--text mb-2 display-3 text-xs-center" style="font-size: 50px;">CruiseAide</h1>
            <div class="subheading mb-3 text-xs-center">Know Your Journey</div>
            <v-btn
              class="blue lighten-2 mt-5"
              dark
              large
              href="#"
            >
              Get Started
            </v-btn>
          </v-layout>
        </v-parallax>
      </section>
      <section>
        <v-layout
          column
          wrap
          class="my-5"
          align-center
        >
          <v-flex xs12 sm4 class="my-3">
            <div class="text-xs-center">
              <h2 class="headline">Best Platform For An Adventurer</h2>
              <span class="subheading">
                Cras facilisis mi vitae nunc 
              </span>
            </div>
          </v-flex>
          <v-flex xs12>
            <v-container grid-list-xl>
              <v-layout row wrap align-center>
                <v-flex xs12 md4>
                  <v-card class="elevation-0 transparent">
                    <v-card-text class="text-xs-center">
                      <v-icon x-large class="blue--text text--lighten-2">color_lens</v-icon>
                    </v-card-text>
                    <v-card-title primary-title class="layout justify-center">
                      <div class="headline text-xs-center">Material Design</div>
                    </v-card-title>
                    <v-card-text>
                      Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare. 
                      Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. 
                      Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti. 
                    </v-card-text>
                  </v-card>
                </v-flex>
                <v-flex xs12 md4>
                  <v-card class="elevation-0 transparent">
                    <v-card-text class="text-xs-center">
                      <v-icon x-large class="blue--text text--lighten-2">flash_on</v-icon>
                    </v-card-text>
                    <v-card-title primary-title class="layout justify-center">
                      <div class="headline">Fast development</div>
                    </v-card-title>
                    <v-card-text>
                      Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare. 
                      Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. 
                      Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti. 
                    </v-card-text>
                  </v-card>
                </v-flex>
                <v-flex xs12 md4>
                  <v-card class="elevation-0 transparent">
                    <v-card-text class="text-xs-center">
                      <v-icon x-large class="blue--text text--lighten-2">build</v-icon>
                    </v-card-text>
                    <v-card-title primary-title class="layout justify-center">
                      <div class="headline text-xs-center">Completely Open Sourced</div>
                    </v-card-title>
                    <v-card-text>
                      Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare. 
                      Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. 
                      Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti. 
                    </v-card-text>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-container>
          </v-flex>
        </v-layout>
      </section>
      <section>
        <v-parallax :src="require('@/assets/2.jpg')" height="550">
          <v-layout column align-center justify-center>
            <div class="headline white--text mb-3 text-xs-center">Web development has never been easier</div>
            <em>Kick-start your application today</em>
            <v-btn
              class="blue lighten-2 mt-5"
              dark
              large
              href="#"
            >
              Get Started
            </v-btn>
          </v-layout>
        </v-parallax>
      </section>
      <section>
        <v-container grid-list-xl>
          <v-layout row wrap justify-center class="my-5">
            <v-flex xs12 sm4>
              <v-card class="elevation-0 transparent">
                <v-card-title primary-title class="layout justify-center">
                  <div class="headline">Company info</div>
                </v-card-title>
                <v-card-text>
                  Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare. 
                  Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. 
                  Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti. 
                </v-card-text>
              </v-card>
            </v-flex>
            <v-flex xs12 sm4 offset-sm1>
              <v-card class="elevation-0 transparent">
                <v-card-title primary-title class="layout justify-center">
                  <div class="headline">Contact us</div>
                </v-card-title>
                <v-card-text>
                  Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare.
                </v-card-text>
                <v-list class="transparent">
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">phone</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>777-867-5309</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">place</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>Chicago, US</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">email</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>john@vuetifyjs.com</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                </v-list>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </section>
    </v-content>

    <v-content v-if="attractionsPage"> <!-- Content Of Attractions Page Start From Here -->
      <section>
        <v-parallax :src="require('@/assets/main.jpg')" height="550">
          <v-layout
            column
            align-center
            justify-center
            class="white--text"
          >
            <img :src="require('@/assets/logo.png')" alt="Vuetify.js">
            <h1 class="white--text mb-2 display-1 text-xs-center">Attractions</h1>
            <div class="subheading mb-3 text-xs-center">Explore The Beauty Around The World</div>
            <v-btn
              class="blue lighten-2 mt-5"
              dark
              large
              href="#"
            >
              Explore
            </v-btn>
          </v-layout>
        </v-parallax>
      </section>
      <section>
        <v-layout
          column
          wrap
          class="my-5"
          align-center
        >
          <v-flex xs12 sm4 class="my-3">
            <div class="text-xs-center">
              <h2 class="headline">Popular Attractions Around The World</h2>
              <span class="subheading">
                Live Your Dream
              </span>
            </div>
          </v-flex>
          <v-flex xs12>
            <v-container grid-list-md text-xs-center>
              <v-layout row wrap>
                <v-flex xs8 offset-xs2>
                  <v-text-field
                  label="Search By Name or City"
                  single-line
                  append-icon="search"
                  v-model="search"
                  @keyup="filterResults"
                  ></v-text-field>
                </v-flex>
                <v-flex class="my-3" xs12 sm6 md4 lg3 v-for="place in filteredAttractions" :key="place.title">
                  <v-card>
                    <v-card-media
                      v-bind:src="place.image"
                      height="200px"
                    >
                    </v-card-media>
                    <v-card-title primary-title>
                      <div class="text-xs-left">
                        <div class="headline">{{place.title}}</div>
                        <span class="grey--text">{{place.city}}, {{place.country}}</span>
                      </div>
                    </v-card-title>
                    <v-card-actions>
                      <v-btn flat>Share</v-btn>
                      <v-btn flat color="primary">Details</v-btn>
                      <v-spacer></v-spacer>
                    </v-card-actions>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-container>
          </v-flex>
        </v-layout>
      </section>
      <section>
        <v-parallax :src="require('@/assets/2.jpg')" height="550">
          <v-layout column align-center justify-center>
            <div class="headline white--text mb-3 text-xs-center">Sightseeing has never been more fun</div>
            <em>Don't Miss Out And Start Exploring Today</em>
            <v-btn
              class="blue lighten-2 mt-5"
              dark
              large
              href="#"
            >
              Get Started
            </v-btn>
          </v-layout>
        </v-parallax>
      </section>
      <section>
        <v-container grid-list-xl>
          <v-layout row wrap justify-center class="my-5">
            <v-flex xs12 sm4>
              <v-card class="elevation-0 transparent">
                <v-card-title primary-title class="layout justify-center">
                  <div class="headline">Company info</div>
                </v-card-title>
                <v-card-text>
                  Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare. 
                  Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. 
                  Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti. 
                </v-card-text>
              </v-card>
            </v-flex>
            <v-flex xs12 sm4 offset-sm1>
              <v-card class="elevation-0 transparent">
                <v-card-title primary-title class="layout justify-center">
                  <div class="headline">Contact us</div>
                </v-card-title>
                <v-card-text>
                  Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare.
                </v-card-text>
                <v-list class="transparent">
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">phone</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>777-867-5309</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">place</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>Chicago, US</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">email</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>john@vuetifyjs.com</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                </v-list>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </section>
    </v-content>

    <v-content v-if="restaurantsPage"> <!-- Content Of Restaurants Page Start From Here -->
      <section>
        <v-parallax :src="require('@/assets/main.jpg')" height="550">
          <v-layout
            column
            align-center
            justify-center
            class="white--text"
          >
            <img :src="require('@/assets/logo.png')" alt="Vuetify.js">
            <h1 class="white--text mb-2 display-1 text-xs-center">Restaurants</h1>
            <div class="subheading mb-3 text-xs-center">Eat All Kinds of Foods Around The World</div>
            <v-btn
              class="blue lighten-2 mt-5"
              dark
              large
              href="#"
            >
              Explore
            </v-btn>
          </v-layout>
        </v-parallax>
      </section>
      <section>
        <v-layout
          column
          wrap
          class="my-5"
          align-center
        >
          <v-flex xs12 sm4 class="my-3">
            <div class="text-xs-center">
              <h2 class="headline">Popular Restaurants Around The World</h2>
              <span class="subheading">
                Become A Foodie
              </span>
            </div>
          </v-flex>
          <v-flex xs12>
            <v-container grid-list-md text-xs-center>
              <v-layout row wrap>
                <v-flex xs8 offset-xs2>
                  <v-text-field
                  label="Search By Name or City"
                  single-line
                  append-icon="search"
                  v-model="search"
                  @keyup="filterResults"
                  ></v-text-field>
                </v-flex>
                <v-flex xs8 offset-xs2 v-model="showFilters">
                  <v-expansion-panel expand>
                    <v-expansion-panel-content>
                      <div slot="header">Cuisine</div>
                      <v-container fluid px-0>
                        <v-checkbox
                          label="Italian"
                          v-model="restaurantFilters.cuisines"
                          @change="filterResults"
                          value="Italian"
                        ></v-checkbox>
                        <v-checkbox
                          label="Chinese"
                          v-model="restaurantFilters.cuisines"
                          @change="filterResults"
                          value="Chinese"
                        ></v-checkbox>
                        <v-checkbox
                          label="English"
                          v-model="restaurantFilters.cuisines"
                          @change="filterResults"
                          value="English"
                        ></v-checkbox>
                      </v-container>
                    </v-expansion-panel-content>
                    <v-expansion-panel-content>
                      <div slot="header">Features</div>
                      <v-container fluid px-0>
                        <v-checkbox
                          label="Delivery"
                          v-model="restaurantFilters.features"
                          @change="filterResults"
                          value="Delivery"
                        ></v-checkbox>
                      </v-container>
                    </v-expansion-panel-content>
                  </v-expansion-panel>
                </v-flex>
                <v-flex class="my-3" xs12 sm6 md4 lg3 v-for="restaurant in filteredRestaurants" :key="restaurant.title">
                  <v-card>
                    <v-card-media
                      v-bind:src="restaurant.image"
                      height="200px"
                    >
                    </v-card-media>
                    <v-card-title primary-title>
                      <div class="text-xs-left">
                        <div class="headline">{{restaurant.title}}</div>
                        <span class="grey--text">{{restaurant.city}}, {{restaurant.country}}</span>
                        <br>
                        <span class="grey--text">Cuisine: {{restaurant.cuisine}}</span>
                      </div>
                    </v-card-title>
                    <v-card-actions>
                      <v-btn flat>Share</v-btn>
                      <v-btn flat color="primary">Details</v-btn>
                      <v-spacer></v-spacer>
                    </v-card-actions>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-container>
          </v-flex>
        </v-layout>
      </section>
      <section>
        <v-parallax :src="require('@/assets/2.jpg')" height="550">
          <v-layout column align-center justify-center>
            <div class="headline white--text mb-3 text-xs-center">Sightseeing has never been more fun</div>
            <em>Don't Miss Out And Start Exploring Today</em>
            <v-btn
              class="blue lighten-2 mt-5"
              dark
              large
              href="#"
            >
              Get Started
            </v-btn>
          </v-layout>
        </v-parallax>
      </section>
      <section>
        <v-container grid-list-xl>
          <v-layout row wrap justify-center class="my-5">
            <v-flex xs12 sm4>
              <v-card class="elevation-0 transparent">
                <v-card-title primary-title class="layout justify-center">
                  <div class="headline">Company info</div>
                </v-card-title>
                <v-card-text>
                  Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare. 
                  Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. 
                  Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti. 
                </v-card-text>
              </v-card>
            </v-flex>
            <v-flex xs12 sm4 offset-sm1>
              <v-card class="elevation-0 transparent">
                <v-card-title primary-title class="layout justify-center">
                  <div class="headline">Contact us</div>
                </v-card-title>
                <v-card-text>
                  Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare.
                </v-card-text>
                <v-list class="transparent">
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">phone</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>777-867-5309</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">place</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>Chicago, US</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">email</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>john@vuetifyjs.com</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                </v-list>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </section>
    </v-content>

    <v-content v-if="accomodationPage"> <!-- Content Of Accomodation Page Start From Here -->
      <section>
        <v-parallax :src="require('@/assets/main.jpg')" height="550">
          <v-layout
            column
            align-center
            justify-center
            class="white--text"
          >
            <img :src="require('@/assets/logo.png')" alt="Vuetify.js">
            <h1 class="white--text mb-2 display-1 text-xs-center">Accomodation</h1>
            <div class="subheading mb-3 text-xs-center">Get The Best Living Standards wherever You Go</div>
            <v-btn
              class="blue lighten-2 mt-5"
              dark
              large
              href="#"
            >
              Explore
            </v-btn>
          </v-layout>
        </v-parallax>
      </section>
      <section>
        <v-layout
          column
          wrap
          class="my-5"
          align-center
        >
          <v-flex xs12 sm4 class="my-3">
            <div class="text-xs-center">
              <h2 class="headline">Popular Hotels Around The World</h2>
              <span class="subheading">
                Live Luxurious Life
              </span>
            </div>
          </v-flex>
          <v-flex xs12>
            <v-container grid-list-md text-xs-center>
              <v-layout row wrap>
                <v-flex xs8 offset-xs2>
                  <v-text-field
                  label="Search By Name or City"
                  single-line
                  append-icon="search"
                  v-model="search"
                  @keyup="filterResults"
                  ></v-text-field>
                </v-flex>
                <v-flex xs8 offset-xs2>
                  <h1 class="subheading left">Price Range</h1>
                </v-flex>
                <v-flex xs4 offset-xs2>
                  <v-card>
                    <v-card-actions>
                      <v-slider @mouseup="filterResults" :max="20000" v-model="accomodationFilters.price" thumb-label step="500" ticks></v-slider>
                    </v-card-actions>
                  </v-card>
                </v-flex>
                <v-flex xs4>
                  <v-text-field
                    name="input-1-3"
                    label="Hint Text"
                    single-line
                    prepend-icon="monetization_on"
                    v-model="accomodationFilters.price"
                    @keyup="filterResults"
                    disabled="true"
                  ></v-text-field>
                </v-flex>
                <v-flex xs8 offset-xs2 v-model="showFilters">
                  <v-expansion-panel expand>
                    <v-expansion-panel-content>
                      <div slot="header">Type</div>
                      <v-container fluid px-0>
                        <v-checkbox
                          label="Hotel"
                          v-model="accomodationFilters.types"
                          @change="filterResults"
                          value="Hotel"
                        ></v-checkbox>
                        <v-checkbox
                          label="Rental Home"
                          v-model="accomodationFilters.types"
                          @change="filterResults"
                          value="RentalHome"
                        ></v-checkbox>
                      </v-container>
                    </v-expansion-panel-content>
                    <v-expansion-panel-content>
                      <div slot="header">Features</div>
                      <v-container fluid px-0>
                        <v-checkbox
                          label="Gym"
                          v-model="accomodationFilters.features"
                          @change="filterResults"
                          value="Gym"
                        ></v-checkbox>
                        <v-checkbox
                          label="Spa"
                          v-model="accomodationFilters.features"
                          @change="filterResults"
                          value="Spa"
                        ></v-checkbox>
                        <v-checkbox
                          label="Swimming Pool"
                          v-model="accomodationFilters.features"
                          @change="filterResults"
                          value="SwimmingPool"
                        ></v-checkbox>
                      </v-container>
                    </v-expansion-panel-content>
                  </v-expansion-panel>
                </v-flex>
                <v-flex class="my-3" xs12 sm6 md4 lg3 v-for="hotel in filteredAccomodations" :key="hotel.title">
                  <v-card>
                    <v-card-media
                      v-bind:src="hotel.image"
                      height="200px"
                    >
                    </v-card-media>
                    <v-card-title primary-title>
                      <div class="text-xs-left">
                        <div class="headline">{{hotel.title}}</div>
                        <span class="grey--text">{{hotel.city}}, {{hotel.country}}</span>
                        <br>
                        <span class="grey--text">{{hotel.type}}: {{hotel.price}}</span>
                      </div>
                      <div class="text-xs-left">
                        
                      </div>
                    </v-card-title>
                    <v-card-actions>
                      <v-btn flat>Share</v-btn>
                      <v-btn flat color="primary">Details</v-btn>
                      <v-spacer></v-spacer>
                    </v-card-actions>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-container>
          </v-flex>
        </v-layout>
      </section>
      <section>
        <v-parallax :src="require('@/assets/2.jpg')" height="550">
          <v-layout column align-center justify-center>
            <div class="headline white--text mb-3 text-xs-center">Sightseeing has never been more fun</div>
            <em>Don't Miss Out And Start Exploring Today</em>
            <v-btn
              class="blue lighten-2 mt-5"
              dark
              large
              href="#"
            >
              Get Started
            </v-btn>
          </v-layout>
        </v-parallax>
      </section>
      <section>
        <v-container grid-list-xl>
          <v-layout row wrap justify-center class="my-5">
            <v-flex xs12 sm4>
              <v-card class="elevation-0 transparent">
                <v-card-title primary-title class="layout justify-center">
                  <div class="headline">Company info</div>
                </v-card-title>
                <v-card-text>
                  Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare. 
                  Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. 
                  Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti. 
                </v-card-text>
              </v-card>
            </v-flex>
            <v-flex xs12 sm4 offset-sm1>
              <v-card class="elevation-0 transparent">
                <v-card-title primary-title class="layout justify-center">
                  <div class="headline">Contact us</div>
                </v-card-title>
                <v-card-text>
                  Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare.
                </v-card-text>
                <v-list class="transparent">
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">phone</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>777-867-5309</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">place</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>Chicago, US</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">email</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>john@vuetifyjs.com</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                </v-list>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </section>
    </v-content>

    <v-content v-if="travelPage"> <!-- Content Of Travel Page Start From Here -->
      <section>
        <v-parallax :src="require('@/assets/main.jpg')" height="550">
          <v-layout
            column
            align-center
            justify-center
            class="white--text"
          >
            <img :src="require('@/assets/logo.png')" alt="Vuetify.js">
            <h1 class="white--text mb-2 display-1 text-xs-center">Travel</h1>
            <div class="subheading mb-3 text-xs-center">Spread Your Wings And Fly With The Best</div>
            <v-btn
              class="blue lighten-2 mt-5"
              dark
              large
              href="#"
            >
              Explore
            </v-btn>
          </v-layout>
        </v-parallax>
      </section>
      <section>
        <v-layout
          column
          wrap
          class="my-5"
          align-center
        >
          <v-flex xs12 sm4 class="my-3">
            <div class="text-xs-center">
              <h2 class="headline">Airliners Available Around The World</h2>
              <span class="subheading">
                Look Above, Fly High
              </span>
            </div>
          </v-flex>
          <v-flex xs12>
            <v-container grid-list-md text-xs-center>
              <v-layout row wrap>
                <v-flex xs8 offset-xs2>
                  <v-text-field
                  label="Search By Name or City"
                  single-line
                  append-icon="search"
                  v-model="search"
                  @keyup="filterResults"
                  ></v-text-field>
                </v-flex>
                
                <v-flex xs8 offset-xs2 v-model="showFilters">
                  <h1 class="subheading left">Price Range</h1>
                </v-flex>
                <v-flex xs4 offset-xs2 v-model="showFilters">
                  <v-card>
                    <v-card-actions>
                      <v-slider @mouseup="filterResults" :max="20000" v-model="travelFilters.price" thumb-label step="500" ticks></v-slider>
                    </v-card-actions>
                  </v-card>
                </v-flex>
                <v-flex xs4 v-model="showFilters">
                  <v-text-field
                    name="input-1-3"
                    label="Hint Text"
                    single-line
                    prepend-icon="monetization_on"
                    v-model="travelFilters.price"
                    @keyup="filterResults"
                    disabled="true"
                  ></v-text-field>
                </v-flex>
                <v-flex class="mt-4" xs8 offset-xs2 v-model="showFilters">
                  <v-expansion-panel expand>
                    <v-expansion-panel-content>
                      <div slot="header" >Flight Class</div>
                      <v-container fluid px-0>
                        <v-checkbox
                          label="First"
                          v-model="travelFilters.classes"
                          @change="filterResults"
                          value="First"
                        ></v-checkbox>
                        <v-checkbox
                          label="Business"
                          v-model="travelFilters.classes"
                          @change="filterResults"
                          value="Business"
                        ></v-checkbox>
                        <v-checkbox
                          label="Economy"
                          v-model="travelFilters.classes"
                          @change="filterResults"
                          value="Economy"
                        ></v-checkbox>
                      </v-container>
                    </v-expansion-panel-content>
                    <v-expansion-panel-content>
                      <div slot="header" >Select Airlines</div>
                      <v-container fluid px-0>
                        <v-checkbox
                          label="Emirates"
                          v-model="travelFilters.airlines"
                          @change="filterResults"
                          value="Emirates"
                        ></v-checkbox>
                        <v-checkbox
                          label="Qatar Airways"
                          v-model="travelFilters.airlines"
                          @change="filterResults"
                          value="Qatar Airways"
                        ></v-checkbox>
                        <v-checkbox
                          label="Air France"
                          v-model="travelFilters.airlines"
                          @change="filterResults"
                          value="Air France"
                        ></v-checkbox>
                        <v-checkbox
                          label="Air Canada"
                          v-model="travelFilters.airlines"
                          @change="filterResults"
                          value="Air Canada"
                        ></v-checkbox>
                        <v-checkbox
                          label="Japan Airlines"
                          v-model="travelFilters.airlines"
                          @change="filterResults"
                          value="Japan Airlines"
                        ></v-checkbox>
                        <v-checkbox
                          label="Turkish Airlines"
                          v-model="travelFilters.airlines"
                          @change="filterResults"
                          value="Turkish Airlines"
                        ></v-checkbox>
                        <v-checkbox
                          label="Air Blue"
                          v-model="travelFilters.airlines"
                          @change="filterResults"
                          value="Air Blue"
                        ></v-checkbox>
                        <v-checkbox
                          label="Shaheen Airlines"
                          v-model="travelFilters.airlines"
                          @change="filterResults"
                          value="Shaheen Airlines"
                        ></v-checkbox>
                      </v-container>
                    </v-expansion-panel-content>
                  </v-expansion-panel>
                </v-flex>

                <v-flex class="my-3" xs12 sm6 md4 lg3 v-for="flight in filteredTravels" :key="flight.title">
                  <v-card>
                    <v-card-media
                      v-bind:src="flight.image"
                      height="200px"
                    >
                    </v-card-media>
                    <v-card-title primary-title>
                      <div class="text-xs-left">
                        <div class="headline">{{flight.title}}</div>
                        <span class="grey--text">{{flight.srcCity}}, {{flight.srcCountry}} - {{flight.destCity}}, {{flight.destCountry}}</span>
                        <br>
                        <span class="grey--text">{{flight.class}} Class, Price: ${{flight.price}}</span>
                      </div>
                    </v-card-title>
                    <v-card-actions>
                      <v-btn flat>Share</v-btn>
                      <v-btn flat color="primary">Details</v-btn>
                      <v-spacer></v-spacer>
                    </v-card-actions>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-container>
          </v-flex>
        </v-layout>
      </section>
      <section>
        <v-parallax :src="require('@/assets/2.jpg')" height="550">
          <v-layout column align-center justify-center>
            <div class="headline white--text mb-3 text-xs-center">Sightseeing has never been more fun</div>
            <em>Don't Miss Out And Start Exploring Today</em>
            <v-btn
              class="blue lighten-2 mt-5"
              dark
              large
              href="#"
            >
              Get Started
            </v-btn>
          </v-layout>
        </v-parallax>
      </section>
      <section>
        <v-container grid-list-xl>
          <v-layout row wrap justify-center class="my-5">
            <v-flex xs12 sm4>
              <v-card class="elevation-0 transparent">
                <v-card-title primary-title class="layout justify-center">
                  <div class="headline">Company info</div>
                </v-card-title>
                <v-card-text>
                  Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare. 
                  Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. 
                  Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti. 
                </v-card-text>
              </v-card>
            </v-flex>
            <v-flex xs12 sm4 offset-sm1>
              <v-card class="elevation-0 transparent">
                <v-card-title primary-title class="layout justify-center">
                  <div class="headline">Contact us</div>
                </v-card-title>
                <v-card-text>
                  Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare.
                </v-card-text>
                <v-list class="transparent">
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">phone</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>777-867-5309</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">place</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>Chicago, US</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                  <v-list-tile>
                    <v-list-tile-action>
                      <v-icon class="blue--text text--lighten-2">email</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>john@vuetifyjs.com</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                </v-list>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </section>
    </v-content>

    <v-layout row justify-center>
      <v-dialog v-model="addAttractionDialog" max-width="500px">
        <v-card>
          <v-card-title>
            <span class="headline">Add New Attraction Place</span>
          </v-card-title>
          <v-card-text>
            <v-container grid-list-md>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Name" hint="Example: Burj Khalifa" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="City" hint="Example: Dubai" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Country" hint="Example: UAE" required></v-text-field>
                </v-flex>
              </v-layout>
            </v-container>
            <small>*indicates required field</small>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" flat @click.native="addAttractionDialog = false">Close</v-btn>
            <v-btn color="blue darken-1" flat @click.native="addAttractionDialog = false">Add</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-layout>

    <v-layout row justify-center>
      <v-dialog v-model="addRestaurantDialog" max-width="500px">
        <v-card>
          <v-card-title>
            <span class="headline">Add New Restaurant</span>
          </v-card-title>
          <v-card-text>
            <v-container grid-list-md>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Name" hint="Example: Salt N Pepper" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="City" hint="Example: London" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Country" hint="Example: UK" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout row wrap>
                <v-flex xs12>
                  <v-select
                    :items="cuisine"
                    label="Select Cuisine"
                    single-line
                  ></v-select>
                </v-flex>
              </v-layout>
            </v-container>
            <small>*indicates required field</small>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" flat @click.native="addRestaurantDialog = false">Close</v-btn>
            <v-btn color="blue darken-1" flat @click.native="addRestaurantDialog = false">Add</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-layout>

    <v-layout row justify-center>
      <v-dialog v-model="addAccomodationDialog" max-width="500px">
        <v-card>
          <v-card-title>
            <span class="headline">Add New Accomodation</span>
          </v-card-title>
          <v-card-text>
            <v-container grid-list-md>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Name" hint="Example: Pearl Continental" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="City" hint="Example: Lahore" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Country" hint="Example: PK" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout row wrap>
                <v-flex xs12>
                  <v-text-field
                    name="input"
                    label="Price"
                    id="price"
                    mask="#####"
                  ></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout row wrap>
                <v-flex xs12>
                  <v-select
                    :items="accomodationTypes"
                    label="Select Type"
                    single-line
                  ></v-select>
                </v-flex>
              </v-layout>
              <v-layout>
                <v-flex xs12>
                  <v-expansion-panel expand>
                    <v-expansion-panel-content>
                      <div slot="header" >Select Features</div>
                      <v-container fluid px-0>
                        <v-checkbox
                          label="Gym"
                          v-model="restaurantFilters.features"
                          value="Gym"
                        ></v-checkbox>
                        <v-checkbox
                          label="Spa"
                          v-model="restaurantFilters.features"
                          value="Spa"
                        ></v-checkbox>
                        <v-checkbox
                          label="Swimming Pool"
                          v-model="restaurantFilters.features"
                          value="SwimmingPool"
                        ></v-checkbox>
                      </v-container>
                    </v-expansion-panel-content>
                  </v-expansion-panel>
                </v-flex>
              </v-layout>
            </v-container>
            <small>*indicates required field</small>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" flat @click.native="addAccomodationDialog = false">Close</v-btn>
            <v-btn color="blue darken-1" flat @click.native="addAccomodationDialog = false">Login</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-layout>

    <v-layout row justify-center>
      <v-dialog v-model="addTravelDialog" max-width="500px">
        <v-card>
          <v-card-title>
            <span class="headline">Add New Ticket</span>
          </v-card-title>
          <v-card-text>
            <v-container grid-list-md>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Source City" hint="Example: Dubai" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Source Country" hint="Example: UAE" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Destination City" hint="Example: Lahore" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Destination Country" hint="Example: Pakistan" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout row wrap>
                <v-flex xs12>
                  <v-select
                    :items="airlines"
                    label="Select Airline"
                    single-line
                  ></v-select>
                </v-flex>
              </v-layout>
              <v-layout row wrap>
                <v-flex xs12>
                  <v-select
                    :items="flightClasses"
                    label="Flight Class"
                    single-line
                  ></v-select>
                </v-flex>
              </v-layout>
              <v-layout row wrap>
                <v-flex xs12>
                  <v-text-field
                    name="input"
                    label="Price"
                    id="price"
                    mask="#####"
                  ></v-text-field>
                </v-flex>
              </v-layout>
            </v-container>
            <small>*indicates required field</small>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" flat @click.native="addTravelDialog = false">Close</v-btn>
            <v-btn color="blue darken-1" flat @click.native="addTravelDialog = false">Login</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-layout>

    <v-layout row justify-center>
      <v-dialog v-model="loginDialog" max-width="500px">
        <v-card>
          <v-card-title>
            <span class="headline">Login</span>
          </v-card-title>
          <v-card-text>
            <v-container grid-list-md>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Email" hint="Example: john.doe@mail.com" required></v-text-field>
                </v-flex>
              </v-layout>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field label="Password" type="password" required></v-text-field>
                </v-flex>
              </v-layout>
            </v-container>
            <small>*indicates required field</small>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" flat @click.native="loginDialog = false">Close</v-btn>
            <v-btn color="blue darken-1" flat @click.native="loginDialog = false">Login</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-layout>

    <v-layout row justify-center>
      <v-dialog v-model="signupDialog" max-width="500px">
        <v-card>
          <v-card-title>
            <span class="headline">SignUp</span>
          </v-card-title>
          <v-card-text>
            <v-container grid-list-md>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field
                    label="Full Name"
                    hint="Example: John Doe"
                    required>
                  </v-text-field>
                </v-flex>
                <v-flex xs12>
                  <v-text-field label="Email" hint="Example: john.doe@mail.com" required></v-text-field>
                </v-flex>
                <v-flex xs12>
                  <v-text-field label="Password" type="password" required></v-text-field>
                </v-flex>
                <v-flex xs12>
                  <v-text-field label="Confirm Password" type="password" required></v-text-field>
                </v-flex>
                <v-flex xs12>
                  <v-select
                    label="Age"
                    required
                    :items="['0-17', '18-29', '30-54', '54+']"
                  ></v-select>
                </v-flex>
              </v-layout>
            </v-container>
            <small>*indicates required field</small>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" flat @click.native="signupDialog = false">Close</v-btn>
            <v-btn color="blue darken-1" flat @click.native="signupDialog = false">SignUp</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-layout>

    <v-footer :fixed="fixed" app>
      <span>&copy; CruiseAide 2017</span>
    </v-footer>
  </v-app>
</template>

<script>
/* eslint semi: ["error", "always"] */
export default {
  data () {
    return {
      items: [
        {
          icon: 'home',
          title: 'Home',
          disabled: true,
          call: this.homeClicked
        },
        {
          icon: 'favorite_border',
          title: 'Attractions',
          disabled: false,
          call: this.attractionsClicked
        },
        {
          icon: 'restaurant',
          title: 'Restaurants',
          disabled: false,
          call: this.restaurantsClicked
        },
        {
          icon: 'hotel',
          title: 'Accomodation',
          disabled: false,
          call: this.accomodationClicked
        },
        {
          icon: 'flight_takeoff',
          title: 'Travel',
          disabled: false,
          call: this.travelClicked
        }
      ],
      adders: [
        {
          icon: 'favorite_border',
          title: 'Attractions',
          call: this.addAttraction
        },
        {
          icon: 'restaurant',
          title: 'Restaurants',
          call: this.addRestaurant
        },
        {
          icon: 'hotel',
          title: 'Accomodation',
          call: this.addAccomodation
        },
        {
          icon: 'flight_takeoff',
          title: 'Travel',
          disabled: false,
          call: this.addTravel
        }
      ],
      buttons: [
        {
          icon: 'input',
          title: 'Login',
          call: this.login
        },
        {
          icon: 'create',
          title: 'SignUp',
          call: this.signup
        }
      ],
      attractions: [
        {
          title: 'Burj Khalifa',
          city: 'Dubai',
          country: 'UAE',
          image: require('@/assets/attractions/burj.jpg')
        },
        {
          title: 'Eiffel Tower',
          city: 'Paris',
          country: 'France',
          image: require('@/assets/attractions/eiffel.jpg')
        },
        {
          title: 'Toronto Tower',
          city: 'Toronto',
          country: 'Canada',
          image: require('@/assets/attractions/tower.jpg')
        },
        {
          title: 'Shibuya',
          city: 'Tokyo',
          country: 'Japan',
          image: require('@/assets/attractions/shibu.jpg')
        }
      ],
      restaurants: [
        {
          title: 'Burj Khalifa',
          city: 'Dubai',
          country: 'UAE',
          features: [],
          cuisine: 'Arabic',
          image: require('@/assets/restaurants/bkrestaurant.jpg')
        },
        {
          title: 'Salt N Pepper',
          city: 'London',
          country: 'UK',
          features: [],
          cuisine: 'English',
          image: require('@/assets/restaurants/snp.jpg')
        },
        {
          title: 'Papa John\'s',
          city: 'New York',
          country: 'USA',
          features: [],
          cuisine: 'Italian',
          image: require('@/assets/restaurants/pjs.jpg')
        },
        {
          title: 'Okonomiyaki Kiji',
          city: 'Osaka',
          country: 'Japan',
          features: [],
          cuisine: 'Japanese',
          image: require('@/assets/restaurants/oko.jpg')
        }
      ],
      accomodations: [
        {
          title: 'Emirates Palace',
          city: 'Abu Dhabi',
          country: 'UAE',
          features: [],
          price: 1500,
          type: 'Hotel',
          image: require('@/assets/accomodation/ephotel.jpg')
        },
        {
          title: 'Burj Khalifa',
          city: 'Dubai',
          country: 'UAE',
          features: [],
          price: 2000,
          type: 'Hotel',
          image: require('@/assets/accomodation/bkhotel.jpg')
        },
        {
          title: 'The Plaza',
          city: 'New York',
          country: 'USA',
          features: [],
          price: 1200,
          type: 'Hotel',
          image: require('@/assets/accomodation/tphotel.jpg')
        },
        {
          title: 'The Westin Excelsior',
          city: 'Rome',
          country: 'Italy',
          features: [],
          price: 950,
          type: 'Hotel',
          image: require('@/assets/accomodation/twehotel.jpg')
        },
        {
          title: '25 Westwoord Drive',
          city: 'Lahore',
          country: 'Pakistan',
          features: [],
          price: 500,
          type: 'RentalHome',
          image: require('@/assets/accomodation/wdroom.jpg')
        },
        {
          title: 'The Boulders',
          city: 'Arizona',
          country: 'USA',
          features: [],
          price: 600,
          type: 'Hotel',
          image: require('@/assets/accomodation/tbhotel.jpg')
        }
      ],
      travels: [
        {
          title: 'Emirates',
          srcCity: 'Dubai',
          srcCountry: 'UAE',
          destCity: 'Lahore',
          destCountry: 'Pakistan',
          class: 'Business',
          price: 700,
          image: require('@/assets/airlines/emirates.png')
        },
        {
          title: 'Air France',
          srcCity: 'London',
          srcCountry: 'UK',
          destCity: 'Paris',
          destCountry: 'France',
          class: 'Business',
          price: 200,
          image: require('@/assets/airlines/airfrance.png')
        },
        {
          title: 'Turkish Airlines',
          srcCity: 'Lahore',
          srcCountry: 'Pakistan',
          destCity: 'Istanbul',
          destCountry: 'Turkey',
          class: 'First',
          price: 1000,
          image: require('@/assets/airlines/turkish.jpg')
        },
        {
          title: 'Japan Airlines',
          srcCity: 'Tokyo',
          srcCountry: 'Japan',
          destCity: 'Dubai',
          destCountry: 'UAE',
          class: 'Business',
          price: 2800,
          image: require('@/assets/airlines/jal.png')
        },
        {
          title: 'Qatar Airways',
          srcCity: 'Abu Dhabi',
          srcCountry: 'UAE',
          destCity: 'Islamabad',
          destCountry: 'Pakistan',
          class: 'Economy',
          price: 200,
          image: require('@/assets/airlines/qatar.png')
        },
        {
          title: 'Air Blue',
          srcCity: 'Dubai',
          srcCountry: 'UAE',
          destCity: 'Lahore',
          destCountry: 'Pakistan',
          class: 'Economy',
          price: 150,
          image: require('@/assets/airlines/airblue.jpg')
        },
        {
          title: 'Shaheen Airlines',
          srcCity: 'Lahore',
          srcCountry: 'Pakistan',
          destCity: 'Karachi',
          destCountry: 'Pakistan',
          class: 'Business',
          price: 180,
          image: require('@/assets/airlines/shaheen.jpg')
        },
        {
          title: 'Air Canada',
          srcCity: 'New York',
          srcCountry: 'USA',
          destCity: 'Toronto',
          destCountry: 'Canada',
          class: 'Business',
          price: 300,
          image: require('@/assets/airlines/aircanada.jpg')
        }
      ],
      airlines: [
        'Emirates', 'Air France', 'Turkish Airlines', 'Japan Airlines', 'Air Blue', 'Shaheen Airlines', 'PIA', 'Air Canada'
      ],
      restaurantFilters: {
        cuisines: [],
        features: []
      },
      accomodationFilters: {
        price: 20000,
        types: [],
        features: []
      },
      travelFilters: {
        price: 20000,
        classes: [],
        airlines: []
      },
      cuisine: ['Italian', 'Chinese', 'English'],
      accomodationTypes: ['Hotel', 'Rental House'],
      flightClasses: ['First', 'Business', 'Economy'],
      clipped: true,
      drawer: true,
      fixed: false,
      homePage: true,
      attractionsPage: false,
      restaurantsPage: false,
      accomodationPage: false,
      travelPage: false,
      miniVariant: true,
      right: true,
      rightDrawer: false,
      title: 'CruiseAide',
      addAttractionDialog: false,
      addRestaurantDialog: false,
      addAccomodationDialog: false,
      addTravelDialog: false,
      loginDialog: false,
      signupDialog: false,
      showFilters: false,
      filteredTravels: [],
      filteredAccomodations: [],
      filteredRestaurants: [],
      filteredAttractions: [],
      search: ''
    };
  },
  methods: {
    add: function () {
      this.addDialog = true;
    },
    login: function () {
      this.loginDialog = true;
    },
    signup: function () {
      this.signupDialog = true;
    },
    addAttraction: function () {
      this.addAttractionDialog = true;
    },
    addRestaurant: function () {
      this.addRestaurantDialog = true;
    },
    addAccomodation: function () {
      this.addAccomodationDialog = true;
    },
    addTravel: function () {
      this.addTravelDialog = true;
    },
    disable: function () {
      this.items[0].disabled = false;
      this.items[1].disabled = false;
      this.items[2].disabled = false;
      this.items[3].disabled = false;
      this.items[4].disabled = false;
    },
    homeClicked: function () {
      this.disable();
      this.items[0].disabled = true;
      this.homePage = true;
      this.attractionsPage = false;
      this.restaurantsPage = false;
      this.accomodationPage = false;
      this.travelPage = false;
    },
    attractionsClicked: function () {
      this.disable();
      this.items[1].disabled = true;
      this.homePage = false;
      this.attractionsPage = true;
      this.restaurantsPage = false;
      this.accomodationPage = false;
      this.travelPage = false;
      this.filteredAttractions = this.attractions;
    },
    restaurantsClicked: function () {
      this.disable();
      this.items[2].disabled = true;
      this.homePage = false;
      this.attractionsPage = false;
      this.restaurantsPage = true;
      this.accomodationPage = false;
      this.travelPage = false;
      this.filteredRestaurants = this.restaurants;
    },
    accomodationClicked: function () {
      this.disable();
      this.items[3].disabled = true;
      this.homePage = false;
      this.attractionsPage = false;
      this.restaurantsPage = false;
      this.accomodationPage = true;
      this.travelPage = false;
      this.filteredAccomodations = this.accomodations;
    },
    travelClicked: function () {
      this.disable();
      this.items[4].disabled = true;
      this.homePage = false;
      this.attractionsPage = false;
      this.restaurantsPage = false;
      this.accomodationPage = false;
      this.travelPage = true;
      this.filteredTravels = this.travels;
    },
    filterResults: function () {
      if (this.attractionsPage) {
        this.filteredAttractions = this.attractions.filter(post => {
          if (post.title.toLowerCase().includes(this.search.toLowerCase())) {
            return true;
          }

          if (post.city.toLowerCase().includes(this.search.toLowerCase())) {
            return true;
          }

          if (post.country.toLowerCase().includes(this.search.toLowerCase())) {
            return true;
          }

          return false;
        });
      }

      if (this.restaurantsPage) {
        this.filteredRestaurants = this.restaurants.filter(post => {
          if (this.restaurantFilters.cuisines.includes(post.cuisine) || this.restaurantFilters.cuisines.length === 0) {
            if (this.restaurantFilters.features.some(r => post.features.includes(r)) || this.restaurantFilters.features.length === 0) {
              if (post.title.toLowerCase().includes(this.search.toLowerCase())) {
                return true;
              }

              if (post.city.toLowerCase().includes(this.search.toLowerCase())) {
                return true;
              }

              if (post.country.toLowerCase().includes(this.search.toLowerCase())) {
                return true;
              }
            }
          }

          return false;
        });
      }

      if (this.accomodationPage) {
        this.filteredAccomodations = this.accomodations.filter(post => {
          if (this.accomodationFilters.price > post.price) {
            if (this.accomodationFilters.types.includes(post.type) || this.accomodationFilters.types.length === 0) {
              if (this.accomodationFilters.features.some(r => post.features.includes(r)) || this.accomodationFilters.features.length === 0) {
                if (post.title.toLowerCase().includes(this.search.toLowerCase())) {
                  return true;
                }

                if (post.city.toLowerCase().includes(this.search.toLowerCase())) {
                  return true;
                }

                if (post.country.toLowerCase().includes(this.search.toLowerCase())) {
                  return true;
                }
              }
            }
          }

          return false;
        });
      }

      if (this.travelPage) {
        this.filteredTravels = this.travels.filter(post => {
          if (this.travelFilters.price > post.price) {
            if (this.travelFilters.classes.includes(post.class) || this.travelFilters.classes.length === 0) {
              if (this.travelFilters.airlines.includes(post.title) || this.travelFilters.airlines.length === 0) {
                if (post.srcCity.toLowerCase().includes(this.search.toLowerCase())) {
                  return true;
                }

                if (post.srcCountry.toLowerCase().includes(this.search.toLowerCase())) {
                  return true;
                }

                if (post.destCity.toLowerCase().includes(this.search.toLowerCase())) {
                  return true;
                }

                if (post.destCountry.toLowerCase().includes(this.search.toLowerCase())) {
                  return true;
                }
              }
            }
          }

          return false;
        });
      }
    }
  },
  name: 'App'
};
</script>