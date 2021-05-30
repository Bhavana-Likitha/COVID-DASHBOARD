<script>
	let country = "";
	let count = new Array();
	let i, k;
	let j;
	let head;
	var names = new Array();
	var confirmed = new Array();
	var deaths = new Array();
	var active = new Array();
	var recovered = new Array();
   
	async function getData() {
	  const d = await fetch(
		`https://covid19.mathdro.id/api/countries/${country}/confirmed`
	  );
	  const data = await d.json();
	  const countr = await fetch("https://covid19.mathdro.id/api/countries/");
	  const countries = await countr.json();
	  for (j = 0; j < 192; j++) {
		count[j] = countries.countries[j].name;
	  }
	  for (k = 0; k < 192; k++) {
		var param = count[k].includes(country);
		if (param == true) {
		  break;
		}
	  }
	  if (param == true) {
		for (i = 0; i < 10; i++) {
		  names[i] = data[i].provinceState;
		  confirmed[i] = data[i].confirmed;
		  recovered[i] = data[i].recovered;
		  deaths[i] = data[i].deaths;
		  active[i] = data[i].active;
		}
		head = true;
	  } else if (param == false) {
		alert("Enter a Valid country with first letter capital");
	  }
	}
   </script>
   <div class="container">
   <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.5.0/css/all.css" integrity="sha384-B4dIYHKNBt8Bc12p+WXckhzcICo0wtJAoU8YZTY5qE0Id1GSseTk6S+L3BlXeVIU" crossorigin="anonymous">
   <meta name="viewport" content="width=device-width,initial-scale=1">
   <link rel="preconnect" href="https://fonts.gstatic.com">
   <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.5.0/css/all.css" integrity="sha384-B4dIYHKNBt8Bc12p+WXckhzcICo0wtJAoU8YZTY5qE0Id1GSseTk6S+L3BlXeVIU" crossorigin="anonymous">
   <link rel="preconnect" href="https://fonts.gstatic.com">
   <link href="https://fonts.googleapis.com/css2?family=Domine&family=Open+Sans&display=swap" rel="stylesheet">
   <div class="nav">
	 <input type="checkbox" id="nav-check">
	 <div class="nav-header">
	   <div class="nav-title">
		<strong style="color:rgb(192, 14, 103);">COVID</strong> DATAHUB
	   </div>
	 </div>
	 <div class="nav-btn">
	   <label for="nav-check">
		 <span></span>
		 <span></span>
		 <span></span>
	   </label>
	 </div>
	 
	 <div class="nav-links">
	   <a href="https://www.mohfw.gov.in/covid_vaccination/vaccination/index.html">Vaccine</a>
	   <a href="https://ourworldindata.org/grapher/current-covid-patients-hospital">Hospitals</a>
	   <a href="https://ourworldindata.org/coronavirus-testing">Tests</a>
	   <a href="https://www.cdc.gov/coronavirus/2019-ncov/symptoms-testing/symptoms.html">Symptoms</a>
	   <button class="sp">SIGNUP</button>
	 </div>
   </div>
   <div class="imte">
   <div class="text">
   <h3>While many are experiencing it first-hand in our world. We are currently experiencing a second wave of Covid-19 leading to a large number of people requiring urgent medical care and aid. 
   <br>
   <div class="short-text">
   In this you will be knowing more about the latest pandemic. This website is for interactive info that where the virus has spread,
   as well as numbers on latest in infection rates,deaths,breakdowns of what countries are suffering from new cases.
   </div>
   </h3>
   </div>
   <img style="width:100%;" src="../covid1.png" alt=" "/>
   </div>
   <div class="ini">
   <div class="search">
	<i class="fa fa-search " ></i>
   <input bind:value={country} placeholder="Enter a country">
   </div>
   <button on:click={getData}>Result</button>
	</div>
	<div>
   <h2 style="text-align:center"> {country}</h2>
   </div>
   {#if head==true}
   <div class="heading">
   <h2>State name</h2>
   <h2 style="padding-left:30px;">Confirmed</h2>
   <h2> Recovered </h2>
   <h2 style="padding-right:28px;"> Deaths </h2>
   <h2 style="margin-right:1%;">Active</h2>
   </div>
   {/if}
   {#if head==false}
   <p>enter a country</p>
   {/if}
   {#each {length: names.length} as names_, i}
   <div class="hello">
   <div class="cnames" >
   <p>{names[i]}</p>
   <hr>
   </div>
   <div class="packthree">
   <div class="confirmed" >
   <h5>Confirmed  :  </h5>
	<p>{confirmed[i]}</p>
   </div>
   <div class="confirmed" >
   <h5>Recovered  :  </h5>
	  <p>{ recovered[i]}</p>
	  
   </div>
	 <div class="confirmed">
   <h5> Deaths  : </h5>
	   <p >{ deaths[i]}</p>
	   
	   </div>
	   <div class="confirmed">
   <h5> Active  :  </h5>
		<p >{ active[i]}</p>
		</div>
		</div>
   </div>
   {/each}
   </div>
   <style>
	 .nav {
	   height: 50px;
	   width: 100%;
	   position: relative;
	 }
	 h6 {
	   font-family: "Domine", serif;
	   font-family: "Open Sans", sans-serif;
	   background-color: #fc5296;
	   background-image: linear-gradient(120deg, #eb4688 0%, #a374b3 74%);
	   -webkit-text-fill-color: transparent;
	   -webkit-background-clip: text;
	   font-weight: bold;
	   word-spacing: 2px;
	   letter-spacing: 2px;
	 }
	 h5 {
	   display: none;
	 }
	 hr {
	   display: none;
	 }
	 .nav > .nav-header {
	   display: inline;
	 }
   
	 .nav > .nav-header > .nav-title {
	   display: inline-block;
	   font-size: 30px;
	   color: #fff;
	   padding: 10px 10px 10px 10px;
	   font-family: "Domine", serif;
	   font-family: "Open Sans", sans-serif;
	 }
   
	 .nav > .nav-btn {
	   display: none;
	 }
   
	 .nav > .nav-links {
	   display: inline;
	   margin-left: 45%;
	   font-size: 18px;
	 }
   
	 .nav > .nav-links > a {
	   display: inline-block;
	   padding: 13px 10px 13px 10px;
	   text-decoration: none;
	   color: #efefef;
	 }
   
	 .nav > .nav-links > a:hover {
	   background-color: rgb(192, 14, 103);
	 }
   
	 .nav > #nav-check {
	   display: none;
	 }
   
	 .heading {
	   display: flex;
	   justify-content: space-between;
	   margin-right: 2%;
	   margin-left: 2%;
	 }
	 .heading h2 {
	   color: rgb(192, 14, 103);
	 }
	 .packthree {
	   display: flex;
	   justify-content: space-between;
	   width: 73%;
	   font-size: 20px;
	 }
	 .hello {
	   display: flex;
	   justify-content: space-between;
	   background-color: #fc5296;
	   background-image: linear-gradient(120deg, #eb4688 0%, #a374b3 74%);
	   border-radius: 15px;
	   padding: 30px;
	   margin: 2px 10px 20px 0px;
	   font-size: 20px;
	 }
	 .container {
	   overflow-x: hidden;
	 }
	 button {
	   width: 200px;
	   height: 50px;
	   border: none;
	   border-radius: 25px;
	   outline: none;
	   margin-left: 10px;
	   font-family: "Domine", serif;
	   font-family: "Open Sans", sans-serif;
	   transition: all 0.3s ease 0s;
	   cursor: pointer;
	   background-image: linear-gradient(315deg, #7e0f2e 0%, #5d30b1 74%);
	   color: #fff;
	   font-size: 20px;
	 }
	 button:hover {
	   background-image: linear-gradient(315deg, #7e0f2e 0%, #5d30b1 74%);
	   color: #fff;
	   transform: translateY(-7px);
	 }
	 .sp {
	   width: 150px;
	   height: 40px;
	   border: none;
	   border-radius: 25px;
	   outline: none;
	   margin-left: 10px;
	   font-family: "Domine", serif;
	   font-family: "Open Sans", sans-serif;
	   transition: all 0.3s ease 0s;
	   cursor: pointer;
	   background-image: linear-gradient(315deg, #7e0f2e 0%, #5d30b1 74%);
	   color: #fff;
	   font-size: 17px;
	   font-weight: 10px;
	 }
	 .search {
	   width: 320px;
	   height: 5px;
	   background-color: #fff;
	   border-radius: 30px;
	   padding: 20px;
	   display: flex;
	   align-items: center;
	   padding-left: 10px;
	 }
	 .search > i {
	   font-size: 18px;
	   color: black;
	   padding-left: 20px;
	   margin-top: 8px;
	   margin-bottom: 9px;
	 }
	 .search > input {
	   background-color: #fff;
	   flex: 1px;
	   height: 20px;
	   outline: none;
	   border: none;
	   padding-left: 10px;
	   font-size: 18px;
	   font-family: "Domine", serif;
	   font-family: "Open Sans", sans-serif;
	 }
	 a,
	 p,
	 h3,
	 h2 {
	   color: white;
	   font-family: "Domine", serif;
	   font-family: "Open Sans", sans-serif;
	 }
	 h3 {
	   font-size: 25px;
	   font-family: "Domine", serif;
	   font-family: "Open Sans", sans-serif;
	   background-color: #fc5296;
	   background-image: linear-gradient(120deg, #eb4688 0%, #a374b3 74%);
	   -webkit-text-fill-color: transparent;
	   -webkit-background-clip: text;
	   font-weight: bold;
	   word-spacing: 2px;
	   letter-spacing: 2px;
	   margin-top: 6%;
	 }
	 .imte {
	   display: flex;
	   align-items: center;
	   justify-content: space-around;
	 }
	 .ini {
	   display: flex;
	   align-items: center;
	   margin-left: 10%;
	 }
	 h2 {
	   text-align: center;
	 }
	 @media (max-width: 600px) {
	   .nav > .nav-btn {
		 display: inline-block;
		 position: absolute;
		 right: 0px;
		 top: 0px;
	   }
	   .nav > .nav-btn > label {
		 display: inline-block;
		 width: 50px;
		 height: 50px;
		 padding: 13px;
	   }
	   .nav > .nav-btn > label:hover,
	   .nav #nav-check:checked ~ .nav-btn > label {
		 background-color: rgba(0, 0, 0, 0.3);
	   }
	   .nav > .nav-btn > label > span {
		 display: block;
		 width: 25px;
		 height: 10px;
		 border-top: 2px solid #eee;
	   }
	   .nav > .nav-links {
		 position: absolute;
		 display: block;
		 width: 100%;
		 background-color: #333;
		 height: 0px;
		 transition: all 0.3s ease-in;
		 overflow-y: hidden;
		 top: 50px;
		 left: 0px;
	   }
	   .nav > .nav-links > a {
		 display: block;
		 width: 100%;
	   }
	   .nav > #nav-check:not(:checked) ~ .nav-links {
		 height: 0px;
	   }
	   .nav > #nav-check:checked ~ .nav-links {
		 height: calc(65vh - 50px);
		 overflow-y: auto;
	   }
	 }
	 @media (max-width: 500px) {
	   .imte {
		 display: flex;
		 flex-direction: column;
		 align-items: center;
	   }
	   img {
		 width: 100%;
	   }
	   .ini {
		 display: flex;
		 flex-direction: column;
		 align-items: center;
		 justify-content: center;
	   }
	   button {
		 width: 150px;
		 height: 40px;
		 border: none;
		 margin-top: 10px;
		 margin-right: 12%;
	   }
	   h3 {
		 font-size: 20px;
	   }
	   .search {
		 margin-top: 20%;
		 width: 200px;
		 height: 5px;
		 background-color: #fff;
		 border-radius: 30px;
		 padding-left: 10px;
		 display: flex;
		 align-items: center;
		 margin-right: 10%;
	   }
	   .search > i {
		 font-size: 15px;
		 color: black;
	   }
	   .search > input {
		 background-color: #fff;
		 flex: 1px;
		 height: 20px;
		 width: 10px;
		 outline: none;
		 border: none;
		 padding-left: 10px;
		 font-size: 18px;
	   }
	   .short-text {
		 display: none;
	   }
	   .hello {
		 display: flex;
		 flex-direction: column;
		 align-items: center;
	   }
	   .packthree {
		 display: flex;
		 flex-direction: column;
		 align-items: center;
		 font-size: 15px;
	   }
	   h5 {
		 display: flex;
		 font-family: "Domine", serif;
		 font-family: "Open Sans", sans-serif;
		 font-size: 20px;
	   }
	   .heading {
		 display: none;
	   }
	   .confirmed {
		 display: flex;
		 align-items: center;
	   }
	   .cnames {
		 font-family: "Domine", serif;
		 font-family: "Open Sans", sans-serif;
		 font-size: 25px;
		 align-items: center;
	   }
	   hr {
		 display: center;
	   }
	   .nav > .nav-header > .nav-title {
		 font-size: 23px;
	   }
	 }
   </style>
