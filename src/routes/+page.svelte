<script>
    import { goto } from '$app/navigation';
  </script>
  
  <style>
    .container {
      text-align: center;
      padding: 2rem;
    }
    h1 {
      font-size: 2.5rem;
      margin-bottom: 1rem;
    }
    p {
      font-size: 1.2rem;
      margin: 1rem 0;
    }
    .cta-button {
      padding: 1rem 2rem;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 1rem;
      margin: 0.5rem;
    }
    .cta-button:hover {
      background-color: #0056b3;
    }
  </style>
  
  <div class="container">
    <h1>Welcome to Speed Vision ANPR</h1>
    <p>Experience cutting-edge vehicle detection and number plate recognition.</p>
    <p>Key Features:</p>
    <ul>
      <li>Real-time Video Processing</li>
      <li>Vehicle Detection</li>
      <li>Number Plate Recognition</li>
      <li>Speed Estimation</li>
      <li>Colour Detection</li>
    </ul>
    <button class="cta-button" on:click={() => goto('/camera')}>
      Get Started
    </button>
    <div>
      <button class="cta-button" on:click={() => goto('/results')}>View Results</button>
      <button class="cta-button" on:click={() => goto('/history')}>History</button>
      <button class="cta-button" on:click={() => goto('/settings')}>Settings</button>
      <button class="cta-button" on:click={() => goto('/help')}>Help</button>
      <button class="cta-button" on:click={() => goto('/about')}>About</button>
      <button class="cta-button" on:click={() => goto('/contact')}>Contact</button>
    </div>
  </div>
  