# Trap Door - Reverse Captcha for Rails 4

Unobtrusive Captcha for your Rails forms. Trap Door works by adding a hidden "honeypot" field to your forms that only a spam bot will fill out. A before filter checks for the presence of this field and banishes bots to a [spam trap](http://en.wikipedia.org/wiki/User:Mike_Rosoft/Spambot).

## Installation

```
gem 'trap_door', :git => 'git://github.com/joaofraga/trap_door.git'
```

## Using Trap Door

### In your view

```erb
<%= form_for(@post) do |form| %>
    <%= trap_door_field %>
    # the rest of your form...
<%- end %>
```

### In your controller

```ruby
class PostController < ApplicationController
  trap_door :only => :create

  # the rest of your controller...
```

## Configuration

By default Trap Door names the hidden_field `:affiliate_id`. Obviously this won't work for everyone so you can change the field name by creating an initializer in `config/initializers` and telling Trap Door the name it should use for the honeypot field:

```ruby
TrapDoor.honeypot_field_name = :go_away
```


Copyright (c) 2009 Mike Breen
Copyright (c) 2013 Philippe Vaucher
Copyright (c) 2014 João Fraga

Released under the MIT license