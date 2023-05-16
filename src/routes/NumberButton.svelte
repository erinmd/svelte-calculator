<script>
    export let number;
    export let calculatorString;
    function updateCalculator(input) {
        calculatorString += input
    }
</script>

<button on:click={() => updateCalculator(number)}>{number}</button>

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
</style>