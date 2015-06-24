# particlerb
Ruby client for the [Particle.io] API

[Particle.io]: https://www.particle.io

*Note: this is not an official gem by Particle. It is maintained by Julien Vanier.*

## Quick start

Install via Rubygems

    gem install particlerb

... or add to your Gemfile

    gem "particlerb", "~> 0.0.1"


### Making requests

API methods are available as module methods (consuming module-level
configuration) or as client instance methods.

```ruby
# Provide authentication credentials
Particle.configure do |c|
  c.access_token = "38bb7b318cc6898c80317decb34525844bc9db55"
end

# Fetch the list of devices
Particle.devices
```
or

```ruby
# Provide authentication credentials
client = Particle::Client.new(access_token: "38bb7b318cc6898c80317decb34525844bc9db55")
# Fetch the list of devices
client.devices
```

## Device commands

List all devices (returns an `Array` of `Device`)
```
devices = Particle.devices
```

Get a `Device` by id or name
```
device = Particle.device('blue_fire')
```

Claim a device
```
Particle.device('blue_fire').claim
```




### Accessing HTTP responses

While most methods return a domain object like `Device`, sometimes you may
need access to the raw HTTP response headers. You can access the last HTTP
response with `Client#last_response`:

```ruby
device   = Particle.device('123456').claim
response = Particle.last_response
headers  = response.headers
```

## Thanks

This gem is heavily inspired by [Octokit][] by GitHub. I stand on the shoulder of giants. Thanks!

Octokit is copyright (c) 2009-2014 Wynn Netherland, Adam Stacoviak, Erik Michaels-Ober and licensed under the [MIT license][Octokit license].

[Octokit]: http://github.com/octokit/octokit.rb
[Octokit license]: https://github.com/octokit/octokit.rb/blob/master/LICENSE.md


## License

Copyright (c) 2015 Julien Vanier

This gem is available under the [GNU General Public License version 3][GPL-v3]

[GPL-v3]: https://github.com/monkbroc/particlerb/blob/master/LICENSE.txt