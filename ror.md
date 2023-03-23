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

```shell
bin/rails console

entity = EntityClass.new(propertyOne: "value")
entity.save
entity
EntityClass.find(1)
EntityClass.all
```

## Routes

```shell
bin/rails routes
```