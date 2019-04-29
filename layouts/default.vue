<template>
  <div>
		<div id="banner" class="w-full text-center capitalize pt-3 pb-3 bg-black text-white font-bold	">
			<p class="capitalize">FOR INTERNAL USE ONLY</p>
		</div>
		<header class="container mx-auto rpd-top">
			<div id="logo" class="w-full text-center text-5xl bg-grey-lighter pt-2 pb-2	">RPD Operations</div>
			<nav class="content-center">
				<ul class="list-reset flex border-b">
					<li class="-mb-px mr-1">
						<a class="pt-3 pb-3 bg-white inline-block py-2 px-4 text-blue-dark font-semibold" href="/">Home</a>
					</li>
					<li class="mr-1">
						<a class="pt-3 pb-3 bg-white inline-block py-2 px-4 text-blue hover:text-blue-darker font-semibold" href="/login/">Login</a>
					</li>
					<li class="mr-1">
						<a class="pt-3 pb-3 bg-white inline-block py-2 px-4 text-blue hover:text-blue-darker font-semibold" href="/admin/add-event">Add Event</a>
					</li>
				</ul>
			</nav>
		</header>
    <nuxt />
		<footer class="w-full text-center capitalize pt-3 pb-3 bg-black text-white font-bold">
			Copyright RPD
		</footer>
  </div>
</template>

<style>

@import url("https://use.typekit.net/xfs0pau.css");
#logo {
	font-family: ocr-a-std, monospace;
	font-weight: 400;
	font-style: normal;
}

html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
} 

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}

.rpd-top {

}

</style>
