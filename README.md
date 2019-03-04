# waru
Distributed map reduce using web assembly

# Node API
/GET/info
* returns json info about this waru node

/POST/kernel
* takes in bytes of a web assembly module as bytes of body to used as map reduce processor

/POST/mapreduce/<function>
* takes in data to map reduce as a json array in body
* returns a json array of results

# Running as a node

```
waru
```

# Running as a router

```
waru router a.mynode.com b.mynode.com c.mynode.com
```

# Writing a processor 

```rust
extern "C" {
    fn console_log(start: i32);
}

fn cstr(s:&str) -> i32{
    std::ffi::CString::new(s).unwrap().into_raw() as i32
}

#[no_mangle]
pub fn malloc(size) -> i32 {
    0
}

#[no_mangle]
pub fn count_bytes(p_data) -> i32 {
    unsafe {
        console_log(cstr("processing starting!"));
        ... do something with data ...
        ... return pointer to output data structure
    }
}
```
