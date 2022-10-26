<template>
	<div class="container">
		<div class="card">
			<div class="card-body">
				<h5 class="card-title text-center">Simple Todo</h5>

				<div class="input-group mt-3">
					<input type="text" class="form-control" placeholder="Type here...">
					<button class="btn btn-primary" type="button" id="button-addon2">Add</button>
				</div>
			</div>
		</div>

		<div class="card my-3">
			<ul class="list-group overflow-hidden">
				<div class="d-flex justify-content-between align-items-center">
					<li class="list-group-item w-100 border-0">An item</li>
					<button type="button" class="btn btn-sm btn-success mx-1 fw-bold">Done</button>
					<button type="button" class="btn btn-sm btn-danger mx-1 fw-bold">X</button>
				</div>
				<div class="d-flex justify-content-between align-items-center">
					<li class="list-group-item w-100 border-0">An item</li>
					<button type="button" class="btn btn-sm btn-success mx-1 fw-bold">Done</button>
					<button type="button" class="btn btn-sm btn-danger mx-1 fw-bold">X</button>
				</div>
				<div class="d-flex justify-content-between align-items-center">
					<li class="list-group-item w-100 border-0">An item</li>
					<button type="button" class="btn btn-sm btn-success mx-1 fw-bold">Done</button>
					<button type="button" class="btn btn-sm btn-danger mx-1 fw-bold">X</button>
				</div>
				<div class="d-flex justify-content-between align-items-center">
					<li class="list-group-item w-100 border-0">An item</li>
					<button type="button" class="btn btn-sm btn-success mx-1 fw-bold">Done</button>
					<button type="button" class="btn btn-sm btn-danger mx-1 fw-bold">X</button>
				</div>
			</ul>
		</div>
	</div>
</template>

<style>
body {
	display: flex;
	min-height: 100vh;
	justify-content: center;
	align-items: center;
}
</style>
