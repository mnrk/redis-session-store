A simple Redis-based session store for Redis. But why, you ask,
when there's [redis-store](http://github.com/jodosha/redis-store/)?
redis-store is a one-fits-all solution, and I found it not to work
properly with Rails, mostly due to a problem that seemed to lie in
Rack's Abstract::ID class. I wanted something that worked, so I
blatantly stole the code from Rails' MemCacheStore and turned it
into a Redis version. No support for fancy stuff like distributed
storage across several Redis instances. Feel free to add what you
seem fit.

This library doesn't offer anything related to caching, and is
only suitable for Rails applications. For other frameworks or
drop-in support for caching, check out
[redis-store](http://github.com/jodosha/redis-store/)

Installation
============

    gem install rails3-redis-session-store

Configuration
=============

See lib/redis-session-store.rb for a list of valid options.
In your Rails app, throw in an initializer with the following contents
and the configuration above:

    YourApp::Application.config.session_store :redis_session_store,
                                              :db => 0,
                                              :expire_after => 10.minutes,
                                              :key_prefix => "your_app:session:"
