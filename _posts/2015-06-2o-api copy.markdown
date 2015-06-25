---
layout: post
title:  "API vs Gem!"
date:   2015-06-14 18:58:19
categories: api ruby gem
---
## API vs Gem

In Jeannie thoughts... An API is a collection of data, lots of data. Companies release their API (like Marvel and Twitter) to the public so that other people can use it to design products that are powered by its service. Which is awesome!

A Ruby Gem takes that data and makes sense of it to use in Ruby programs. Or from what I  gather, making methods to call on specific data that we want. People make Gems for APIs so you don't have to. A Ruby Gem can be built for lots of purposes, not just APIs. It's a nicely packaged file or set of files that you can load and use on your computer to help you build programs. 

``` ruby

{% highlight ruby %}

# Initializing a client of the Twitter Gem
client = Twitter::REST::Client.new do |config|
  config.consumer_key        = "#########################"
  config.consumer_secret     = "#########################"
  config.access_token        = "#########################"
  config.access_token_secret = "#########################"
end
 

# Using gem method to search for Miley Cyrus's last 3 tweets and upcase them.
# Appears as though she is shouting.

client.search("from:mileycyrus", result_type: "recent").take(3).collect do |tweet|
 puts "This is Miley Cyrus Shouting: #{tweet.text.upcase}"
end

{% endhighlight %}