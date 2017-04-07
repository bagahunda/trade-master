<template>
  <nav class="nav has-shadow">
    <div class="nav-left">
      <router-link class="nav-item" to="/">Stock Trader</router-link>
      <router-link class="nav-item is-tab" activeClass="is-active" to="/portfolio">Portfolio</router-link>
      <router-link class="nav-item is-tab" activeClass="is-active" to="/stocks">Stocks</router-link>
    </div>
    <div class="nav-right nav-menu">
      <a href="#" class="nav-item is-tab">End Day</a>
      <div class="has-dropdown">
        <a href="#" class="button is-medium">Save & Load</a>
        <ul class="dropdown box">
          <li>
            <a href="#">Save Data</a>
          </li>
          <li>
            <a href="#">Load Data</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>