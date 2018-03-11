# kit file system

file system meta protocol library, for managing directory trees as magical little file systems of their own.

# Examples 

```lisp

(include "kit/header")
(import-namespace kit)

(require! (lit File-system Directory File) "./index"
          'assert)
(var home (.load File-system "./") )
(var test-value "hello world")


(pipe (.set home  "./test.txt" test-value)
      (.then (aprint "test file set"))
      (.then (-> (.find home "test.txt")))
      (.then (aprint "file found, checking value"))
      (.then (#-> (get 'string)))
      (.then (=> (s)
                 (assert (= s test-value)
                         "file was not set with appropriate value"))))
```
