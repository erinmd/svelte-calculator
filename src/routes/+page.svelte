<script>
    import NumberButton from "./NumberButton.svelte";
    import OperatorButton from "./OperatorButton.svelte";
    let calculatorString = ''
    let ans = '';
    function calculateAnswer(){
        let calculation = ''
        for (let i = 0; i < calculatorString.length; i++) {
            const char = calculatorString[i]
            if (char === '÷') calculation += '/'
            else if (char === '×') calculation += '*'
            else calculation += char
        }
        calculatorString += '='
        try {
            ans = eval(calculation)
        } catch {
            ans = 'invalid calculation'
        }
    }
</script>

<h1>Calculator</h1>
<section class='calculatorDisplay'>
    <p class='sum'>{calculatorString}</p>
    <p class='answer'>{ans}</p>
</section>
<section>
    <OperatorButton bind:calculatorString={calculatorString} operator={'('} />
    <OperatorButton bind:calculatorString={calculatorString} operator={')'} />
    <button class='operator' on:click={() => {
        calculatorString = ''
        ans = ''
        }}>C</button>
    <button class='operator' on:click={() => {
        calculatorString = calculatorString.substring(0, calculatorString.length - 1)
        ans = ''
        }}>←</button>
</section>
<section>
    <NumberButton bind:calculatorString={calculatorString} number={'7'} />
    <NumberButton bind:calculatorString={calculatorString} number={'8'} />
    <NumberButton bind:calculatorString={calculatorString} number={'9'} />
    <OperatorButton bind:calculatorString={calculatorString} operator={'÷'} />
</section>
<section>
    <NumberButton bind:calculatorString={calculatorString} number={'4'} />
    <NumberButton bind:calculatorString={calculatorString} number={'5'} />
    <NumberButton bind:calculatorString={calculatorString} number={'6'} />
    <OperatorButton bind:calculatorString={calculatorString} operator={'×'} />
</section>
<section>
    <NumberButton bind:calculatorString={calculatorString} number={'1'} />
    <NumberButton bind:calculatorString={calculatorString} number={'2'} />
    <NumberButton bind:calculatorString={calculatorString} number={'3'} />
    <OperatorButton bind:calculatorString={calculatorString} operator={'-'} />
</section>
<section>
    <NumberButton bind:calculatorString={calculatorString} number={'0'} />
    <NumberButton bind:calculatorString={calculatorString} number={'.'} />
    <button class='operator' on:click={calculateAnswer}>=</button>
    <OperatorButton bind:calculatorString={calculatorString} operator={'+'} />
</section>

<style>
    button {
        color:rgb(235, 235, 255);
        background-color: rgb(0, 105, 105);
        width: 100px;
        height: 100px;
        border-radius: 10px;
        margin: 5px;
        font-size: 40px;
    }
    .operator {
        background-color: grey
    }
    .calculatorDisplay {
        border: solid 2px;
        width: 435px;
        height: 75px;
        margin: 5px;
        border-radius: 10px;
    }
    p {
        margin: 5px;
        height: 25px
    }

    .answer {
        text-align: right;
        font-size: 20px;
    }
</style>