// Login page Js

var user = [{
"userId" : "123",
"userType" : "normal"
},
{
"userId" : "100",
"userType" : "special"
}];

// Login function
function login(){

sessionStorage.setItem('loginId', document.getElementById("userid").value);

if(document.getElementById("userid").value  == "" && document.getElementById("password").value  == ""){
alert("Please enter user id and password");
}
if(document.getElementById("userid").value  != 123 && document.getElementById("userid").value  != 100){
alert("Invalid user id");
}
if(document.getElementById("password").value != 1234){
alert("Invalid password");
}

if(document.getElementById("userid").value == 123 && document.getElementById("password").value == 1234){
window.location = "EventHomePage.html";
}

if(document.getElementById("userid").value == 100 && document.getElementById("password").value == 1234){
window.location = "EventHomePage.html";
}
}

// Event Home page

function logout(){
window.location = "Login.html";
}

/*---Object for events----*/
var events = {"eventsPresent" :[{

  "eventType":"Sports",
  "title": "IPL Nagpur",
  "startDate": "03/5/2020",
  "endDate" : "04/5/2020",
  "Location": "VCA stadium"
},
{

  "eventType":"Cultural",
  "title": "Dance Plus",
  "startDate": "13/12/2020",
  "endDate" : "30/12/2020",
  "Location": "VCA stadium"
},
{

  "eventType":"Celebration",
  "title": "Women's Day Celebration",
  "startDate": "03/2/2021",
  "endDate" : "03/2/2021",
  "Location": "Taj Hotel"
},
{

  "eventType":"Academic",
  "title": "Workshop",
  "startDate": "03/11/2020",
  "endDate" : "13/11/2020",
  "Location": "TR training classes"
},
{

  "eventType":"Sports",
  "title": "Batminton match",
  "startDate": "03/10/2020",
  "endDate" :"03/10/2020",
  "Location": "VCA stadium"
}]
};


/*--------event list iterate-------*/

//window.localStorage.setItem('eventsPresent', JSON.stringify(events));
//events = JSON.parse(window.localStorage.getItem('eventsPresent'));

var text = "", eLen, i,events;
eLen = events.eventsPresent.length;

document.addEventListener("DOMContentLoaded", function(event) { 

var loginId = sessionStorage.getItem("loginId");

if(loginId == 123){
document.getElementById("createbtn").style.visibility = "hidden";
document.getElementById("myEvents").style.visibility = "hidden";
}

text = "<div style='color:chocolate;'>";
for (i = 0; i < eLen; i++) {
  text += "<div style='width: 50%;margin-left: 24%;border: 1px solid darkorchid;border-radius: 10px;'>\
  <p style='font-weight: 600;'>" + events.eventsPresent[i].title + "</p>\
  <p><span> Start Date : " + events.eventsPresent[i].startDate  + "</span><span style='margin-left: 3%;'> End Date : " + events.eventsPresent[i].endDate  + "</span></p>\
  <p> Location : " + events.eventsPresent[i].Location + "</p></br>\
  <input type='button' value='Book Ticket' style='margin-bottom: 6%; border-radius: 5px; background: #1e88e5;' onclick='bookEvent()'></div></br>";
}
text += "</div>";
document.getElementById("demo").innerHTML = text;



});

// Events Filter function
function filterEvents(){
var selectedOpt = document.getElementById("eventSelect");
var selectedEvent = selectedOpt.options[selectedOpt.selectedIndex].text;
console.log(selectedEvent);

text = "<div style='color:chocolate;'>";
for (i = 0; i < eLen; i++) {
if(events.eventsPresent[i].eventType == selectedEvent ){
  text += "<div style='width: 50%;margin-left: 24%;border: 1px solid darkorchid;border-radius: 10px;'>\
  <p style='font-weight: 600;'>" + events.eventsPresent[i].title + "</p>\
  <p><span> Start Date : " + events.eventsPresent[i].startDate  + "</span><span style='margin-left: 3%;'> End Date : " + events.eventsPresent[i].endDate  + "</span></p>\
  <p> Location : " + events.eventsPresent[i].Location + "</p></br>\
  <input type='button' value='Book Ticket' style='margin-bottom: 6%; border-radius: 5px; background: #1e88e5;' onclick='bookEvent()'></div></br>";
}
if(selectedEvent == "All"){
text += "<div style='width: 50%;margin-left: 24%;border: 1px solid darkorchid;border-radius: 10px;'>\
  <p style='font-weight: 600;'>" + events.eventsPresent[i].title + "</p>\
  <p><span> Start Date : " + events.eventsPresent[i].startDate  + "</span><span style='margin-left: 3%;'> End Date : " + events.eventsPresent[i].endDate  + "</span></p>\
  <p> Location : " + events.eventsPresent[i].Location + "</p></br>\
  <input type='button' value='Book Ticket' style='margin-bottom: 6%; border-radius: 5px; background: #1e88e5;' onclick='bookEvent()'></div></br>";
}
}
text += "</div>";
document.getElementById("demo").innerHTML = text;
}


/*--------------show hide function-----*/
function myHome() {
 
  var home = document.getElementById("home");
  var contact = document.getElementById("contact");
  var create = document.getElementById("create");
    home.style.display = "block";
    contact.style.display = "none";
	create.style.display = "none";
	
	
  var selectedOpt = document.getElementById("eventSelect");
 selectedOpt.options[selectedOpt.selectedIndex].text = "All";
 
 text = "<div style='color:chocolate;'>";
for (i = 0; i < eLen; i++) {
  text += "<div style='width: 50%;margin-left: 24%;border: 1px solid darkorchid;border-radius: 10px;'>\
  <p style='font-weight: 600;'>" + events.eventsPresent[i].title + "</p>\
  <p><span> Start Date : " + events.eventsPresent[i].startDate  + "</span><span style='margin-left: 3%;'> End Date : " + events.eventsPresent[i].endDate  + "</span></p>\
  <p> Location : " + events.eventsPresent[i].Location + "</p></br>\
  <input type='button' value='Book Ticket' style='margin-bottom: 6%; border-radius: 5px; background: #1e88e5;' onclick='bookEvent()'></div></br>";
}
text += "</div>";
document.getElementById("demo").innerHTML = text;

  
}

function myEventList() {

 var home = document.getElementById("home");
  var contact = document.getElementById("contact");
  var create = document.getElementById("create");
    home.style.display = "none";
    contact.style.display = "block";
	create.style.display = "none";
	
	myEvents = JSON.parse(window.localStorage.getItem("myList"));
	
	var text = "", eLen, i,events;
eLen = myEvents.length;

text = "<div style='color:chocolate;'>";
for (i = 0; i < eLen; i++) {
  text += "<div style='width: 50%;margin-left: 24%;border: 1px solid darkorchid;border-radius: 10px;'>\
  <p style='font-weight: 600;'>" + myEvents[i].title + "</p>\
  <p><span> Start Date : " + myEvents[i].startDate  + "</span><span style='margin-left: 3%;'> End Date : " + myEvents[i].endDate  + "</span></p>\
  <p> Location : " + myEvents[i].Location + "</p></div></br>";
}
text += "</div>";
document.getElementById("myevent").innerHTML = text;
	

}

function eventCreate() {

 var home = document.getElementById("home");
  var contact = document.getElementById("contact");
  var create = document.getElementById("create");
    home.style.display = "none";
    contact.style.display = "none";
	create.style.display = "block";

}


// When the user clicks the button, open the modal 
function createNewEvent(eventTypeId) {
  document.getElementById("myModal").style.display = "block";
  document.forms["myForm"]["eventtitle"].value = "";
  document.forms["myForm"]["startdate"].value ="";
  document.forms["myForm"]["enddate"].value = "";
 document.forms["myForm"]["loc"].value = "";
  
  if(eventTypeId == 1){
  
  document.forms["myForm"]["eventtype"].value = "Sports"; 
  console.log("Sports");
  }
  else if(eventTypeId == 2){
  document.forms["myForm"]["eventtype"].value = "Academic"; 
  console.log("Academic");
  }
  else if(eventTypeId == 3){
  document.forms["myForm"]["eventtype"].value = "Celebration"; 
  console.log("Celebration");
  }
  else if(eventTypeId == 4){
  document.forms["myForm"]["eventtype"].value = "Cultural"; 
  console.log("Cultural");
  }
}

// When the user clicks on <span> (x), close the modal
function closeModal() {
  document.getElementById("myModal").style.display = "none";
} 

function closeBookModal() {
document.getElementById("bookModal").style.display = "none";
}

function bookEvent() {
  document.getElementById("bookModal").style.display = "block";
  }

// On Submission of Event Details
function submitEvent(form){

  if (form.eventtitle.value == "") {
    alert("Title must be filled out");
    return false;
  }
  
  if (form.loc.value == "") {
    alert("Location must be filled out");
    return false;
  }
  
  if (form.startdate.value == "") {
    alert("Start date must be filled out");
    return false;
  }
  
  if (form.enddate.value == "") {
    alert("End date must be filled out");
    return false;
  }

//start date validation
  // regular expression to match required date format
    re = /^(\d{1,2})\/(\d{1,2})\/(\d{4})$/;

    if(form.startdate.value != '') {
      if(regs = form.startdate.value.match(re)) {
	  
	  //for month feb
	  if(regs[2] == 2){
	  if(regs[3] % 4 === 0 ){
	  //day value between 1 to 29
	  if(regs[1] < 1 || regs[1] > 29) {
          alert("Invalid value for start date day: " + regs[1]);
          form.startdate.focus();
          return false;
        }
		} else {
		//day value between 1 to 28
		 if(regs[1] < 1 || regs[1] > 28) {
          alert("Invalid value for start date day: " + regs[1]);
          form.startdate.focus();
          return false;
        }
		}
	  
	  }
	  
	  if(regs[2] == 1 || regs[2] == 3 || regs[2] == 5 || regs[2] == 7 || regs[2] == 8 || regs[2] == 10 || regs[2] == 12){
	
        // day value between 1 and 31
        if(regs[1] < 1 || regs[1] > 31) {
          alert("Invalid value for start date day: " + regs[1]);
          form.startdate.focus();
          return false;
        }
		}
		
		 if(regs[2] == 4 || regs[2] == 6 || regs[2] == 9 || regs[2] == 11){
	
        // day value between 1 and 30
        if(regs[1] < 1 || regs[1] > 30) {
          alert("Invalid value for start date day: " + regs[1]);
          form.startdate.focus();
          return false;
        }
		}
		
        // month value between 1 and 12
        if(regs[2] < 1 || regs[2] > 12) {
          alert("Invalid value for start date month: " + regs[2]);
          form.startdate.focus();
          return false;
        }
        // year value between 2020 and 2025
        if(regs[3] < (new Date()).getFullYear() || regs[3] > 2025 ) {
          alert("Invalid value for start date year: " + regs[3] + " - must be between" + (new Date()).getFullYear() + " and 2025");
          form.startdate.focus();
          return false;
        }
      } else {
        alert("Invalid date format: " + form.startdate.value);
        form.startdate.focus();
        return false;
      }
    }

	
	
	
	//End date validation
		reg = /^(\d{1,2})\/(\d{1,2})\/(\d{4})$/;
	
	if((regs = form.enddate.value.match(reg)) && (start = form.startdate.value.match(re))){
	
	if(start[3] > regs[3]){
	alert("start date should be less than end date");
	form.enddate.focus();
          return false;
	}
	
	if(start[3] == regs[3]){
	
	  if(start[2] > regs[2]){
	  alert("start date should be less than end date");
	  form.enddate.focus();
          return false;
	  }
	  
	  if(start[2] == regs[2]){
	  
	  if(start[1] > regs[1]){
	  
	  alert("start date should be less than end date");
	  form.enddate.focus();
          return false;
	  }
	  
	}
	

	
	}
	
	}
	

	
	if(regs = form.enddate.value.match(reg) ) {

    if(form.enddate.value != '') {
	
      if(regs = form.enddate.value.match(reg)) {
	  
	  //for month feb
	  if(regs[2] == 2){
	  if(regs[3] % 4 === 0 ){
	  //day value between 1 to 29
	  if(regs[1] < 1 || regs[1] > 29) {
          alert("Invalid value for end date day: " + regs[1]);
          form.enddate.focus();
          return false;
        }
		} else {
		//day value between 1 to 28
		 if(regs[1] < 1 || regs[1] > 28) {
          alert("Invalid value for end date day: " + regs[1]);
          form.enddate.focus();
          return false;
        }
		}
	  
	  }
	  
	  if(regs[2] == 1 || regs[2] == 3 || regs[2] == 5 || regs[2] == 7 || regs[2] == 8 || regs[2] == 10 || regs[2] == 12){
	
        // day value between 1 and 31
        if(regs[1] < 1 || regs[1] > 31) {
          alert("Invalid value for end date day: " + regs[1]);
          form.enddate.focus();
          return false;
        }
		}
		
		 if(regs[2] == 4 || regs[2] == 6 || regs[2] == 9 || regs[2] == 11){
	
        // day value between 1 and 30
        if(regs[1] < 1 || regs[1] > 30) {
          alert("Invalid value for end date day: " + regs[1]);
          form.enddate.focus();
          return false;
        }
		}
		
        // month value between 1 and 12
        if(regs[2] < 1 || regs[2] > 12) {
          alert("Invalid value for end date month: " + regs[2]);
          form.enddate.focus();
          return false;
        }
        // year value between 2020 and 2025
        if(regs[3] < (new Date()).getFullYear() || regs[3] > 2025 ) {
          alert("Invalid value for end date year: " + regs[3] + " - must be between" + (new Date()).getFullYear() + " and 2025");
          form.enddate.focus();
          return false;
        }
      } else {
        alert("Invalid date format: " + form.enddate.value);
        form.enddate.focus();
        return false;
      }
    }

	
	}
	
	var obj = {};
			 
	obj.eventType = form.eventtype.value;
	obj.title = form.eventtitle.value;
	obj.startDate = form.startdate.value;
	obj.endDate = form.enddate.value;
	obj.Location = form.loc.value;
	
	var myEvents = [];
	myEvents.push(obj);
	
	window.localStorage.setItem("myList", JSON.stringify(myEvents));
	
	myEventList();
	
	
	}