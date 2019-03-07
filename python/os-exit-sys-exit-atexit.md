## os._exit()과 sys.exit()과 atexit

```python
import sys, atexit
def foo():
  sys.exit(1234)
atexit.register(foo)
sys.exit(0)
```
이러면 0이 반환된다.

```python
import sys, atexit
def foo():
  os._exit(1234)  # changed here
atexit.register(foo)
sys.exit(0)
```
이러면 1234가 반환된다.
