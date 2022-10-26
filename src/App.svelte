<script>
    // import { Router, Route, Link } from "svelte-navigator";
    import MineApp from "./minesweeper/MineApp.svelte";
    import PianoApp from "./pianogame/pianoApp.svelte";
import SnakeApp from "./snake/SnakeApp.svelte";
    import TicApp from "./tic-tac-toe/TicApp.svelte";

  
</script>

<!-- <main class="bg-red-900 w-[100vw] h-[620px]"> -->
  <!-- <SnakeApp /> -->
<!-- </main> -->
<!-- <TicApp/> -->
<!-- <hr> -->
<!-- <MineApp /> -->
<PianoApp />
<!-- <Router>
  <header>
    <h1>History</h1>

    <nav>
      <BackButton />
      <ForwardButton />
      <Link to="/">Base</Link>
      <Link to="home">Home</Link>
      <Link to="about">About</Link>
      <Link to="blog">Blog</Link>
    </nav>
  </header>

  <main>
    <Route path="blog/*blogRoute" component={Blog} />

    <Route path="home">
      <h3>Home</h3>
      <p>Home sweet home...</p>
    </Route>

    <Route path="about">
      <h3>About</h3>
      <p>That's what it's all about!</p>
    </Route>

    <Route>
      <h3>Default</h3>
      <p>No Route could be matched.</p>
    </Route>
  </main>
</Router> -->

<!-- <script>
  import { useNavigate } from "svelte-navigator";

  const navigate = useNavigate();
</script>

<button title="Go back" on:click={() => navigate(-1)}>&lt;-</button> -->