# DigitalOcean Function Addons

# How to use
1. Install from [PyPi](https://pypi.org/project/do_function_addons/)
2. Import `Event` and `Context` from `function_addons.request`
3. Change your DO Functions function signature to `(event: Event, context: Context)`

# Adding custom event keys
DigitalOcean functions adds any extra request body to Event. Simply extend the Event class with your custom attributes for typing support.

```python
from function_addons.request import Event, Context

class MyEvent(Event):
    data: object

def main(event: MyEvent, context: Context):
    data = event["data"] 
```

Make sure to either use `.get()` or `except KeyError` as this doesn't validate if the key is actually present.