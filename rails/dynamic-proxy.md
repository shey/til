# TIL: Wrapping Hashes and the Dynamic Proxy Pattern

Wrap a plain hash in Ruby so it behaves like an object with real methods without needing to define all the accessors. Super useful for things like fast_jsonapi, which expects method calls, not hash keys.


```ruby
class SubjectDynamicProxy
  attr_reader :id

  def initialize(attrs, id)
    @id = id
    @attrs = attrs.stringify_keys
  end

  def method_missing(name, *args, &block)
    return @attrs[name.to_s] if @attrs.key?(name.to_s)
    super
  end

  def respond_to_missing?(name, include_private = false)
    @attrs.key?(name.to_s) || super
  end
end
```

# Also See:
- [Ruby, Proxy Pattern and Metaprogramming](https://gist.github.com/Madh93/9816c6408f3b06b4081f8bd5b242b253#ruby-proxy-pattern-and-metaprogramming)
