<script>
  $: quotes = [];

  function fetchQuote() {
    fetch("http://quotable.io/random")
      .then((res) => res.json())
      .then((data) => {
        quotes = data;
      });
  }

  fetchQuote();
</script>

<main>
  <div>
    <p>{quotes.content}</p>
    <p><strong>- {quotes.author}</strong></p>
    <button on:click={fetchQuote}>New Quote</button>
  </div>
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Merriweather:wght@400;700&display=swap");

  :root {
    box-sizing: border-box;
  }

  div {
    display: flex;
    flex-direction: column;
    align-items: center;

    width: 60vw;

    text-align: center;
    padding: 1em;
  }

  main {
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: "Merriweather", sans-serif;
    margin: 0;
    padding: 0;
  }

  p {
    line-height: 1.5em;
    font-size: 1.5em;
    margin: 1em;
  }

  button {
    border-radius: 1em;
    height: 3em;
    width: 7em;
    font-size: 1em;
    margin: 1.5em;
    cursor: pointer;

    border: 2px solid rgb(69, 187, 69);
    background: #caffbf;
  }

  @media (max-width: 640px) {
    main {
      width: 100vw;
    }
  }
</style>
