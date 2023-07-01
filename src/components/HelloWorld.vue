<script setup>
fetch('https://demo.crehler.dev/store-api/product-listing/e435c9763b0d44fcab67ea1c0fdb3fa0', {
  method: 'POST',
  headers: {
    'sw-access-key': 'SWSCMDV3N2DIOUNZTKNNCTBBCW',
    Accept: 'application/json',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    order: 'price-asc'
  })
})
  .then((response) => response.json())
  .then((response) => {
    {
      let text = '<ul class="list-group">'
      response['elements'].forEach(myFunction)
      text += '</ul class="list-group">'
      document.getElementById('name').innerHTML = text
      function myFunction(value) {
        text +=
          '<li class="list-group-item">' +
          '<div id="nam"><b>' +
          value['translated']['name'] +
          '</b></div>' +
          '<div id="desc">' +
          value['translated']['description'] +
          '</div>' +
          '<div id="price">' +
          '<b>Cena</b> ' +
          value['calculatedPrice']['totalPrice'] +
          '</div>' +
          '</li>'
      }
    }
  })

function clek() {
  var message = document.getElementById('site-search')
  message = message.value
  if (message == '') {
    var list = document.getElementById('list')
    list = list.value

    fetch('https://demo.crehler.dev/store-api/product-listing/e435c9763b0d44fcab67ea1c0fdb3fa0', {
      method: 'POST',
      headers: {
        'sw-access-key': 'SWSCMDV3N2DIOUNZTKNNCTBBCW',
        Accept: 'application/json',
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        order: String(list)
      })
    })
      .then((response) => response.json())
      .then((response) => {
        {
          let text = '<ul class="list-group">'
          response['elements'].forEach(myFunction)
          text += '</ul class="list-group">'
          document.getElementById('name').innerHTML = text
          function myFunction(value) {
            text +=
          '<li class="list-group-item">' +
          '<div id="nam"><b>' +
          value['translated']['name'] +
          '</b></div>' +
          '<div id="desc">' +
          value['translated']['description'] +
          '</div>' +
          '<div id="price">' +
          '<b>Cena</b> ' +
          value['calculatedPrice']['totalPrice'] +
          '</div>' +
          '</li>'
          }
        }
      })
  } else {
    var list = document.getElementById('list')
    list = list.value
    var message = document.getElementById('site-search')
    message = message.value
    fetch('https://demo.crehler.dev/store-api/search', {
      method: 'POST',
      body: JSON.stringify({
        search: String(message),
        order: String(list)
      }),
      headers: {
        'Content-type': 'application/json',
        'sw-access-key': 'SWSCMDV3N2DIOUNZTKNNCTBBCW'
      }
    })
      .then((response) => response.json())
      .then((json) => {
        {
          let text = '<ul class="list-group">'
          json['elements'].forEach(myFunction)
          text += '</ul class="list-group">'
          document.getElementById('name').innerHTML = text
          function myFunction(value) {
            text +=
          '<li class="list-group-item">' +
          '<div id="nam"><b>' +
          value['translated']['name'] +
          '</b></div>' +
          '<div id="desc">' +
          value['translated']['description'] +
          '</div>' +
          '<div id="price">' +
          '<b>Cena</b> ' +
          value['calculatedPrice']['totalPrice'] +
          '</div>' +
          '</li>'
          }
        }
      })
  }
}

function click() {
  var message = document.getElementById('site-search')
  message = message.value
  if (message == '') {
    var list = document.getElementById('list')
    list = list.value

    fetch('https://demo.crehler.dev/store-api/product-listing/e435c9763b0d44fcab67ea1c0fdb3fa0', {
      method: 'POST',
      headers: {
        'sw-access-key': 'SWSCMDV3N2DIOUNZTKNNCTBBCW',
        Accept: 'application/json',
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        order: String(list)
      })
    })
      .then((response) => response.json())
      .then((response) => {
        {
          let text = '<ul class="list-group">'
          response['elements'].forEach(myFunction)
          text += '</ul class="list-group">'
          document.getElementById('name').innerHTML = text
          function myFunction(value) {
            text +=
          '<li class="list-group-item">' +
          '<div id="nam"><b>' +
          value['translated']['name'] +
          '</b></div>' +
          '<div id="desc">' +
          value['translated']['description'] +
          '</div>' +
          '<div id="price">' +
          '<b>Cena</b> ' +
          value['calculatedPrice']['totalPrice'] +
          '</div>' +
          '</li>'
          }
        }
      })
  }else{
  var list = document.getElementById('list')
  list = list.value
  var message = document.getElementById('site-search')
  message = message.value
  fetch('https://demo.crehler.dev/store-api/search', {
    method: 'POST',
    body: JSON.stringify({
      search: String(message),
      order: String(list)
    }),
    headers: {
      'Content-type': 'application/json',
      'sw-access-key': 'SWSCMDV3N2DIOUNZTKNNCTBBCW'
    }
  })
    .then((response) => response.json())
    .then((json) => {
      {
        let text = '<div><ul class="list-group">'
        json['elements'].forEach(myFunction)
        text += '</div></ul class="list-group">'
        document.getElementById('name').innerHTML = text
        function myFunction(value) {
          text +=
          '<li class="list-group-item">' +
          '<div id="nam"><b>' +
          value['translated']['name'] +
          '</b></div>' +
          '<div id="desc">' +
          value['translated']['description'] +
          '</div>' +
          '<div id="price">' +
          '<b>Cena</b> ' +
          value['calculatedPrice']['totalPrice'] +
          '</div>' +
          '</li>'
        }
      }
    })
}
}

</script>

<template>
    <nav class="navbar navbar-light text-white bg-dark">
      <div class="container-fluid">
        <a class="navbar-brand text-white bg-dark">
          <h1><b>Shopware listing</b></h1>
        </a>
      <div id="lol">
          <select class="form-select text-white bg-dark" @input="clek()" id="list">
            <option value="price-asc" selected="true">Najtańsze</option>
            <option value="price-desc">Najdroższe</option>
          </select>
        </div>
      </div>
    </nav>
    <br />
    <br />
    <br />
      <div class="dropdown">
        <input
          class="form-select form-select-lg mb-3"
          aria-label=".form-select-lg example"
          type="text"
          @change="click()"
          id="site-search"
          name="qbe"
          placeholder="Szukaj..."
        />
      </div>
      <br />
    <br />
    <div id="name"></div>
</template>

<style scoped>

#menu {
	background: #F7F7F9;
	border-radius: 0;
	display: inline-block;
	width:100%;
	margin:0px;
}
.menu-left ul {
	margin: 0;
	padding:0;
	font-size: 17px; 
    width: 100%;
}
.menu-left ul li {
	display:inline-block;
	vertical-align: top;
	width: 30%;
  text-align:center;
}

#list{
    float:right;
}
h1 {
  font-weight: 100;
  font-size: 1.5rem;
  position: relative;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
