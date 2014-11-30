# Iron_ebooks (non-iron.io fork)

A simple and hackish ruby script for pseudorandomly posting to a _ebooks account tweets derived from a regular twitter account

## Setup

1. Signup for a Twitter account you want to use for ebooking things
2. Sign into dev.twitter.com with the same credentials
3. Create an application for your _ebooks account (generate the credentials)
4. Create a file named twitter_init.rb in this directory with the OAuth credentials and the source account you want to use for seeding the markov process
5. Run "bundle install"
6. Run "bundle exec ruby ebooks.rb" to produce a tweet.
7. You can schedule it now to run regularly using the scheduler. I'd suggest once every 53 minutes or so.

## Configuring

There are several parameters that control the behavior of the bot. You can override them by setting them in the twitter_init.rb file. 

```
$rand_limit = 10
```

The bot does not run on every invocation. It runs in a pseudorandom fashion whenever `rand($rand_limit) == 0`. You can override it to make it more or less frequent. To make it run every time, you can set it to 0. You can also bypass it on a single invocation by passing `-p '{"force": true}'`

```
$include_urls = false
```

By default, the bot ignores any tweets with URLs in them because those might just be headlines for articles and not text you've written. If you want to use them, you can set this parameter to true.

```
$markov_index = 2
```

The Markov index is a measure of associativity in the generated Markov chains. I'm not going to go into the theory, but 1 is generally more incoherent and 3 is more lucid. If you want to change this, though.
