# Ruby On Rails

## Controller

```shell
bin/rails generate controller Articles index [--skip-routes]
```

## Model

```shell
bin/rails generate model Article title:string body:text
```
> Model names are singular, because an instantiated model represents a single data record.
> To help remember this convention, think of how you would call the model's constructor:
> we want to write `Article.new(...)`, `not Articles.new(...)`.
[source](https://guides.rubyonrails.org/getting_started.html#mvc-and-you-generating-a-model)

### Add record

```ruby
bin/rails console

entity = EntityClass.new(propertyOne: "value")
entity.save
entity
EntityClass.find(1)
EntityClass.all
```

### Show all records

```shell
EntityClass.all
```

### Seed database

```ruby
#db/seeds.rb

# frozen_string_literal: true

EntityClass.destroy_all

EntityClass.create!(
  [
    { name: 'Foo' },
    { name: 'Bar' }
  ]
)

puts "Created #{EntityClass.count} entities"
```
```shell
rails db:seed
```

## Migration

### N2N with `has_and_belongs_to_many`

> If you don't need to do anything with the relationship model,
> it may be simpler to set up a has_and_belongs_to_many relationship
> (though you'll need to remember to create the joining table in the database).
[source](https://guides.rubyonrails.org/association_basics.html#the-has-and-belongs-to-many-association)

#### Models

```ruby
# models
# /!\ Do no forget plural
class Foo < ApplicationRecord
  has_and_belongs_to_many :bars
end

class Bar < ApplicationRecord
  has_and_belongs_to_many :foos
end
```

#### Migration's script

```ruby
class SweetNameForMigration < ActiveRecord::Migration[7.0]
  def change
    # if needed
    create_table :foo do |t|
      # declare columns
    end

    # if needed
    create_table :bar do |t|
      # declare columns
    end

    create_table :modelas_modelbs, id: false do |t|
      t.belongs_to :foo
      t.belongs_to :bar
    end
  end
end
```

#### How to insert a dependant data in console
```ruby
# Get entities for each associtation
foo = Foo.create({})
bar = Bar.create({})

bar.foos << foo
# or
foo.bars << bar
```

#### How display data of the association as nested data
```ruby
render json: foo, include: :bar
```

## Routes

```shell
bin/rails routes
```

## General

Show all commands
```shell
rails -T
```

Show all commands with a filter
```shell
rails -T test
```
