# Shoppe

Shoppe is an Rails-based e-commerce platform which allows you to easily introduce a
catalogue-based store into your Rails 4 applications. 

**This version of Shoppe is currently unmaintained.**

## Features

* An attractive & easy to use admin interface with integrated authentication
* Full product/catalogue management
* Stock control
* Tax management
* Flexible & customisable order flow
* Delivery/shipping control, management & weight-based calculation

## Getting Started

Shoppe provides the core framework for the store and you're responsible for creating
the storefront which your customers will use to purchase products. In addition to
creating the UI for the frontend, you are also responsible for integrating with whatever
payment gateway takes your fancy.

### Installing into a new Rails application

To get up and running with Shoppe in a new Rails application is simple. Just follow the
instructions below and you'll be up and running in minutes.

    rails new my_store
    cd my_store
    echo "gem 'shoppe'" >> Gemfile
    bundle
    rails generate shoppe:setup
    rails generate nifty:key_value_store:migration
    rake db:migrate shoppe:setup
    rails server

## Using a custom mailer

You may want to override the default Shoppe email templates. In order to do so:

1. Create a `config/initializers/shoppe.rb` file in your *Rails* project.
2. Add the following snipped of code to the file:

        Shoppe.setup do |config|
          config.mailer = "Your::Mailer::Class"
        end

3. Create an `app/mailers/my_project/mailer.rb` file containing a class like this:

    class Your::Mailer::Class < Shoppe::Mailer

    It is important your mailer class **extends** the *Shoppe::Mailer* class.
4. Place any of email templates you wish to override with the following names:
  - accepted.(html|text).erb
  - shipped.(html|text).erb
  - rejected.(html|text).erb
  - received.(html|text).erb
  - new_password.(html|text).erb

**Note**: the *Shoppe* gem no longer has two mailer classes (*UserMailer* and *OrderMailer*) but only one (namely *Shoppe::Mailer*)

## Contribution

I do not plan on maintaining this project. However, in case you wish to contribute with a pull request, feel free to request it.
I may try to look into it and merge it.

## License

Shoppe is licenced under the MIT license. Full details can be found in the MIT-LICENSE
file in the root of the repository.
