---
layout: post
title: How to make sure to use request.user in django serializers
tags: python django
---

Often we want to make sure that a serializer will use the current
logged user in a field.

Still the serializer should be able to work with a different follower
. For example when it is used programmaticaly or outside the scope of
a request.

The solution to do that is to override the call to serializer.save()
in the view to include the request user.

```python
class ArticleCreateView(generics.CreateAPIView):
    """Endpoint to create a charge."""

    serializer_class = serializers.ArticleSerializer

    def perform_create(self, serializer):
        """Add userto the serializer."""
        serializer.save(user=self.request.user)
```

perform_create is defined in
[mixins.py](https://github.com/encode/django-rest-framework/blob/2b6245db5359571f10d27ace16473d70e160dce2/rest_framework/mixins.py#L25)


In the serializer kwargs argument are added to the validated data in
the save() method see
[serializers.py](https://github.com/encode/django-rest-framework/blob/master/rest_framework/serializers.py#L203)

```python
def save(self, **kwargs):
    validated_data = dict(
        list(self.validated_data.items()) +
        list(kwargs.items())
    )

    if self.instance is not None:
        self.instance = self.update(self.instance, validated_data)
        assert self.instance is not None, (
            '`update()` did not return an object instance.'
        )
    else:
        self.instance = self.create(validated_data)
        assert self.instance is not None, (
            '`create()` did not return an object instance.'
        )

    return self.instance
```

So you should never override the `save()` method in custom serializers
but instead rely on `create()` and `update()`, wich will be called
with `validated_data` overrided by `save()`'s kwargs arguments.
