---
title: Introduction to Rails
nav_order: 7
---

<!--prettier-ignore-start-->
# Intro to Rails - Building a Blog 
{: .no_toc }

placeholder.

## Table of Contents
{: .no_toc .text-delta }  

1. TOC
{:toc}

<!--prettier-ignore-end-->

## Introduction

In this Rails tutorial we will create a simple blogging application. This application will allow the users to:

- Post new blog entries (title, body, timestamp).
- Edit or delete existing blog entries.
- View all blog entries in reverse-chronological order.
- On post, the system will ensure the user has provided a title.

## Objectives

Upon completion of this tutorial, you should be able to:

- Create a new Rails project from the command line.
- Start and stop the testing web-server.
- Generate a scaffold for a particular MVC bundle.
- Prepare your project database using Rake.
- Edit and modify a view associated with a controller action.
- Add simple validation to a model.
- Interact with a model via the console.
- Explore the project logs.

\*MVC = Model View Controller

## Rails 6

This course module was originally created for Rails 2.3.x it was then updated for use with Rails 3, with future refactoring for Rails 4, 5 and 6.

If you notice anything that needs to be changed, please let me know.

_When all else fails reference the following two resources:_

- [Rails API](http://api.rubyonrails.org/)
- [Rails Guides](http://guides.rubyonrails.org/)

**It is highly recommend that you read through the [Getting Started with Rails](http://guides.rubyonrails.org/getting_started.html) guide.**

## Setup Instructions

To begin with run the windows command line program: `cmd.exe`

Let's create a new Rails project named 'blog':

- In the command window type: `rails new blog`

This command will generate a 'blog' folder along with a number of sub-folders and files. Your Rails application 'exists' within these folders and files.

Be sure to run this command from inside the folder where you wish to place your application folder.

## Starting the Server

Now we'll run the built-in test web-server:

- Open a second console window, navigate to your 'blog' folder and type:

`rails server`

- Load the default welcome screen for your application here:

[http://localhost:3000](http://localhost:3000)

The command you ran above tells Ruby to launch an HTTP Web Server through which you can test your Rails application. The name of the server you launched is Puma.

#### Resources

- [Puma Web Server](https://puma.io/)

## Scaffolding

Let's tell Rails to scaffold us up an MVC-bundle for a blog post:

- From the command line type: `rails generate scaffold Post title:string body:text`

Here we've specified that we wish to generate a scaffold named 'Post'. We have further specified that each post contains a 'title' (which is a string) and a 'body' (which is a text blob).

We'll see later on that by Rails will also add a 'created_at' and 'updated_at' property to each post.

The scaffold generator takes the name of the model (the resource) and optionally a list of field names and types.

Files generated as a result of the scaffolding:

- `\blog\app\controllers\posts_controller.rb`
- `\blog\app\views\posts\index.html.erb`
- `\blog\app\views\posts\show.html.erb`
- `\blog\app\views\posts\new.html.erb`
- `\blog\app\views\posts\edit.html.erb`
- `\blog\app\views\posts\_form.html.erb`
- `\blog\app\models\post.rb`
- `\blog\app\helpers\posts\_helper.rb`
- `\blog\db\migrate\001_create_posts.rb`

Amongst others...

## Database Creation & Migration

The default Rails database is SQLite. Let's create the database table where we will store our blog posts:

- From the command line type: `rails db:migrate`

This command creates a new 'posts' table in your database. This table will contain five columns:

- id (Auto-incrementing integer index)
- title (string)
- body (text blob)
- created_at (timestamp created automatically)
- updated_at (timestamp created automatically)

**Note:** Even though we created a scaffold for 'Post' (singular) the table created by Rake was named 'posts' (plural). This is a Rails standard. The controller and the views will also reference 'posts' (plural).

If you want to better understand the DB Migration you should investigate the following file from within your blog project folder:

`blog\db\migrate\001_create_posts.rb`

(In the place of 001 in the filename will actually be a long timestamp.)

This file was created when you ran the scaffolding command. It details (in Ruby) the database table associated with the scaffolded resource.

#### Resources

- [Rails DB Migrations](https://edgeguides.rubyonrails.org/active_record_migrations.html) (Rails Guides)
- [SQLite @ Wikipedia](http://en.wikipedia.org/wiki/SQLite)
- [SQLite.org](http://sqlite.org/)

## Testing the Scaffolding

We should now be able to load our posts controller:

[http://127.0.0.1:3000/posts](http://127.0.0.1:3000/posts)

We can even add a new post by click on the 'New post' link.

## MVC Bundles

When we created the `Post` scaffolding, Rails created a `posts` controller with a number of actions to allow for [CRUD](http://en.wikipedia.org/wiki/Create,_read,_update_and_delete) tasks within our `posts` table in the database.

For example, the `index` action fetches all posts from the model. This action is accessible via the following url:

`http://127.0.0.1:3000/posts/`

This index action has an associated view to display the posts:

`blog\app\views\posts\index.html.erb`

The controller uses the `Post` model to access the `posts` table in the database:

`blog\app\models\post.rb`

All controller methods represent actions that are accessible via a URL. Each action has an associated view. The scaffolding creates an `index`, `show`, `new`, `edit`, `create`, `update` and `destroy` action.

For example, the 'new post' action is found in the `new` method of the `posts` controller.

The `posts` controller can be found here:

`blog\app\controllers\posts_controller.rb`

Its `new` action is accessible via the following URL:

`http://127.0.0.1:3000/posts/new`

The associated view is located here:

`blog\app\views\posts\new.html.erb`

#### Resources

- [Rails Controllers Overview](http://guides.rubyonrails.org/action_controller_overview.html) (Rails Guides)

## Adding Validation

Let's add some simple validation to our blog posting.

- Open the `Post` model located here: `blog\app\models\post.rb`

The `Post` class defined in this file allows us to interact with our `posts` table in the database. It is currently empty, but it inherits the database functionality from the `ActiveRecord::Base` class (by way of the `ApplicationRecord` class).

- Add the following line inside the `Post` class:

`validates :title, presence: true`

Now, before a post can be added to the `posts` table Rails will ensure that the user has specified a title. Try adding [a new post](http://127.0.0.1:3000/posts/new) without a title.

#### Resources

- [Active Record Validations](http://guides.rubyonrails.org/active_record_validations.html) (Rails Guides)

## Creating the Blog View

Let's edit the `posts` controller's `index` view to make this look more like a real blog. Open the following file:

`blog\app\view\posts\index.html.erb`

Ruby code is embedded into this view within `<%` and `%>` tags. If we want to print a string from Ruby into the HTML we use `<%=` and `%>`.

The `@posts` variable was 'given' to our view by the `index` action of the `posts` controller. Notice that we are using a for-in loop to display all posts. The view will be more 'blog-like' if the posts are shown in reverse chronological order.

Replace the current `index` view with the following, and study this code until you can sing it blindfolded. Notice how the post `title` and `body` are accessed. What does the `link_to` method do?

```erb
<h1>Our Blag</h1>
<br />
<% @posts.each do |post| %>
  <h2> <%= post.title %> </h2>
  <p> <%= post.body %> </p>
  <p>
    Created at:
    <%= link_to post.created_at, post %>
    - <%= link_to 'Edit', edit_post_path(post) %>
    - <%= link_to 'Destroy', post, :confirm => 'Are you sure?', :method => :delete %>
  </p>
  <hr />
<% end %>
<br />
<%= link_to 'New post', new_post_path %>
```

To ensure that blog posts appear in reverse-chronological order, edit the `index` action of the `posts` controller. Modify the line where the `@posts` variable is created to look like this:

```ruby
@post = Post.order("created_at DESC")
```

#### Resources

- [Erb - Ruby Embedded in HTML](http://www.ruby-doc.org/stdlib/libdoc/erb/rdoc/classes/ERB.html)

## Layouts

You may have noticed that the views associated with controller actions are not complete HTML files. This is because each view is inserted inside an HTML layout shell before it is displayed. The layout for your application can be found here:

`\blog\app\views\layouts\application.html.erb`

The each view is inserted into a layout before the HTML is sent to the user's browser. The view is inserted where the layout reads:

```erb
<%= yield %>
```

The layout yields to a particular view; how very polite, proper and posh!

#### Resources

- [Rails Layout and Rendering](http://guides.rubyonrails.org/layouts_and_rendering.html) (Rails Guides)

## Script Console

The Rails script console allows us to interact with our project models.

- From a command prompt type: `rails console`

_(Ensure that you are in your project's root folder.)_

From the console try playing around:

```ruby
p = Post.all # Ask the Post model for all posts.
p[0].title
first = Post.first
new_post = Post.new title: 'Hello from Console', body: 'This is a test'
new_post.save # Save our new post to the database.
Post.all
```

A second way to add from the console:

```ruby
Post.create title: 'Another Console Post', body: 'Second console body text.'
```

## Exploring the Logs

Every time we interact with a controller action Rails generates a log message. These messages show any errors that may occur, along with all the SQL generated by our models when interacting with the database.

Since our server is running in the default development mode, the log file is located here:

`blog\log\development.log`

The logs will also be shown in the terminal window where you are running the rails server.

We can also inject custom messages into our logs from our controllers or models as follows:

```ruby
logger.warn "WARNING: This is a custom log message."
```

#### Resources

- [More on tweaking Rails configurations](http://guides.rubyonrails.org/configuring.html) (Rails Guides)
