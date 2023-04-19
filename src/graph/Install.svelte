<script>
  import copyIcon from '../assets/clipboard.svg';
  const copyNPM = () => navigator.clipboard.writeText('npm install svelvet');
  const copyYarn = () => navigator.clipboard.writeText('yarn add svelvet');
</script>

<div class="installWrapper">
  <div class="installInner1">
    <h3>Get Started Easily</h3>
    <p>
      Start mapping out your ideas with our NPM package. Simply provide your
      node data to the
      <code class="highlight" style="color:#E94646;">Svelvet</code> component and
      you're ready to show off your interactive diagram - no extra configuration
      needed!
    </p>
    <a href="/docs/installation" class="btn-pink">More Info</a>
  </div>
  <div class="installInner2">
    <div class="typingWindowWrapper">
      <div class="typingWindow">
        <div class="typingNavBar">
          <div class="btn-circle" style="background-color: #FF605C;" />
          <div class="btn-circle" style="background-color: #FFBD44;" />
          <div class="btn-circle" style="background-color: #00CA4E;" />
        </div>
        <div class="typing-demo">npm install svelvet</div>
      </div>
    </div>
    <p>
      To install and save in your <code class="highlight">package.json</code>
      dependencies, run the command below using
      <strong>npm</strong>:
    </p>
    <div class="clipboard">
      <code>
        <span style="color:#9F2A39;">npm install</span> svelvet
      </code>
      <img on:click={copyNPM} src={copyIcon} alt="clipboard icon" />
    </div>
    <p>
      Or <strong>yarn</strong>:
    </p>
    <div class="clipboard">
      <code>
        <span style="color:#9F2A39;">yarn add</span> svelvet
      </code>
      <img on:click={copyYarn} src={copyIcon} alt="clipboard icon" />
    </div>
  </div>
</div>

<style>
  .installWrapper {
    display: flex;
    flex-direction: column;
    height: fit-content;
    width: 100%;
    padding: 5vw;
    align-self: center;
    text-align: left;
    margin: 10vw 0;
  }
  .installInner1 {
    order: 1;
    align-self: center;
    text-align: center;
  }
  .installInner1 h3 {
    font-size: 2rem;
    font-weight: bold;
    text-align: center;
    color: #374151;
  }
  .installInner1 p {
    margin-bottom: 1rem;
    color: #6b7280;
    text-align: left;
  }
  .installInner2 {
    display: none;
    flex-direction: column;
    padding: 5vw;
    order: 2;
    align-self: center;
  }
  .installInner2 p {
    color: #4b5563;
    margin: 1rem 0 1rem 0;
  }
  .typingWindowWrapper {
    justify-content: center;
    margin: 5vw;
  }
  .clipboard {
    display: flex;
  }
  .clipboard code {
    border-radius: 0.375rem;
    padding: 0.75rem;
    background-color: #fae4e6;
    color: #e94646;
    width: 100%;
  }
  .clipboard img {
    border-radius: 0.375rem;
    padding: 0.75rem;
    background-color: #fae4e6;
    margin-left: -1rem;
    cursor: pointer;
  }
  .typingWindow {
    overflow: hidden;
    border-radius: 0.5rem;
    background-color: #f0f0f0;
    min-width: fit-content;
    width: 100%;
    display: grid;
    place-items: center;
  }
  .typingNavBar {
    height: 1.75rem;
    width: 100%;
    background-color: #ccc;
    display: flex;
    align-items: center;
  }
  .btn-circle {
    float: left;
    margin-left: 7px;
    width: 12px;
    height: 12px;
    border-radius: 100%;
    background-color: #ff605c;
  }
  .typing-demo {
    width: 20ch;
    animation: typing 4s steps(20), blink 0.5s step-end infinite alternate;
    animation-iteration-count: infinite;
    white-space: nowrap;
    overflow: hidden;
    border-right: 3px solid;
    font-family: monospace;
    font-size: 16px;
    margin: 0.75rem 0 0.75rem 0;
  }
  @keyframes typing {
    0% {
      width: 0%;
    }
    25%,
    100% {
      width: 20ch;
    }
  }
  @keyframes blink {
    50% {
      border-color: transparent;
    }
  }

  /* tablet view */
  @media (min-width: 768px) {
    .installWrapper {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      padding: 8vw;
      text-align: left;
      margin: 1vw 0;
    }
    .installInner1 {
      order: 1;
      padding-right: 5vw;
      text-align: center;
    }
    .installInner2 {
      order: 2;
      align-self: center;
      display: flex;
      flex-direction: column;
      padding: 5vw;
    }
    .installInner1 h3 {
      text-align: left;
    }
    .installInner1 p {
      text-align: left;
    }
    .typingWindowWrapper {
      width: 320px;
      margin: 0 0 3vw 0;
    }
  }
  /* desktop view */
  @media (min-width: 1024px) {
    .installWrapper {
      padding: 5vw 15vw 5vw 15vw;
    }
  }
</style>
