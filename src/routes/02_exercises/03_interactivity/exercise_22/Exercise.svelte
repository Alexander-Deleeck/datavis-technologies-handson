<script>
    let counter = 0
    function myClicker(event) {
        counter += 1
    }

    function myReset(event) {
        counter = 0
    }
</script>

<button on:click={myClicker}> Click here {counter}</button>

<button on:click={myReset}> Reset counter {counter}</button>