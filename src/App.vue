<template>
  <div id="app">
    <Header />

    <GridList />
  </div>
</template>

<script>
import Header from './components/Header'
import GridList from './components/GridList'

export default {
  name: 'App',
  components: {
    Header,
    GridList
  }
}
</script>

<style>
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta2/css/all.min.css');

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  background-color: #f5f6f7;
  display: flex;
  justify-content: center;
  padding: 20px 0;

  font-family: Helvetica, Arial, sans-serif;
}

/* grid */
.grid {
  width: 100%;
  max-width: 1280px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  margin: 0 auto;
  padding: 0;
  list-style-type: none;
}

.grid__item {
  margin: 0 10px 20px;

  flex: 1 1 290px;
}
.modal {
  position: relative;
  padding: 20px;
}
.vm--overlay {
  background: rgba(0, 0, 0, 0.5) !important;
}

/* card */
.card {
  background-color: #fff;
  overflow: hidden;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.2);
  border-radius: 2px;
  line-height: 0;
  cursor: pointer;
}

.card:hover {
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.2);
}
.card__header {
  display: grid;
  grid-template: 'min-content' /95% 5%;
}
.close {
  right: 1%;
  top: 5%;
  position: absolute;
  margin: auto;
}
.card__body {
  width: 100%;
  height: 215px;
  overflow: hidden;
  background-color: #eee;
}

.card__body img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.card__footer {
  width: 100%;
  padding: 10px 15px;
}

.card__likes {
  float: right;
  color: #ea4c89;
  font-size: 19px;
}

.card__date {
  margin-right: 20px;
  font-family: Courier, serif;
  font-size: 13px;
  color: #999;
}

.media__obj {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background-color: #d8d8d8;
  margin-right: 15px;
  float: left;
}

.media__body {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  width: 100%;
  min-height: 32px;
  line-height: 32px;
}

.media__body a {
  font-family: Courier, serif;
  font-size: 15px;
  color: #999;
}

.media__body a:hover {
  text-decoration: none;
}

/* pagination */
.pagination {
  margin: 0 auto;
  max-width: 1280px;
  width: 100%;
  padding: 0 4px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.pagination__left,
.pagination__right,
.pagination__mid {
  padding: 30px 0;
}

.pagination a,
.pagination span {
  display: block;
  text-align: center;
  font-family: Helvetica, Arial, sans-serif;
  font-weight: 300;
  line-height: 42px;
  height: 44px;
  color: #999;
  font-size: 18px;
}

.pagination a {
  padding: 0 16px;
  max-width: 160px;
  background-color: transparent;
  border-radius: 4px;
  border: 1px solid #ccc;
  text-decoration: none;
  margin: 0 6px;
  transition: all 0.2s ease-in-out;
}

.pagination a:hover,
.pagination a.current {
  border-color: #ea4c89;
  color: #ea4c89;
}

.pagination__mid {
  margin: 0 auto;
  display: flex;
  justify-content: center;
}

.pagination__mid ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.pagination__mid li {
  display: inline-block;
}

.hidden {
  display: none !important;
}

.loader {
  position: fixed;
  z-index: 9;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  /*   position: relative; */
}

.loader::before,
.loader::after {
  content: '';
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
}

.loader::before {
  background: hsla(0, 0%, 100%, 0.7);
}

.loader::after {
  content: '';
  font-size: 48px;
  width: 1em;
  height: 1em;
  border: 2px solid #ccc;
  border-top-color: #ea4c89;
  border-radius: 50%;
  animation: spinner 1s linear infinite;
}

@keyframes spinner {
  to {
    transform: rotate(1turn);
  }
}

.text-center {
  text-align: center;
}

.filters {
  margin-bottom: 20px;
  text-align: center;
}
.filters label {
  margin-right: 15px;
}
select {
  /* display: block; */
  font-size: 16px;
  font-family: sans-serif;
  font-weight: 700;
  color: #444;
  line-height: 1.3;
  padding: 0.6em 1.4em 0.5em 0.8em;
  width: 120px;
  max-width: 100%;
  box-sizing: border-box;
  margin: 0;
  border: 1px solid #aaa;
  box-shadow: 0 1px 0 1px rgba(0, 0, 0, 0.04);
  border-radius: 0.5em;
  -moz-appearance: none;
  -webkit-appearance: none;
  appearance: none;
  background-color: #fff;
  background-image: url('data:image/svg+xml;charset=US-ASCII,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%22292.4%22%20height%3D%22292.4%22%3E%3Cpath%20fill%3D%22%23EA4C89%22%20d%3D%22M287%2069.4a17.6%2017.6%200%200%200-13-5.4H18.4c-5%200-9.3%201.8-12.9%205.4A17.6%2017.6%200%200%200%200%2082.2c0%205%201.8%209.3%205.4%2012.9l128%20127.9c3.6%203.6%207.8%205.4%2012.8%205.4s9.2-1.8%2012.8-5.4L287%2095c3.5-3.5%205.4-7.8%205.4-12.8%200-5-1.9-9.2-5.5-12.8z%22%2F%3E%3C%2Fsvg%3E'),
    linear-gradient(to bottom, #ffffff 0%, #e5e5e5 100%);
  background-repeat: no-repeat, repeat;
  background-position: right 0.7em top 50%, 0 0;
  background-size: 0.65em auto, 100%;
}

select::-ms-expand {
  display: none;
}
select:hover {
  border-color: #888;
}
select:focus {
  border-color: #aaa;
  box-shadow: 0 0 1px 3px #ea4c89;
  box-shadow: 0 0 0 3px -moz-mac-focusring;
  color: #222;
  outline: none;
}
select option {
  font-weight: normal;
}

p {
  margin: 0;
}
</style>
