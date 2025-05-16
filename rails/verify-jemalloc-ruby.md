## jemalloc


### To control how jemalloc handles freed memory
```bash
MALLOC_CONF="narenas:2,dirty_decay_ms:1000,muzzy_decay_ms:1000,background_thread:true"
```

### To Confirm MALLOC_CONF Was Applied

```bash
tr '\0' '\n' < /proc/$(pgrep -f sidekiq)/environ | grep MALLOC_CONF
```

### Check Which Libraries Ruby is Linked Against
```bash
ruby -r rbconfig -e "puts RbConfig::CONFIG['MAINLIBS']"
```

### Elsewhere
1. [malloc doubles ruby memory](https://www.speedshop.co/2017/12/04/malloc-doubles-ruby-memory.html)
