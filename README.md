# Django Numerators
Django Numerators track autonumber style inner_id for model record
This repository contains a [Numerator](https://github.com/sasriawesome/django_numerators) model utils to create nice formatted Inner ID.

## Installation
```
$ pip install django-numerators
```
or
```
$ pip install git+https://github.com/sasriawesome/django_numerators.git#egg=django-numerators
```

## Usage

```
from django.db import models
from django_numerators.models import NumeratorMixin, NumeratorReset

class Product(NumeratorMixin):
    doc_prefix = 'PD'
    name = models.CharField(max_length=100)

```

## Usage with Polymorphic
install django-polymorphic
```
$ pip install django-polymorphic
```
### Using Parent Model doc_prefix
```
from django.db import models
from polymorphic.models import PolymorphicModel
from django_numerators.models import NumeratorMixin, NumeratorReset

class Product(NumeratorMixin):
    doc_prefix = 'PD'
    parent_prefix = True
    parent_model = 'Parent2'
    name = models.CharField(max_length=100)

class Inventory(Product):
    pass

class Asset(Product)
    pass
```
### Using Child Model doc prefix

```
class Product(NumeratorMixin):
    name = models.CharField(max_length=100)

class Inventory(Product):
    doc_prefix = 'INV'

class Asset(Product)
    doc_prefix = 'AST'
```
