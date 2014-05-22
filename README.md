# Gubbins

Gubbins is [Dispel Magic](http://www.d20srd.org/srd/spells/dispelMagic.htm) for
one-file MVC web apps in Ruby. Imagine Camping if Camping was boring.

Gubbins: Little, Boring, Works OK*.

\* Note: At this time, Gubbins does not work OK.

## Installation

Add this line to your application's Gemfile:

    gem 'gubbins'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install gubbins

## Example Gubbins app

```ruby
module Blog
  class App < Gubbins::Router
    route '/', to: IndexController
    route '/post/(\d+)', to: PostController
  end

  class Post < Gubbins::Model
    validates_presence_of :title
  end

  class IndexController < Gubbins::Controller
    def get
      @posts = Post.all
      render :index
    end
  end

  class PostController < Gubbins::Controller
    def get(post_id)
      @post = Post.find post_id
      render :post
    end
  end
end
```

## Contributing

1. Fork it ( https://github.com/cndreisbach/gubbins/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
