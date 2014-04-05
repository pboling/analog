# analog

A Ruby helper for scaling numbers.

#### Background

Provides a quick way to scale a number from one range or set to another.

A simple example is:

You want to plot a point on a 500px graph using a data that lies in the 0..1 range.

```ruby
Scale.transform(0.5).from(0..1).to(0..500)
=> 250
```

This is generally useful for converting data from raw values to a range used for display or other kinds of output.

I use it all the time in music programming, converting OSC messages to musical notes and things like that and figure it might be useful to others.

#### Usage

```ruby
require "scale"
```

This example will scale a number down by 1/10th

```ruby
Scale.transform(22).from(0..150).to(0..15)
=> 2

```

Output a float by using a float in the destination range


```ruby
Scale.transform(22).from(0..150).to(0..15.0)
=> 2.2

```

You can use Arrays and Sets
```ruby
Scale.transform(0.40).from(0..1).to([0, 2, 4, 8, 12, 16, 32, 64, 128, 512])
=> 8

Scale.transform(8).from(Set.new([0, 2, 4, 8, 16, 64])).to(0..10)
=> 6
```

See the [examples](https://github.com/arirusso/analog/tree/master/examples) for more

###### Core Extension

There is a Numeric extension that you can optionally include.

```ruby
require "scale/core_ext"

0.40.scaled_from(0..1).to([0, 2, 4, 8, 12, 16, 32, 64, 128, 512])
=> 8
```

See the [core_ext example](https://github.com/arirusso/analog/blob/master/examples/core_ext.rb) for more examples.

#### Installation

    gem install analog
    
or with Bundler

    gem "analog"

#### License

Licensed under Apache 2.0, See the file LICENSE
Copyright (c) 2014 [Ari Russo](http://arirusso.com) 

