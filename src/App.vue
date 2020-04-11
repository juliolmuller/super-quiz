<template>
	<div id="app">
    <header id="app-header">
      <h1>Super Quiz</h1>
    </header>
    <div class="wrapper">
      <main id="app-main">
        <!-- content -->
      </main>
    </div>
    <footer id="app-footer">
      <span>Todos os direitors reservados &copy; 2020 LacusSoft</span>
    </footer>
	</div>
</template>

<script>
export default {}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
	color: #FFF;
  font-family: 'Oswald', sans-serif;
}

body {
	background: linear-gradient(to right, rgb(0, 0, 70), rgb(28, 181, 224));
}

html, body, #app {
  height: 100%;
}

#app {
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;

	display: flex;
	flex-direction: column;
	align-items: center;
}

#app-header {
  flex-shrink: 0;
}

#app-header h1 {
  padding: 2rem;
	font-weight: 200;
	font-size: 4rem;
}

.wrapper {
  flex-grow: 1;
  display: flex;
  width: 100%;
}

#app-main {
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
}

#app-footer {
  flex-shrink: 0;
}

#app-footer span {
  display: block;
  padding: 2rem;
  color: #aaa;
  font-size: small;
}

@keyframes flip-out {
	from { transform: rotateY(0deg); }
	to { transform: rotateY(90deg); }
}

@keyframes flip-in {
	from { transform: rotateY(90deg); }
	to { transform: rotateY(0deg); }
}

.flip-enter-active {
	animation: flip-in 0.3s ease;
}

.flip-leave-active {
	animation: flip-out 0.3s ease;
}
</style>
