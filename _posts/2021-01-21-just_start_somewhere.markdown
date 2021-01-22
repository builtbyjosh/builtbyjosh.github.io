---
layout: post
title:      "Just Start Somewhere"
date:       2021-01-22 03:34:38 +0000
permalink:  just_start_somewhere
---


For the rails application assignment, I decided to create a very simple online store. It was a basic game sales clone of game stop. While it is much simpler than what it started out to be, I had hoped to make it bigger than it was. I had originally ran into trouble by trying to focus on too many of the problems at once. I couldn't get anything to work together, because it didn’t work on its own. I endend up starting over on my app and making sure to keep a smaller focus on what needed to be done.

With my app, I restarted by making a Cart, Game, and Line Item model and controller. This was basically the heart of my application. The Line Item model acted as a join table for the game and cart. From there I created my belongs to and has many associations. With the line item table, I was able to create the required “has many through” relationship between the cart model and game model.

With each of these models, I created the basic crud views and routes. This was mostly to ensure that I could test out each route, make sure each association worked, and I was able to use each element. However, I did not need to have all of the created routes and views to make my app.

One way I was able to reduce the amount of views and routes was by creating the current_cart method. This created a new cart every time a user logged in or checked out. With this I only needed a cart show page. And I was able to make an add to cart button on each games show page. The form used, had a hidden field for the game_id attached as well as the cart_id attached for the addition. 

`<% if logged_in? %>
    <%= form_for @line_item  do |f|%>
        <%= f.hidden_field :game_id, value: @game.id %>
        <%= f.number_field :quantity, value: 1, :min =>  1%>
        <%= f.submit "Add to Cart "%>
    <% end %>
<% end %>`

I also set the logged_in? method to check if there is a current_cart set. This allowed me to reduce the amount of logic programmed into several of the controllers. This is because, a logged in user has to have a cart. It is found or created when they signin or revisit the page.

The next hurdle I had to face was the checkout route. I didnt want to delete the cart because I wanted to keep a record of the game purchases. So I set the checkout route up so that it deleted the cart_id from the session hash. The way that the current_cart helper method worked:

` def current_cart
      if !session[:cart_id].nil?
        Cart.find(session[:cart_id])
      else
          @cart = Cart.new(user_id: session[:user_id])          
          @cart.save
          session[:cart_id] = @cart.id
      end
    end`
		
As soon as the cart_id was deleted, a new cart was created.  This allowed me to keep a record of completed carts without destroying any records.

But before all of the current_cart logic, I also created the User class. This was to help keep assign carts to people . I had also used a has_many association to line items with the user class. This helped me create the show page for the carts as well as the game library on the user show page. 

For pages I was able to delete, I didn't need any line item view pages. They were a join item and created when I added an item to the cart. So game id and cart id were automatically assigned. For the game views, I was able to skip the new, create, edit, and update views and routes. At least for a normal user. Since this was a basic online store, the user had no business doing any of those things with the games. So I only allowed the show and index page. But I did incorporate ActiveAdmin. This allowed me to sign into my app with admin privileges. From there I had the ability to add new games or edit existing games.  

The final hurdle I have had to deal with in my app was the third party signup/login. The main gem for doing this, omniauth, has recently been updated to 2.0. A major version change. So the majority of the tutorials and helpers online were not helpful. However, I did find a[ stack overflow response](http://https://stackoverflow.com/questions/65783394/no-route-matches-get-auth-google-oauth2-error-keeps-coming-up) that helped me finally push through my final hurdle.




		

