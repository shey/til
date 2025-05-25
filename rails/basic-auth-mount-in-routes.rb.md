## You can wrap a mounted Rack app with Basic Auth inline in

```ruby
  mount Rack::Auth::Basic.new(Yabeda::Prometheus::Exporter) { |u, p|
    ActiveSupport::SecurityUtils.secure_compare(u, ENV.fetch("METRICS_USER", "metrics")) &&
      ActiveSupport::SecurityUtils.secure_compare(p, ENV.fetch("METRICS_PASSWORD", "secret"))
  } => "/i/metrics"
```
