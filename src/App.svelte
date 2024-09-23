<script>import "./app.css";
import { Router, Route } from "svelte-navigator";
import Layout from "./components/common/layout.svelte";
import Home from "./routes/home.svelte";
import MyProjects from "./routes/myProjects.svelte";
import TopNavBar from "./components/common/topNavBar.svelte";</script>

<Layout>
  <TopNavBar></TopNavBar>  
  <Router>
    <Route path="/" component={Home}></Route>
    <Route path="/my-projects" component={MyProjects}></Route>
  </Router>
</Layout>
