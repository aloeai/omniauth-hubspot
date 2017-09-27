# OmniAuth Hubspot

Hubspot OAuth2 Strategy for OmniAuth.

Read the [Hubspot OAuth docs](https://developers.hubspot.com/docs/methods/oauth2/oauth2-overview) for more details:

## Installing

Add to your `Gemfile`:

```ruby
gem 'omniauth-hubspot', '~> 0.1.0', github: 'advocately/omniauth-hubspot'
```

Then `bundle install`.

## Usage

`OmniAuth::Strategies::Hubspot` is simply a Rack middleware. Read the OmniAuth docs for detailed instructions: https://github.com/intridea/omniauth.

Here's a quick example, adding the middleware to a Rails app in `config/initializers/omniauth.rb`:

```ruby
Rails.application.config.middleware.use OmniAuth::Builder do
  provider :hubspot, ENV['HUBSPOT_CLIENT_ID'], ENV['HUBSPOT_CLIENT_SECRET']
end
```

To start the authentication process with Hubspot you simply need to access `/auth/hubspot` route.

## Auth Hash

Here's an example *Auth Hash* available in `request.env['omniauth.auth']`:

```ruby
{"provider"=>"hubspot",
 "uid"=>nil,
 "info"=>
  {"uid"=>33333,
   "hub_id"=>1111,
   "app_id"=>2222,
   "token_type"=>"access",
   "scopes"=>["content", "oauth", "files"],
   "email"=>"michael@domain.com",
   "hub_domain"=>"domain.com"},
 "credentials"=>
  {"token"=>
    "dfkjadlfkjasdkjflaskdjfjsldflasjdflkasdjflaskdjf",
   "refresh_token"=>"lkfkjasldjkflaskjdflkasjdlfjkasdljfk",
   "expires_at"=>1489053154,
   "expires"=>true},
 "extra"=>
  {"user"=>
    {
     "user"=>"michael@domain.com",
     "hub_domain"=>"domain.com",
     "scopes"=>["content", "oauth", "files"],
     "hub_id"=>1111,
     "app_id"=>2222,
     "user_id"=>33333,
     "token_type"=>"access"}}}
```
