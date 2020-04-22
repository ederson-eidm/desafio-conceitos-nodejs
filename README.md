
<img alt="GoStack" src="https://storage.googleapis.com/golden-wind/bootcamp-gostack/header-desafios.png" />

<h3 align="center">
  Challange 02: Concepts  Node.js
</h3>



<p align="center">
  <a href="#rocket-about-challenge">About Challenge</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#memo-license">Licença</a>
</p>

## :rocket: About Challenge

This will be an application to store repositories in your portfolio, which will allow the creation, listing, update and removal of the repositories, and also allow the repositories to receive "likes".


### Application routes


- **`POST /repositories`**: The route must receive `title`,` url` and `techs` within the body of the request, the URL being the link to the github of this repository. When registering a new project, it must be stored inside an object in the following format: `{ id: "uuid", title: 'Desafio Node.js', url: 'http://github.com/...', techs: ["Node.js", "..."], likes: 0 }`; 

Make sure the ID is a UUID, and always start the likes as 0.

- **`GET /repositories`**: Route that lists all repositories;

- **`PUT /repositories/:id`**: The route should only change the `title`,` url` and `techs` of the repository that has the` id` equal to the `id` present in the parameters of the route;

- **`DELETE /repositories/:id`**: The route must delete the repository with the `id` present in the route parameters;

- **`POST /repositories/:id/like`**: The route must increase the number of likes from the specific repository chosen through the `id` present in the route parameters, at each call of this route, the number of likes must be increased by 1;

**Tip**: Above we use `POST` in a route, even if it changes the number of likes in the repository without creating anything directly.

If we semantically divide the responsibilities of our application into entities, the like would be an entity, and the repository would be another entity.

With this separation, we have different business rules for each entity, so by calling the route 'like' and adding only one like, we can interpret that we are creating a new like, and not updating the likes.

So why not use `PUT` instead of` POST`? Precisely because we are "creating" A new like, and not updating the number of likes to any other value.

It may be difficult to see because it is just a number, but think that each like is saved in a table in the bank with the user who performed this like. Now it’s clearer that you’re creating a new like, right?


### Testing specification

In each test, you have a brief description of what your application must do in order for the test to pass.


For this challenge we have the following tests:

- **`should be able to create a new repository`**: For this test to pass, your application must allow a repository to be created, and return a json with the created project.

- **`should be able to list the repositories`**: For this test to pass, your application must allow an array to be returned with all the repositories that have been created so far.

- **`should be able to update repository`**: For this test to pass, your application must allow only the `url`,` title` and `techs` fields to be changed.

- **`should not be able to update a repository that does not exist`**: For this test to pass, you must validate in your update route whether the repository id sent by the url exists or not. If not, return an error with status `400`.

- **`should not be able to update repository likes manually`**: For this test to pass, you must not allow your update route to directly change the likes of that repository, maintaining the same number of likes that the repository already had before the update. This is because the only place that should update this information is the route responsible for increasing the number of likes.

- **`should be able to delete the repository`**: For this test to pass, you must allow your delete route to delete a project, and when you delete it, it returns an empty response, with status `204`.

- **`should not be able to delete a repository that does not exist`**: For this test to pass, you must validate on your delete route whether the repository id sent by the url exists or not. If not, return an error with status `400`.

- **`should be able to give a like to the repository`**: For this test to pass, your application must allow a repository with the given id to receive likes. The value of likes must be increased by 1 with each request, and as a result, return a json containing the repository with the number of likes updated.


- **`should not be able to like a repository that does not exist`**: For this test to pass, you must validate on your like route whether the repository id sent by the url exists or not. If not, return an error with status `400`.


## :memo: License

This project is under the MIT license.
Made based on the rocketseat course, Bootcamp GoStack.[rocketseat]


---

Done with💜 by EIDM 

[rocketseat]: https://rocketseat.com.br
