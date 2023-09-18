---
toc: true
comments: true
layout: post
title: Bank Account Simulator
description: A cool bank account simulator that makes use of if and else statements paired with try and catch statements
type: hacks
courses: { compsci: {week: 4} }
---

<!-- 
Errors I encountered:
1. I was using a finally statement after the try catch statement to add to the total amount, without realizing that 'finally' made it so that any input would be added even if it was invalid
2. On line 48, I wrote 'document.getElementbyId' instead of 'document.getElementById' (capitalization error). Funnily enough, the catch statement actually displayed the error ('document.getElementbyId is not a function')and helped me fix it!
 -->

<html>

<head>
    <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.4/css/jquery.dataTables.min.css">
    <script type="text/javascript" language="javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script>var define = null;</script>
    <script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.13.4/js/jquery.dataTables.min.js"></script>
</head>

<body>

<table id="demo" class="table">
  <thead>
    <tr>
      <th>Item</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Burger</th>
      <th>$4.00</th>
    </tr>
    <tr>
      <th>Fries</th>
      <th>$2.00</th>
    </tr>
    <tr>
      <th>Drink</th>
      <th>$1.00</th>
    </tr>
  </tbody>
</table>
<script>$("#demo").DataTable();</script>

<p>Please deposit an amount between 1-1000 dollars</p>

<!-- Code to create the deposit button -->
<input id="demo" type="text">
<button type="button" onclick="deposit()">Deposit</button>
<p id="message"></p>
<!-- Displays the total amount of dollars in bank account -->
<p>Total: <span id="total">0</span> dollars</p>

<script>
var menu = {
  burger: 4.00,
  fries: 2.00,
  drink: 1.00
}
//Sets amount in bank account to 0
var totalAmount = 0;

function deposit() {
  //Sets error display to empty
  const message = document.getElementById("message");
  message.innerHTML = "";
  let x = document.getElementById("demo").value;
  //Checks if the input is valid
  try { 
    if(x.trim() == "")  throw "empty";
    if(isNaN(x)) throw "not a number";
    x = Number(x);
    if(x > 1000)  throw "too much";
    if(x < 1)   throw "too little";

    //Updates if input is valid
    totalAmount += x;
    document.getElementById("total").textContent = totalAmount;
  }
  //If input is not valid, display the error
  catch(err) {
    message.innerHTML = "Deposit is " + err;
  }
}

function withdrawal() {

}
</script>

</body>
</html>