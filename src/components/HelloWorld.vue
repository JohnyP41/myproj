<script setup>


  fetch("https://demo.crehler.dev/store-api/product-listing/e435c9763b0d44fcab67ea1c0fdb3fa0", {
    method: 'POST',
    headers: {
        'sw-access-key':'SWSCMDV3N2DIOUNZTKNNCTBBCW',
        'Accept': 'application/json',
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({ 
      order: "price-asc"
    })
}).then(response => response.json()).then(response =>{{

  let text = "<div><ul>";
  response["elements"].forEach(myFunction);
  text += "</div></ul>";
  document.getElementById("name").innerHTML = text;
  function myFunction(value) {
      text += "<li>"+"<div id=\"nam\">"+value["translated"]["name"]+"</div>"+"<div id=\"desc\">"+value["translated"]["description"]+"</div>"+"<div id=\"price\">"+"Cena "+value["calculatedPrice"]["totalPrice"]+"</div>"+ "</li>";
} 
}})

function clek()
{
  var message=document.getElementById("site-search");
  message=message.value;
  if(message==""){
    var list=document.getElementById("list");
  list=list.value

  fetch("https://demo.crehler.dev/store-api/product-listing/e435c9763b0d44fcab67ea1c0fdb3fa0", {
    method: 'POST',
    headers: {
        'sw-access-key':'SWSCMDV3N2DIOUNZTKNNCTBBCW',
        'Accept': 'application/json',
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({ 
      order: String(list)
    })
}).then(response => response.json()).then(response =>{{

  let text = "<div><ul>";
  response["elements"].forEach(myFunction);
  text += "</div></ul>";
  document.getElementById("name").innerHTML = text;
  function myFunction(value) {
      text += "<li>"+"<div id=\"nam\">"+value["translated"]["name"]+"</div>"+"<div id=\"desc\">"+value["translated"]["description"]+"</div>"+"<div id=\"price\">"+"Cena "+value["calculatedPrice"]["totalPrice"]+"</div>"+ "</li>";
} 
}})
  }
  else{
  var list=document.getElementById("list");
  list=list.value
  var message=document.getElementById("site-search");
  message=message.value;
  fetch("https://demo.crehler.dev/store-api/search", {
  method: "POST",
  body: JSON.stringify({
    search: String(message),
    order: String(list)
  }),
  headers: {
    "Content-type": "application/json",
    'sw-access-key':'SWSCMDV3N2DIOUNZTKNNCTBBCW'
  }
}).then((response) => response.json()).then((json) => {{
  console.log(message)
  let text = "<div><ul>";
  json["elements"].forEach(myFunction);
  text += "</div></ul>";
  document.getElementById("name").innerHTML = text;
  function myFunction(value) {
      text += "<li>"+"<div id=\"nam\">"+value["translated"]["name"]+"</div>"+"<div id=\"desc\">"+value["translated"]["description"]+"</div>"+"<div id=\"price\">"+"Cena "+value["calculatedPrice"]["totalPrice"]+"</div>"+ "</li>";
  }

}});
  }


}

function click(){
  var list=document.getElementById("list");
  list=list.value
  var message=document.getElementById("site-search");
  message=message.value
  fetch("https://demo.crehler.dev/store-api/search", {
  method: "POST",
  body: JSON.stringify({
    search: String(message),
    order: String(list)
  }),
  headers: {
    "Content-type": "application/json",
    'sw-access-key':'SWSCMDV3N2DIOUNZTKNNCTBBCW'
  }
}).then((response) => response.json()).then((json) => {{
  
  let text = "<div><ul>";
  json["elements"].forEach(myFunction);
  text += "</div></ul>";
  document.getElementById("name").innerHTML = text;
  function myFunction(value) {
      text += "<li>"+"<div id=\"nam\">"+value["translated"]["name"]+"</div>"+"<div id=\"desc\">"+value["translated"]["description"]+"</div>"+"<div id=\"price\">"+"Cena "+value["calculatedPrice"]["totalPrice"]+"</div>"+ "</li>";
  }

}});

}






</script>

<template>
  <div class="greetings">
    <h1 class="green"><a href="">Shopware listing</a>
    <select @input="clek()" id="list">
   <option value="price-asc"  selected="true">Najtańsze</option>
   <option value="price-desc" >Najdroższe</option>
   </select>
    </h1>
    <h3>
      <div class="dropdown">
      <input type="text"  @change="click()" id="site-search" name="q" placeholder="Szukaj...">
    </div>
    </h3>
    <div id="name"></div>
  </div>
</template>

<style scoped>

h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
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
