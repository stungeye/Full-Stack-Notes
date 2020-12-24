---
title: View Helpers
parent: Rails Overview
nav_order: 6
---

<!--prettier-ignore-start-->
## View Helpers
{: .no_toc }

View helpers are method we can call in our ERB views to generate markup. In the previous section we looked at the [link_to helper](05-urls-are-routes.html#the-link_to-helper). 

There are many other helpful helpers.

### Table of Contents
{: .no_toc }  

1. TOC
{:toc}

<!--prettier-ignore-end-->

## Displaying Images

The image_tag helper builds an HTML `<img />` tag for the specified file. By default, files are loaded from the `app/assets/images` folder.

To display the `app/assets/images/fish.png` image:

```erb
<%= image_tag "fish.png" %>
```

We can also any of the `img` tag attributes using symbols:

```erb
<%= image_tag "fish.png", , :width ='20%' %>
```

This would generate:

```html
<img alt="Fish" src="/assets/fish.png" width="20%" />
```

For model objects that include an image URL string property, or an [ActiveStorage](https://edgeguides.rubyonrails.org/active_storage_overview.html) attached image, we use the helper like this:

```erb
<%= image_tag @product.image %>
```

Assuming that `@product` is an ActiveRecord model object.

## Rails View Partials

Partials are a device for breaking the view rendering process into more manageable chunks. With a partial, you can move the code for rendering a particular view to its own file. This allows us to keep our view code DRY.

Render the `_menu.html.erb` file found in the current folder:

```erb
<%= render 'menu' %>
```

This is a short-cut for:

```erb
<%= render partial: 'menu' %>
```

If the `_menu.html.erb` file isn't in the current folder, for example the `app/view/shared` folder:

```erb
<%= render 'shared/menu' %>
```

**NOTE:** Partial filenames must always begin with an underscore, but we don't use the underscores in the `render` arguments.

## Rendering Partials for Objects or Collections

Given a @product variable that contains a Product object render a `_product.html.erb` file found in the products view folder.

```erb
<%= render @product %>
```

Given a collection of Product objects in @products render the `views/products/_product.html.erb` once for each Product.

```erb
<%= render @products %>
```

These are shortened forms for the fully expanded calls to the render command. The first of these is equivalent to:

```erb
<%= render partial: 'product', object: @product %>
```

The second is equivalent to:

```erb
<%= render partial: 'product', collection: @products %>
```

#### Resources

Rails partials have a lot more to offer, including local variables. Be sure to read through:

- [View Partials](http://guides.rubyonrails.org/layouts_and_rendering.html#using-partials) from the Layouts and Rendering Rails Guide.

## Working With Model Forms

We can use the `form_with` helper to bind a form to a model object.

Imagine a controller where the `new` and `edit` actions load a `Post` object into a `@post` variable. In the view, we could build a form bound to the `Post` model object:

```erb
<%= form_with(model: @post, local:true) do |f| %>
  <div>
      <%= f.label :title %><br/>
      <%= f.text_field :title %>
  </div>
  <div>
    <%= f.label :body %><br/>
    <%= f.text_area :body %>
  </div>
  <div>
    <%= f.label :image %><br/>
    <%= f.text_field :image %>
  </div>
  <%= f.submit %>
<% end %>
```

The `f` block argument is a form builder. We use it to build the various components of our form.

For example, this code:

```erb
<%= f.label :image %>
<%= f.text_field :image %>
```

Would generate these html form tags, associated with the `Post` object's `image` property.

```erb
<label for="post_image">Image</label>
<input id="post_image" name="post[image]" size="30" type="text" value="" />
```

#### Resources

More information on dealing with generic forms, or model-centric forms read the [Form Helper Rails Guide](http://guides.rubyonrails.org/form_helpers.html#dealing-with-model-objects).

## Model Forms with Associations

Rails makes it easy to associate one model with another by way of a foreign key. In our CRM example the customer model had a `province_id` property. To link the two models:

in `app\models\customer.rb`:

```ruby
belongs_to :province
```

in `app\models\province.rb`:

```ruby
has_many :customers
```

Then within the customers `_form` partial:

```erb
<div class="field">
  <%= f.label :province_id %><br />
  <%= f.collection_select :province_id, @provinces, :id, :name %>
</div>
```

This view code assumes that the `@provinces` instance variable contains a collection of all the Province objects from the provinces table. This instance variable would have to be added to any controller actions using this `_form` partial.

It also assumes that Province objects have a `name` property containing the name of the province.

## Select Dropdowns with form_tag

The `f.collection_select` helper works nicely with `form_for`, but sometimes you want to build a select dropbox for use with a `form_tag`. For this we use a combination of `select_tag` and `options_for_select`.

```erb
<%= form_tag some_route_path do %>
   <%= select_tag :my_option, options_for_select(@some_array) %>
   <%= submit_tag "Search" %>
<% end %>
```

When this form is submitted the option selected by the user in the select dropdown will be found in `params[:my_option]`.

The `@some_array` variable should be an array of strings to use as options for the select dropdown.

If your options are coming from an ActiveRecord collection, you can use the `options_from_collection_for_select` helper. The added benefit of this helper is that the `value` attributes of each `option` tag can be made to contain the ActiveRecord `id` of the collection members.

So for example, if you had an `@categories` collection of `Category` objects where each category had a `name`:

```erb
<%= select_tag :category, options_from_collection_for_select(@categories, 'id', 'name') %>
```

On submission of the form the selected category id could be found in `params[:category]`.

#### Resources

- [Rails API: options_for_select](http://api.rubyonrails.org/classes/ActionView/Helpers/FormOptionsHelper.html#method-i-options_for_select)
- [Rails API: options_from_collection_for_select](http://api.rubyonrails.org/classes/ActionView/Helpers/FormOptionsHelper.html#method-i-options_from_collection_for_select)
- [Rails Guide: The Select and Option Tags](http://guides.rubyonrails.org/form_helpers.html#the-select-and-option-tags)
