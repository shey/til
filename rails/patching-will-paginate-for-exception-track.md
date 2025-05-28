# Fixing undefined method 'per' and 'total_count' Errors When Using will_paginate with exception-track

```ruby
if defined?(WillPaginate)
  module WillPaginate
    module ActiveRecord
      module RelationMethods
        def per(value = nil)
          per_page(value)
        end

        def total_count
          count
        end
      end
    end

    module CollectionMethods
      alias_method :num_pages, :total_pages
    end
  end
end
```