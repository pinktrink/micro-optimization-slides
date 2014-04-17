# Micro-optimizations
* They add up
* HTML
    * Place common attributes first, in the same order
    * Alphabetize the rest
    * GZIP with compress consistent attributes better
* JSON
    * Nested objects vs flat arrays
        * Nested objects have more repeated character sequences, thus will be better compressed by GZIP
    * Property mapping for single-character properties
        * Keep it DRY, host property maps on the server
    * Bit-flagging vs boolean values
* JavaScript
    * Looping
        * While
            * Reverse-while
                * Older processors supported a JUMP_IF_NOT_ZERO equivalent instruction
                * Optimizers can now handle this
            * Do-while
        * For
            * For-in
                * Prototypical iteration
            * Cached for
                * `Array.length` is a **getter**, not simply a property
        * Avoid iterating multiple times
            * Lazy.js
        * Don't declare functions within loops
    * Property access
        * Cache multiple accesses
        * Don't over-cache
            * Cache scalar variables only for reading
    * Animation
        * Can it be done with CSS3?
    * Functions
        * Define functions before iteration
    * Loading
        * If it has no dependencies, make it async
        * It it doesn't require the DOM to exist, **do not** run it after the DOM content has loaded
* CSS
    * Animations
        * Transitions
            * Null-transform hack to offload processing to the GPU
        * Position vs translate
    * Selectors
        * Avoid too many selectors
        * Know the structure of you HTML, don't guess it
            * Use <tbody> and <thead> in tables
    * Media queries
        * Keep them in the same file to avoid too many HTTP requests
    * Why we haven't seen the parent selector
* Cookies
    * Use bye data and bit-flagging
    * Can you use local storage instead?
* Serving
    * Use multiple subdomains
        * Most browsers only handle 6 simultaneous requests from a single domain
        * A good medium is 3 or 4
    * Use a CDN
        * S3 is a good idea
    * Use HTTP errors, don’t just return 200 and include an error code
    * REST
        * Use REST methods
* Q/A
