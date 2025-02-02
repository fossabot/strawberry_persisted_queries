# 🍓Strawberry Persisted Queries

[![PyPI](https://img.shields.io/pypi/v/strawberry_persisted_queries?logo=pypi&logoColor=white&style=for-the-badge)](https://pypi.org/project/strawberry_persisted_queries/)
[![GitHub Sponsors](https://img.shields.io/github/sponsors/catgirlinspace?style=for-the-badge&logo=githubsponsors)](https://github.com/sponsors/catgirlinspace)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fcatgirlinspace%2Fstrawberry_persisted_queries.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fcatgirlinspace%2Fstrawberry_persisted_queries?ref=badge_shield)

Apollo-compatible persisted queries for Strawberry. 

## Usage

Add `PersistedQueriesExtension()` to your extensions.

```python
import strawberry
from strawberry_persisted_queries import PersistedQueriesExtension

schema = strawberry.Schema(
    query=Query,
    extensions=[
        PersistedQueriesExtension(),
    ],
)
```

### Django

For Django users, a Django cache backend is available. This uses the default cache set in Django. 
```python
from strawberry_persisted_queries.django_cache import DjangoPersistedQueryCache

PersistedQueriesExtension(cache_backend=DjangoPersistedQueryCache())
```

### Safelisted Queries

`DictSafelist` can be used to require persisted queries to already be saved.
This can be used with a build tool to ensure only queries used by your app are available.

```python
from strawberry_persisted_queries.safelisting import DictSafelist

PersistedQueriesExtension(safelist=DictSafelist({
    'sha256Hash': 'query {...}',
}))
```


## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fcatgirlinspace%2Fstrawberry_persisted_queries.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fcatgirlinspace%2Fstrawberry_persisted_queries?ref=badge_large)