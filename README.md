# Portfolio Links

|Name and Link|Description|Technologies Used|
|---|---|---|
|[UTIN-SLAA](https://help.github.com/articles/page-build-failed-tag-not-properly-terminated/)| free-lance work completed for local 501-3(c) |JavaScript, ReactJS, HTML5, CSS3|
|[Utah Dermagraphics](https://trrapp12.github.io/utahdermagraphics/)| free-lance work done to improve a local business owners website| JavaScript, HTML5, CSS3|
|[Recipe Organizer](http://trrapp12.github.io/recipe_organizer/)| V-School Final Project * Basic CRUD functionality allowing users to add, edit, and delete recipes. * It allows users to collect, sort, organize, and browse recipes. * It allows for photos to be uploaded. * It allows users to sort and retrieve recipes by name or by ingredient type. * It links to a few Pinterest sites for resources to other recipes.| Django, SQLite, JavaScript, HTML5, CSS3, MVC|
|[Agents of Shield Directory](http://trrapp12.github.io/avengers_agents_of_shield_directory/)| Utilizes the concept of modules to create more readable and manageable code that applies DRY principles. * Utilizes MVC/MVW architecture * Creates three different controllers that receive user input and makes calls to model objects and the view to perform appropriate actions. * Creates a module that uses ng-route and $routeProvider to direct the consumer to the appropriate urls and views. * Uses $http to read a JSON object. * Filters content using directives. * Uses two-way data binding to make queries. * Uses deep-linking to navigate through views. | JavasScript, CSS3, HTML5|
|[Calculator](https://trrapp12.github.io/refactored-calculator/)|  creates a HTML and JavaScript calculator. * Preforms math on multiple integers. * Handles operations from simple arithmatic to advanced functions like sin, cos, tan, √, ∛, π, a3. * functionality to switch between radian and degrees for all sin, cos, and tan equations. *  Classical set-up with GUI interface including a button with the equals sign, buttons for numbers 0-9, and buttons for the following operators (+, -, /, * , sin, cos, tan, √, ∛, π, a3 ),  | JavasScript, CSS3, HTML5|
|[Slap-Happy](https://trrapp12.github.io/Slap-Happy/)| Demonstrates the correct use of functions, conditionals, loops, arrays.  * Properly sequences JavaScript statements. * Changes the DOM based on application state (win/loss, valid/invalid guess). * Selects a random word from a dictionary of words. * Displays all guesses on the user's screen so the user knows what letters he/she has already guessed. * Displays a visual indication for each letter in the word. * Displays the number of turns remaining. * Decrements the number of turns remaining. * Displays letters guessed in the position that they are contained in the word. * Includes a GitHub Repo url, containing an index.html, one or more CSS files, one or more JavaScript files (e.g. js/main.js) | JavasScript, CSS3, HTML5|
|[KONAMI](https://trrapp12-ironyard.github.io/konami/)| basic keystroke listener which listens to keys pushed and displays them to the screen, but with a cool KONAMI easter-egg| JavaScript, HTML5, CSS3|
|[wk-01-alpha](https://help.github.com/articles/page-build-failed-tag-not-properly-terminated/)| a cool tribute to all things fast| JavaScript, HTML5, CSS3|
|[Sundae Worship](https://trrapp12.github.io/Sundae-Worship/)| a basic website with an ice-cream theme|JavaScript, HTML5, CSS3|
|[Parallax Example](http://trrapp12.github.io/parallax-example/)| uses a parallax library to do some awesome interaction with mouse movement and parallax| Parallax, JavaScript, Photoshop|
|[CSS/JS Clock](https://trrapp12-ironyard.github.io/CSS_JS_clock/)| uses CSS and Javascript to get current time and convert it into an analog clock display with animation | HTML5, JavaScript, CSS3|
|[Flex-Box](https://trrapp12-ironyard.github.io/flex-box/)| simple demonstration of flex-box CSS | HTML5, CSS3|

Current Code Examples working with GTM: 

<details>
  <summary> JavaScript to write dynamic HTML script tag </summary>

```javascript

(function () {
  // define function
  function addScript() {
    //select main wrapper
    var c = document.querySelector("#mainWrapper");
    // create outer div
    var el = document.createElement('div');
    //give el an id
    el.id = "teconsent";
    // create inner script
    var innerEl = document.createElement('script');
    //give inner script src attribute, async attribute, and cross origin attribute
    innerEl.setAttribute('src', 'https://consent.trustarc.com/notice?domain=nuskin.com&country=gb&js=nj2&c=teconsent&language=en_GB&text=true&noticeType=bb&behavior=implied');
    innerEl.setAttribute('async', 'async');
    innerEl.setAttribute('crossorigin', '');
    // append div to wrapper
    c.appendChild(el)
    // append script to div
    el.appendChild(innerEl);
  };
    try {
    //call's function in try catch in case mainwrapper wasn't drawn for some reason, doesn't break the page
    addScript();
  }
  catch(error) {
    console.error(error);
    // expected output: ReferenceError: nonExistentFunction is not defined
    // Note - error messages will vary depending on browser
  }
})()
```
</details>

<details>
  <summary>JavaScript to scrape dataLayer for an "orderUpdated" Event, then retrieve the amount</summary>
  
  ```javascript
  function () {
  var a = window.dataLayer; 
  var b = [];
  for (i=0; i <a.length; i++) {
    if (a[i].event === "orderUpdated") {
      b.push(a[i])   
    }
  }
  var c = b.pop();
  return c[0]["orderTotals"].pointsUsed;
}
```
</details>

<details>
  <summary>JavaScript "Normalizer" (takes the action from a GTM tag and normalizes the capitalization)</summary>
  
  ```javascript
  function () {
  if(window.google_tag_manager["GTM-TWJS4J3"]) {
    var a = window.google_tag_manager["GTM-TWJS4J3"].dataLayer.get("context");
    var b = a.charAt(0).toUpperCase();
    var c = a.slice(1).toLowerCase();
    var d = b.concat(c);
    return d; 
    console.log("true")
  }
  else if (window.google_tag_manager["GTM-5RNZGHC"]) {
    var a = window.google_tag_manager["GTM-5RNZGHC"].dataLayer.get("context");
    var b = a.charAt(0).toUpperCase();
    var c = a.slice(1).toLowerCase();
    var d = b.concat(c);
    return d; 
    console.log("false")
  }
  else {
    console.log("neither 'GTM-TWJS4J3' nor 'GTM-5RNZGHC' buckets detected")
  }
}
```
</details>

<details>
  <summary>Button Click Event Listener that functions even through a shadowRoot </summary>

```javascript 
(function () {
  //create node array of buttons
  var buttons = document.querySelectorAll("[data-buttonNumber]");

  // iterate over array to individually apply addEventListener
  for (i = 0; i < buttons.length; i++) {

    // adds addEventListener onto buttons, since the attribute is not defined on the buttons themselves
    buttons[i].shadowRoot.children[1].addEventListener("click", function (evt) {
          // have to work way back up the DOM past shadowRoot to get the attribute, again, since listener has to be put on button, but attribute was put on a parent element instead
          var content = this.parentNode.host.getAttribute('data-buttonnumber');
          var stringContent = content.toString();
          dataLayer.push({
            'event' : 'buttonPushed',
            'value' : stringContent
          });
    });
  }
})();
```
</details>

<details>
  <summary>IFFE statement that logs user tier into Local Storage </summary>
  
  ```javascript
  (function() {
    return JSON.parse(JSON.parse(JSON.stringify(localStorage.loyaltyData))).userTier.name
  })();
  ```
</details>

<details>
  <summary>Listener to check if radio is checked</summary>
  
  ```javascript 
(function (){

  var parent = document.getElementsByClassName('create-invite-radio-group');
  var group = document.getElementsByClassName("ns-radio");
  var left = group[0];
  var middle = group[1];
  var right = group[2]
  
  parent[0].addEventListener('click', function() {
    if (left.classList.contains("checked")) {
      console.log('left checked')
      dataLayer.push({
        'event': 'linkTypeSelected',
        'data' : 'customer'
      })
    }
    else if (middle.classList.contains("checked")) {
      console.log('middle checked')
      dataLayer.push({
        'event': 'linkTypeSelected',
        'data' : 'Member'
      })
    }
    else if (right.classList.contains("checked")) {
      console.log('right checked')
      dataLayer.push({
        'event': 'linkTypeSelected',
        'data' : 'Brand Affiliate'
      })
    }
    else {
      console.log('none checked')
    }
  })

})()
```
</details>

<details>
  <summary>Listener to Get Elapsed Time</summary>
  
  ```javascript 
(function () {
var startTime = new Date().getTime();
var paymentSection = document.getElementById('checkout-edit-payment');
  var pageTitle={{Page Title}};
console.log("beginning of function, startTime is " + startTime);

window.addEventListener('click', function (evt){
  
if (evt.target.parentNode.id === 'backToCartButton' && pageTitle==Checkout) {
var updatedTime = new Date().getTime();

console.log("in backToCartButton, startTime is " + startTime);
var elapsedTimeNew = startTime ? ((updatedTime - startTime)/1000) : '1';
window.dataLayer.push({
'event': 'calculateTimeUponExitNew',
'elapsedTimeNew': elapsedTimeNew,
'message' : 'backToCartButton clicked'
});
}
})
paymentSection.addEventListener('click', function (evt) {
if (startTime === null) {
startTime = new Date().getTime();
console.log("in eventListener, startTime is " + startTime);
return;
}
// if this is the arrow being clicked or the continue button being clicked
if (evt.target.classList.contains('section-edit') || evt.target.id === 'paymentContinueButton') {
var updatedTime = new Date().getTime();
window.dataLayer.push({
'event': 'calculateTimeUponExitNew',
'elapsedTimeNew': ((updatedTime - startTime)/1000),
'message' : 'arrow or continue clicked'
});
}
}
);
window.addEventListener('beforeunload', function() {
if (startTime === null) {
startTime = new Date().getTime();
var updatedTime = new Date().getTime();
window.dataLayer.push({
'event': 'calculateTimeUponExitNew',
'elapsedTimeNew': ((updatedTime - startTime)/1000),
'message' : 'beforeunload activated with start time null'
});
}
else {
var updatedTime = new Date().getTime();
  console.log("hey there", updatedTime, startTime);
window.dataLayer.push({
'event': 'calculateTimeUponExitNew',
'elapsedTimeNew': ((updatedTime - startTime)/1000),
'message' : 'beforeunload activated with start time set'
});
}
});
})();
```
</details>

<details>
  <summary>Dynamically detect country code in url to determine which external ID entry to pull from local Storage</summary>
  
  ```javascript
  (function () {
  var url = window.location.href;
  var countryCodeRegEx = /[a-z]{2}_[A-Z]{2}/ ;
  var countryCode = countryCodeRegEx.exec(url).toString().slice(-2);
  console.log(countryCode);
  var localStorageCountry = "orders-" + countryCode
  var a = JSON.parse(window.localStorage[localStorageCountry]);
  return a[0].externalId; 
})()
```
</details>

<details>
  <summary>IFFE to change camelCase to TitleCase</summary>
  
  ```javascript
  (function () {
  // var eventName = {{Event}};
  var eventName = "skinConsult"
  var firstWord = /^[a-z]*(?=[A-Z])/;
  var subsequentWords = /[A-Z](?<=[A-Z])[a-z]*/
  var array = [];

  function pushFirstName () {
    var newName = eventName.match(firstWord).toString();
    var newNameCap = newName.charAt(0).toUpperCase() + newName.slice(1)
    array.push(newNameCap);
  }
  function pushSubsequentWords () {
    array.push(eventName.match(subsequentWords).toString());
  }
  function concatPhrase () {
    // console.log(array.join(' '));
    return array.join(" ");
  }

  pushFirstName();
  pushSubsequentWords();
  concatPhrase();

})();
```
</details>




