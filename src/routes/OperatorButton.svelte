<script>
    export let operator;
    export let calculatorString;
    function updateCalculator(input) {
        if (calculatorString[calculatorString.length - 1] === '=') calculatorString= calculatorString.substring(0, calculatorString.length - 1)
        if (/\d/.test(calculatorString[calculatorString.length - 1])) calculatorString += input
        if (calculatorString.length === 0 && input === '(') calculatorString += input
    }
</script>

<button class='operator' on:click={() => updateCalculator(operator)}>{operator}</button>

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
</style>