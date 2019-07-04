<template>
  <header class="header">
    <div class="header-left">
      <div class="logo">
        <p>
          Oceana Planet
        </p>
      </div>
    </div>
    <nav class="header-right">
      <ul class="navigation">
        <li>HOME</li>
        <li>ABOUT</li>
        <li>CONTACT</li>
      </ul>
    </nav>
  </header>
</template>

<style>
.header {
  width: 100%;
  padding: 0 50px;
  display: flex;
  justify-content: space-between;
}
.logo {
  background-color: #15468e;
  color: #ffffff;
  width: 226px;
  height: 93px;
  border-radius: 5px;
  margin-top: -10px;
}
.logo p {
  font-size: 24px;
  padding-top: 30px;
}
.header-right {
  width: 50%;
}
.navigation {
  display: flex;
  flex-direction: row;
  width: 100%;
  justify-content: space-evenly;
}
.navigation li {
  padding-top: 20px;
  list-style-type: none;
  color: #ffffff;
  font-size: 14px;
}
</style>
