# Stripe
Library for accessing Stripe API

## Installation
Add this line to your application's Gemfile:
    gem 'stripe-ruby'
Then execute:
    $ bundle
Or install it yourself as:
    $ gem install stripe-ruby
## Usage Examples
~~~
# Configure your api key
Stripe.api_key = YOUR_SECRET_KEY
# Example of direct CC charge in Ruby
Stripe::Charge.create(
      {
        "source"=> "TOKEN FROM STRIPE.JS or SDK",
        "receipt_email"=>"customer email address",
        "installments"=>"number of installments",
        "line_items" => 
        [
          {
            "name"=>"Test Item",
            "amount"=>"1000",
            "currency"=>"usd",
            "quantity"=>"1"
          }
        ]
      }
)
# Example of Subscription Management in a few lines. Supports recurring payment via Card or Bank Transfer. For Card payments, recommended to attach payment method to customer (Default Payment Source).
customer = Stripe::Customer.create({
      "email"=>"CUSTOMER EMAIL",
      "name"=>"CUSTOMER NAME"
})
subscription = Stripe::Subscription.create({
"plan" => "starter_plan", "customer" => customer.id
})
# Example of Plan Downgrade/Upgrade (Automatic proration calculation between plans, credits, etc)
subscription.update({ plan: "premium_plan" });
# Customer Payment History
customer.list_invoices
~~~

# PR Merge: 2025-11-25 16:57:46

# PR Merge: 2025-11-25 16:58:11
