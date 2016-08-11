# Angularjs 1 - Aula 04 - Exercício

**Nome:** Valdir Pereira Junior

**Github:** [valdir-pereira)](https://github.com/valdir-pereira)

**Data:** 10/08/2016

## 1. Adicionar mais 1 campo em todos os Controllers e utilizar ele em orderBy.

## 2. Utilizar esse valor adicional no ng-init para cada ng-repeat da View.

## 3. Criar um campo de filtro para cada ng-repeat.

**Código com todas as 3 respostas juntas pra facilitar**

```html
<!DOCTYPE html>
<html lang="en" data-ng-app="exercise04">
<head>
	<meta charset="UTF-8">
	<title> Exercise 04 </title>
	<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
</head>
<body>
<div class="container">
	<div class="row">
		<section data-ng-controller="ProfessorController as Professor">
			<h1>{{Professor.titulo}} </h1>
			<span data-ng-init="predicate = 'apelido'; reverse = true; "></span>
			
			<label>
				Busca: <input ng-model="searchTeacher">
			</label>

			<table class="table table-striped">
				<thead>
					<tr>
						<th data-ng-repeat="(key, value) in Professor.professores[0]">{{key}} </th>
					</tr>
				</thead>
				<tbody>
					<tr data-ng-repeat="professor in Professor.professores | orderBy:predicate:reverse | filter:searchTeacher">
						<td data-ng-repeat="(key, value) in professor">{{value}} </td>				
					</tr>
				</tbody>
			</table>
		</section>

		<section data-ng-controller="UserController as User">
			<h1>{{User.titulo}} </h1>
			<label> 
				Busca: <input ng-model="searchUser">
			</label>

			<span data-ng-init="predicate = 'estado'; reverse = true; "></span>
			<table class="table table-striped">
				<thead>
					<tr>
						<th data-ng-repeat="(key, value) in User.users[0]">{{key}}</th>
					</tr>
					<tbody>
						<tr data-ng-repeat="user in User.users | orderBy:predicate | filter:searchUser ">
							<td data-ng-repeat="(key, value) in user">{{value}}</td>
						</tr>
					</tbody>
				</thead>
			</table>		
		</section>

		<section data-ng-controller="CourseController as Curso">
			<h1>{{Curso.titulo}} </h1>
			<label> 
				Busca: <input ng-model="searchCurso">
			</label>

			<span data-ng-init="predicate = 'tempoCurso'; reverse = true; "></span>

			<table class="table table-striped">
				<thead>
					<tr>
						<th data-ng-repeat="(key, value) in Curso.cursos[0]">{{key}}</th>
					</tr>
					<tbody>
						<tr data-ng-repeat="curso in Curso.cursos | orderBy:predicate | filter:searchCurso ">
							<td data-ng-repeat="(key, value) in curso">{{value}}</td>
						</tr>
					</tbody>
				</thead>
			</table>		
		</section>		
	</div>
</div>
	
	<script src="angular.min.js"></script>
	<script>
	angular.module('exercise04', [])
		.controller('ProfessorController', ProfessorController)
		.controller('UserController', UserController)
		.controller('CourseController', CourseController);		

		function ProfessorController() {
			var vm = this;
			vm.titulo = "Professores do Be MEAN";
			vm.professores = [
				{name: 'Suissa', age: 30, salario: 8580, horarioAula: '13:00', apelido: 'Sussu'},
				{name: 'João', age: 33, salario: 12420, horarioAula: '19:00', apelido: 'Jão'},
				{name: 'Francine', age: 26, salario: 14500, horarioAula: '8:00', apelido: 'Fran'}
			];
		}

		function UserController() {
			var vm = this;
			vm.titulo = "Be MEAN - Usuários";
			vm.users = [
			  {name: 'Suissa', email: 'suissera@manoveio.com', estado: 'SP'}
			, {name: 'João', email: 'joao@macioesedoso.com', estado: 'MG'}
			, {name: 'Franciele', email: 'fran@quimica.com', estado: 'SC'}
			];
		}

		function CourseController() {
			var vm = this;
			vm.titulo = "Be MEAN - Cursos";
			vm.cursos = [
			  {name: 'Be MEAN', teacher: 'suissa', tempoCurso: 81}
			, {name: 'Learn Machine', teacher: 'Ivan Gustavo', tempoCurso: 42}
			, {name: 'Laravel', teacher: 'Michel Douglas', tempoCurso: 96}
			];
		}
	</script>
</body>
</html>
```