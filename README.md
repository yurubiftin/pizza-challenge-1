# PizzaDelivery
For this assessment, you'll be working on an API for tracking pizzas restaurants.
The instructions below will walk you through the process of ideation and planning your app: deciding on your models and relationships, planning how the information will be laid out on the page, etc.
 You should work through all the planning steps before you start doing any coding.
We have three models: `restaurants`,   `pizzas`, and `restaurants_pizzas`.
we have three controllers as well
## Topics
- Models
- Associations
- Validations
- Routes, Controllers, and REST
## Instructions
To get started, run `bundle install` while inside of this directory.
Build out all of the methods listed in the deliverables. The methods are listed
           in a suggested order, but you can feel free to tackle the ones you think are
easiest. Be careful: some of the later methods rely on earlier ones.
**Remember!** This code challenge does not have tests. You cannot run `rspec`
and you cannot run `learn`. You'll need to create your own sample instances so
that you can try out your code on your own.
Make sure your associations and
methods work in the console before submitting.
We've provided you with a tool that you can use to test your code. To use it,
run `rake console` from the command line. This will start a `pry` session with
your classes defined. You can test out the methods that you write here.
You are
also encouraged to use the `seeds.rb` file to create sample data to test your
models and associations.
**Before you submit!** Save and run your code to verify that it works as you
expect.
If you have any methods that are not working yet, feel free to leave
comments describing your progress.
## What You Already Have
The starter code has migrations and models for the initial `restaurant` and `pizzas`
models, and seed data for some `restaurant_pizza` `restaurant`s and `pizzas`s. The schema currently
looks like this:
#### Restaurant Table
| Column | Type   |
| ------ | ------ |
| name   | String |
#### Pizzas Table
| Column | Type    |
| ------ | ------- |
| name   | String  |
|ingredient| String |
#### restaurant_pizzas Table
| Column | Type    |
| ------ | ------- |
| pizza_id|integer |
| price  | Integer |
|restaurant_id|integer|
### Requirements
For this project, you must:
Create a Rails API backend.
Have at least three resources (three DB tables).
### Project Setup
Once you have the plan in place for the application you want to build take the following steps:
Create a new Rails project.
Create a new GitHub repository (NB: ENSURE IT IS PRIVATE).
Add your TM as a contributor to the project. (This is only for grading purposes. We promise, we won't steal your code)
Ensure you regularly commit to the repository.
Project Guidelines
Your project should conform to the following set of guidelines:
 ### Models
You need to create the following relationships:
- A `Restaurant` has many `Pizza`s through `RestaurantPizza`
- A `Pizza` has many `Restaurant`s through `RestaurantPizza`
- A `RestaurantPizza` belongs to a `Restaurant` and belongs to a `Pizza`
Start by creating the models and migrations for the following database tables:
domain-1.png
Add any code needed in the model files to establish the relationships. Then, run the migrations.
 You are welcome to generate your own seed data to test the application.
### Validations
Add validations to the `RestaurantPizza` model:
- must have a `price` between 1 and 30
### Routes
Set up the following routes. Make sure to return JSON data in the format
specified along with the appropriate HTTP verb.
GET /restaurants
Return JSON data in the format below:
```
[
  {
    "id": 1,
    "name": "Sottocasa NYC",
    "address": "298 Atlantic Ave, Brooklyn, NY 11201"
  },
  {
    "id": 2,
    "name": "PizzArte",
    "address": "69 W 55th St, New York, NY 10019"
  }
]
```
GET /restaurants/:id
If the `Restaurant` exists, return JSON data in the format below:
```
{
  "id": 1,
  "name": "Sottocasa NYC",
  "address": "298 Atlantic Ave, Brooklyn, NY 11201",
  "pizzas": [
    {
      "id": 1,
      "name": "Cheese",
      "ingredients": "Dough, Tomato Sauce, Cheese"
    },
    {
      "id": 2,
      "name": "Pepperoni",
      "ingredients": "Dough, Tomato Sauce, Cheese, Pepperoni"
    }
  ]
}
```
If the `Restaurant` does not exist, return the following JSON data, along with
the appropriate HTTP status code:
```
{
  "error": "Restaurant not found"
}
```
DELETE /restaurants/:id
If the `Restaurant` exists, it should be removed from the database, along with
any `RestaurantPizza`s that are associated with it (a `RestaurantPizza` belongs
to a `Restaurant`, so you need to delete the `RestaurantPizza`s before the
`Restaurant` can be deleted).
After deleting the `Restaurant`, return an _empty_ response body, along with the
appropriate HTTP status code.
If the `Restaurant` does not exist, return the following JSON data, along with
the appropriate HTTP status code:
```
{
  "error": "Restaurant not found"
}
```
GET /pizzas
Return JSON data in the format below:
```
[
  {
    "id": 1,
    "name": "Cheese",
    "ingredients": "Dough, Tomato Sauce, Cheese"
  },
  {
    "id": 2,
    "name": "Pepperoni",
    "ingredients": "Dough, Tomato Sauce, Cheese, Pepperoni"
  }
]
```
POST /restaurant_pizzas
This route should create a new `RestaurantPizza` that is associated with an
existing `Pizza` and `Restaurant`. It should accept an object with the following
properties in the body of the request:
```
{
  "price": 5,
  "pizza_id": 1,
  "restaurant_id": 3
}
```
If the `RestaurantPizza` is created successfully, send back a response with the data
related to the `Pizza`:
```
{
  "id": 1,
  "name": "Cheese",
  "ingredients": "Dough, Tomato Sauce, Cheese"
}
```
If the `RestaurantPizza` is **not** created successfully, return the following
JSON data, along with the appropriate HTTP status code:
```
{
  "errors": ["validation errors"]
}
```
## LICENSE
This repository is distributed under the ISC License
## Author
This repository is maintained by:
- [Yurub Ahmed]
