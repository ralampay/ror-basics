## Setup the `rspec` gem for Rails

1. In your `Gemfile`, include the following:

```ruby
group :development, :test do
  gem 'rspec-rails'
end
```

2. Install the gem

```bash
bundle install
```

3. Bootstrap `rspec`

```bash
rails generate rspec:install
```

## Writing a Request Spec

Use this to write specifications regarding user requests. The flow can be as follows:

```ruby
require 'rails_helper'

RSpec.describe 'Pages', type: :request do
  describe "GET /profile" do
    it "returns a successful response" do
      get("/profile")

      expect(response).to have_http_status(200)
      # expect(response.status).to eq(200)
    end
  end
end
```

To run the test we execute:

```bash
rspec spec
```
