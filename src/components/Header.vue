<template>
  <nav class="nav has-shadow">
    <div class="container">
      <div class="nav-left">
        <router-link class="nav-item nav-logo" to="/">Stock Trader</router-link>
        <router-link class="nav-item is-tab" activeClass="is-active" to="/portfolio">Portfolio</router-link>
        <router-link class="nav-item is-tab" activeClass="is-active" to="/stocks">Stocks</router-link>
      </div>
      <div class="nav-right nav-menu">
        <a href="#" class="nav-item is-tab">End Day</a>
        <div class="has-dropdown">
          <a href="#" class="button">
            <span>Save & Load</span>
            <span class="icon is-small">
              <i class="fa fa-angle-down"></i>
            </span>
          </a>
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
    </div>
  </nav>
</template>

<style>

  .nav-logo {
    font-size: 24px;
    font-weight: bold;
  }

  .has-dropdown {
    position: relative;
    align-items: center;
    display: flex;
    flex-grow: 0;
    flex-shrink: 0;
    font-size: 1rem;
    justify-content: center;
    padding: .5rem .75rem
  }

  .dropdown {
    display: none;
  }

</style>