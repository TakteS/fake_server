# Fakex

[![Build Status](https://travis-ci.com/bernardolins/fakex.svg?token=nSxTcKtuZPdY1GgrbMLv&branch=master)](https://travis-ci.com/bernardolins/fakex)

```elixir
setup do
  Fakex.Action.create(:status_400, status_code: 400, body: ~s<"error": "bad request">)
  Fakex.Action.create(:status_200, status_code: 200, body: ~s<"user": {"name": "John", "age": 25}>)
  
  Fakex.Behavior.create(:my_server, [:400, :200])
  :ok
end

test "retry when 400" do
  assert User.get == %{name: "John", age: 25}
end
```

## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed as:

  1. Add fakex to your list of dependencies in `mix.exs`:

        def deps do
          [{:fakex, "~> 0.0.1"}]
        end

  2. Ensure fakex is started before your application:

        def application do
          [applications: [:fakex]]
        end

