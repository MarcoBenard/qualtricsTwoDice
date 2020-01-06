# Two Dice in Qualtrics

## Embedded data

- In the 'Survey Flow' add a new 'Embedded Data' Element
- Move this new Element to the top of the flow
- Create 2 embedded data values to store the dice values:
  - dice1
  - dice2

## Look & Feel

In the **Header** paste the following script.

(click 'edit' and use the 'source-button, <>' to paste the code in HTML-mode!)

```JavaScript
<script>
        var face1 = new Image();
        face1.src = "http://mneme.psy.vu.nl/etp/so/dice/1-red.png";
        var face2 = new Image();
        face2.src = "http://mneme.psy.vu.nl/etp/so/dice/2-red.png";
        var face3 = new Image();
        face3.src = "http://mneme.psy.vu.nl/etp/so/dice/3-red.png";
        var face4 = new Image();
        face4.src = "http://mneme.psy.vu.nl/etp/so/dice/4-red.png";
        var face5 = new Image();
        face5.src = "http://mneme.psy.vu.nl/etp/so/dice/5-red.png ";
        var face6 = new Image();
        face6.src = " http://mneme.psy.vu.nl/etp/so/dice/6-red.png";

        // --- //

        var Bface1 = new Image();
        Bface1.src = "http://mneme.psy.vu.nl/etp/so/dice/1-green.png";
        var Bface2 = new Image();
        Bface2.src = "http://mneme.psy.vu.nl/etp/so/dice/2-green.png";
        var Bface3 = new Image();
        Bface3.src = "http://mneme.psy.vu.nl/etp/so/dice/3-green.png";
        var Bface4 = new Image();
        Bface4.src = "http://mneme.psy.vu.nl/etp/so/dice/4-green.png";
        var Bface5 = new Image();
        Bface5.src = "http://mneme.psy.vu.nl/etp/so/dice/5-green.png ";
        var Bface6 = new Image();
        Bface6.src = " http://mneme.psy.vu.nl/etp/so/dice/6-green.png";

        function throwBoth() {
            // get the button
            var throwButton = document.getElementById("throwButton");
            throwdice1();
            throwdice2();
            // hide the button
            throwButton.style.display = "none";
        }

        function throwdice1() {
            // get random number
            var randomdice1 = Math.floor(6 * Math.random()) + 1;
            // Store value in data
            Qualtrics.SurveyEngine.setEmbeddedData("dice1", randomdice1);
            // replace dice image
            document.images["mydice1"].src = eval("face" + randomdice1 + ".src");
        }

        function throwdice2() {
            // get random number
            var randomdice2 = Math.floor(6 * Math.random()) + 1;
            // Store value in data
            Qualtrics.SurveyEngine.setEmbeddedData("dice2", randomdice2);
            // replace dice image
            document.images["mydice2"].src = eval("Bface" + randomdice2 + ".src");
        }
    </script>
```

## Survey / Question

Create a new 'Descriptive Text' question, enter the 'HTML-view' and paste the following code into the question:

```JavaScript
<div>
   <img src="http://mneme.psy.vu.nl/etp/so/dice/0-red.png" id="mydice1" alt="">
   &nbsp;&nbsp;
   <img src="http://mneme.psy.vu.nl/etp/so/dice/0-green.png" id="mydice2" alt="">
</div>
<div>
   <input id="throwButton" type="button" value="Throw the dice!!" onclick="throwBoth()">
</div>
```
