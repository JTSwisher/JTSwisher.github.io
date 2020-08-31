---
layout: post
title:      "Cocktail Recipe App… a Rails Application"
date:       2020-08-31 18:01:52 +0000
permalink:  cocktail_recipe_app_a_rails_application
---


[Medium Article ](https://medium.com/@jefftswisher/cocktail-book-a-rails-app-9ee17bb483a2)

Up until now my time at Flatiron Schools software engineering program has been focused around the ruby programming language. We have worked through the procedural operations of the language and covered the object orientated aspect as well for our foundation. After having our solid foundation we delved into Ruby frame works and learned how to use them to build a well rounded web application.

Our first framework we utilized was Sinatra which is more lightweight, less feature rich and not as abstract as rails. Learning Sinatra was a huge stepping stone in bringing everything thus far full circle and providing a deeper understanding of all the aspects of a full fledged web application. This was very exciting and I could not wait to dive into rails to see its benefits and additional features.

For my Rails project I decided to create a recipe app specific to cocktails named, “Cocktail Book.” The basic functionality needed to allow users to create an account, create a cocktail recipe, favorite and save to their account a pre-existing cocktail recipe, as well as provide a rating and any additional comments to a favorite cocktail they save to their account.

One of the most difficult things throughout this process was handling the nested form for cocktails and the associated nested attributes each cocktail would have. To build a successful cocktail I needed to implement three tables and their associated models: cocktails, ingredients & cocktail_ingredients. The cocktails & ingredients table were standard while the cocktail_ingredients table was the join table for this resource.

The cocktail_ingredients join table would include the cocktail_id, ingredient_id and a quantity which was editable by the user. I could have easily included the quantity in the ingredients table and gotten away without utilizing the join table. However, without the join table my ingredients would not be reusable across different cocktails as each ingredient would then have a set quantity that may or may not be usable in the cocktail recipe being created by a user. Thus requiring ingredients to be duplicated in the db with their own unique quantities.

Throughout my application I used Bootstrap for styling. This being said I wanted to utilize Bootstrap’s form components to keep the styling uniform. I stumbled upon the gem: “bootstrap_form”, “~> 4.0.” This allowed me to continue to utilize the Rails Action View Form helper form_for with Bootstraps styling added.
Image for post
Image for post

In the above form you can see the nested “cocktail_ingredients” under “cocktail” and the nested “ingredients” under “cocktail_ingredients.” In the cocktails controller I had to instantiate placeholder “cocktail_ingredients” & “ingredient” objects to allow the user to associated multiple ingredients with their cocktail.
Image for post
Image for post

This renders 5 fields for both the “cocktail_ingredients” & “ingredient” attributes.
Image for post
Image for post

After the user submit the form I needed to whitelist the incoming params to make sure no foreign attributes were beign introduced. In the cocktails controller I created a strong_params method to ensure we are only getting the desired attributes passed through to the create action in the controller.
Image for post
Image for post
Strong params method.
Image for post
Image for post
Cocktail create action.

The create action above builds us 3 objects across all 3 models: Cocktail, Ingredient & CocktailIngredient, as well as creating the associations between all three objects thanks to the association declarations in the models themselves.

This experience was very beneficial and provided many great learning opportunities. Going forward I would like to add more functionality to the app to include leveraging Rails’s Active Storage component to allow cocktail images to be uploaded at the time of recipe while utilizing an Amazon S3 bucket to hold those images in the cloud.

Check out the repo here and happy building!
