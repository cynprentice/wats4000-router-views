<template>
<div id="survey">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/survey">Survey</router-link> |
    </div>
    <router-view/>

    <h1>Secret</h1>
    <figure>
        <img src="../assets/toiletPaper.jpg" alt="various strange rolls of toilet paper" width="400px">
        <figcaption>Regrettable online purchases during desperate times.</figcaption>
    </figure>

  </div>
</template>
