<script>
  let result = 0;
  let var1 = 0;
  let valString = "";
  let operationFlag = false;
  let resultFlag = false;
  let selectedOperand = "";

  function select(num) {
    valString += num;
    result = parseFloat(valString);
  }
  function clearInput() {
    valString = "";
    result = 0;
  }
  function handleOperand(operand) {
    if (operationFlag === false) {
      selectedOperand = operand;
      var1 = result;
      clearInput();
      operationFlag = true;
      // add color to selected button
      // document.getElementById(operand).classList.add("btn-pressed");
      btn_pressed = true;
    }
  }
  function showResult() {
    if (operationFlag) {
      if (selectedOperand === "+") {
        result += var1;
      } else if (selectedOperand === "-") {
        result = var1 - result;
      } else if (selectedOperand === "*") {
        result *= var1;
      } else if (selectedOperand === "/") {
        result = var1 / result;
      }
      resultFlag = true;
      operationFlag = false;
    }
  }
</script>

<body>
  <div class="container">
    <h1><div class="heading glass">Calculator</div></h1>
    <div class="calc-keypad">
      <input
        class="btn-value"
        type="number"
        bind:value={result}
        placeholder="Enter something"
      />
      <div class="row">
        <button class="btn glass" on:click={() => select("1")}>1</button>
        <button class="glass btn" on:click={() => select("2")}>2</button>
        <button class="glass btn" on:click={() => select("3")}>3</button>
        <button
          class="btn btn-op glass"
          id="+"
          on:click={() => handleOperand("+")}>+</button
        >
      </div>
      <div class="row">
        <button class="btn glass" on:click={() => select(4)}>4</button>
        <button class="btn glass" on:click={() => select(5)}>5</button>
        <button class="btn glass" on:click={() => select(6)}>6</button>
        <button
          class="btn btn-op glass"
          id="-"
          on:click={() => handleOperand("-")}>-</button
        >
      </div>
      <div class="row">
        <button class="btn glass" on:click={() => select(7)}>7</button>
        <button class="btn glass" on:click={() => select(8)}>8</button>
        <button class="btn glass" on:click={() => select(9)}>9</button>
        <button
          class="btn btn-op glass"
          id="*"
          on:click={() => handleOperand("*")}>*</button
        >
      </div>
      <div class="row">
        <button class="btn glass" on:click={() => select(0)}>0</button>
        <button class="btn glass" on:click={() => select(".")}>.</button>
        <button class="btn glass" on:click={showResult}>=</button>
        <button
          class="btn glass btn-op"
          id="/"
          on:click={() => handleOperand("/")}>/</button
        >
      </div>
      <div class="row">
        <button class="btn glass btn-block" on:click={clearInput}>Clear</button>
      </div>
    </div>
  </div>
</body>

<!-- svelte-ignore missing-declaration -->
<style>
  body {
    background-color: deepskyblue;
    /* background: #c8dce7; */
  }

  .container {
    padding-left: 15px;
    padding-right: 15px;
    margin-left: auto;
    margin-left: auto;
    text-align: center;
  }

  .glass {
    background: rgba(255, 255, 255, 0.7);
    border-radius: 3em;
    z-index: 1;
    -webkit-backdrop-filter: blur(20px);
    backdrop-filter: blur(20px);
    border: solid 2px transparent;
    background-clip: padding-box;
    -webkit-box-shadow: 10px 10px 10px rgba(46, 54, 68, 0.03);
    box-shadow: 10px 10px 10px rgba(46, 54, 68, 0.03);
  }
  .heading {
    display: inline-block;
    width: 285px;
    padding: 0.375rem 0.75rem;
  }

  .btn {
    display: inline-block;
    font-size: 20px;
    background: rgba(255, 255, 255, 0.9);
    text-align: center;
    vertical-align: middle;
    padding: 0.375rem 0.75rem;
    width: 66px;
    height: 56px;
    border-radius: 3px;
    cursor: pointer;
    box-shadow: 0px 4px rgba(0, 0, 0, 0.2);
  }
  .btn-block {
    width: 278px;
  }
  .btn-op {
    background: #fada3b;
  }
  .btn-value {
    width: 278px;
    border: 0;
    text-align: center;
    font-size: 20px;
    box-shadow: 0px 3px rgba(0, 0, 0, 0.2);
  }
</style>
