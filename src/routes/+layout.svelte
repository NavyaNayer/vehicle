<script>
    import { onMount } from 'svelte';
  </script>
  
  <style>
    header {
      background-color: #343a40;
      color: white;
      padding: 1rem;
      text-align: center;
    }
    footer {
      background-color: #343a40;
      color: white;
      padding: 1rem;
      text-align: center;
      position: relative;
      bottom: 0;
      width: 100%;
    }
    main {
      min-height: calc(100vh - 120px); /* Adjust based on header and footer height */
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }
    nav {
      margin: 1rem 0;
    }
    nav a {
      color: white;
      text-decoration: none;
      margin: 0 10px;
      padding: 0.5rem 1rem;
      border: 1px solid transparent;
      border-radius: 5px;
      transition: background-color 0.3s;
    }
    nav a:hover {
      background-color: #0056b3;
    }
  </style>
  
  <header>
    <h1>Speed Vision ANPR</h1>
    <nav>
      <a href="/">Home</a>
      <a href="/camera">Camera</a>
      <a href="/results">Results</a>
      <a href="/history">History</a>
      <a href="/settings">Settings</a>
      <a href="/help">Help</a>
      <a href="/about">About</a>
      <a href="/contact">Contact</a>
    </nav>
  </header>
  
  <main>
    <slot />
  </main>
  
  <footer>
    <p>&copy; 2024 Speed Vision. All Rights Reserved.</p>
  </footer>
  