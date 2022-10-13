Tester for [ASYNC-248](https://clojure.atlassian.net/browse/ASYNC-248).

## Before patch

Time loading the ns from source:

```
% clj -A:pre
Clojure 1.11.1
user=> (time (use 'foo))
"Elapsed time: 3363.642768 msecs"
```

Compile:

```
% rm -rf classes
% mkdir classes
% clj -A:pre
Clojure 1.11.1
user=> (compile 'foo)
foo
```

Time loading the ns from aot:

```
% clj -A:pre:aot
Clojure 1.11.1
user=> (time (use 'foo))
"Elapsed time: 646.012997 msecs"
```

## After patch

To set up for this, check out core.async, apply patch in ASYNC-248, refer to it in :post dep in deps.edn.

Time loading the ns from source:

```
% clj -A:post
Clojure 1.11.1
user=> (time (use 'foo))
"Elapsed time: 2978.468039 msecs"
```

Compile:

```
% rm -rf classes
% mkdir classes
% clj -A:post
Clojure 1.11.1
user=> (compile 'foo)
foo
```

Time loading the ns from aot:

```
% clj -A:post:aot
Clojure 1.11.1
user=> (time (use 'foo))
"Elapsed time: 121.879343 msecs"
```
