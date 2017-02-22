# IT102.Shoots.Ladders
Excersize in functions with private variables
Your assignment is to adapt the Louie vs Sal race to 100 card game to make an online version of the classic board game Chutes and Ladders. Here are the requirements:

    2 players (minimum) race to 100
    on each turn, all the players roll 2 (six-sided) dice each
    each player advances the total on his/her 2 dice
    there is also a "wild card" button

When the wild card button is pressed, one of the following outcomes will happen at random:

    1 or both players advance 10 (go up a ladder)
    1 or both players fall back 10 (down a chute)
    no movement - just a silly message

<!DOCTYPE html>
<html>
<body>

<h2> Lucky Louie and Slippery Sal </h2>

<button type="button" onclick="showTurn()">Deal!</button>

<p id="lucky">Lucky</p>
<p id="slippery">Slippery</p>

<script>

//var luckyTotal = 0; //uncomment for a global variable
var slipperyTotal = 0;

function draw(){
return Math.ceil(Math.random()*11);
}

// Louie's Original Function
//function luckyTurn(){
// var luckyTotal = 0;
// luckyTotal += draw();
// return luckyTotal;
//}

// Louie's Function with Closure
var luckyTurn = (function () {
var luckyTotal = 0;
return function () {return luckyTotal += draw();}
})();

//test code
//alert (typeof luckyTurn);

//Sal's function
function slipperyTurn(){
slipperyTotal += draw();
//luckyTotal -= 1; //notice the closure breaks Sal's cheat
return slipperyTotal;
}

function showTurn(){
document.getElementById("lucky").innerHTML = "Lucky: " + luckyTurn();
document.getElementById("slippery").innerHTML = "Slippery: " + slipperyTurn();
}

</script>

</body>
</html>
