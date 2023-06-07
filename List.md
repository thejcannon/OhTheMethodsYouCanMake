# Links

https://docs.python.org/3/reference/datamodel.html

https://docs.python.org/3/library/unittest.mock.html

(Non-exhaustive, deepcopy missing) https://github.com/python/cpython/blob/d63a7c3694d5c4484fcaa01c33590b1d4bc2559e/Include/internal/pycore_global_strings.h#L72

Numeric Types:

- \_\_add\_\_ + \_\_radd\_\_ + \_\_iadd\_\_
- \_\_sub\_\_ + \_\_rsub\_\_ + \_\_isub\_\_
- \_\_mul\_\_ + \_\_rmul\_\_ + \_\_imul\_\_
- \_\_matmul\_\_ + \_\_rmatmul\_\_ + \_\_imatmul\_\_
- \_\_truediv\_\_ + \_\_rtruediv\_\_ + \_\_itruediv\_\_
- \_\_floordiv\_\_ + \_\_rfloordiv\_\_ + \_\_ifloordiv\_\_
- \_\_mod\_\_ + \_\_rmod\_\_ + \_\_imod\_\_
- \_\_divmod\_\_ + \_\_rdivmod\_\_ + (No idivmod)
- \_\_pow\_\_ + \_\_rpow\_\_ + \_\_ipow\_\_
- \_\_lshift\_\_ + \_\_rlshift\_\_ + \_\_ilshift\_\_
- \_\_rshift\_\_ + \_\_rrshift\_\_ + \_\_irshift\_\_
- \_\_and\_\_ + \_\_rand\_\_ + \_\_iand\_\_
- \_\_xor\_\_ + \_\_rxor\_\_ + \_\_ixor\_\_
- \_\_or\_\_ + \_\_ror\_\_ + \_\_ior\_\_

(and unary)

- \_\_neg\_\_
- \_\_pos\_\_
- \_\_abs\_\_
- \_\_invert\_\_

(To other types)

- \_\_complex\_\_
- \_\_int\_\_
- \_\_float\_\_
- \_\_index\_\_ (special)
- \_\_bool\_\_
- \_\_bytes\_\_
- \_\_str\_\_
- \_\_unicode\_\_
- \_\_fspath\_\_

(math funcs)

- \_\_round\_\_
- \_\_trunc\_\_
- \_\_floor\_\_
- \_\_ceil\_\_

Context Managers:

- \_\_enter\_\_ + \_\_aenter\_\_
- \_\_exit\_\_ + \_\_aexit\_\_

Pattern Matching:

- \_\_match_args\_\_

Iterators:

- \_\_next\_\_ + \_\_anext\_\_

Comparing:

- \_\_lt\_\_
- \_\_le\_\_
- \_\_eq\_\_
- \_\_ne\_\_
- \_\_gt\_\_
- \_\_ge\_\_

Strings:

- \_\_format\_\_
- \_\_repr\_\_

Attributes:

- \_\_delattr\_\_
- \_\_getattr\_\_
- \_\_getattribute\_\_
- \_\_setattr\_\_
- \_\_dir\_\_

Descritpors:

- \_\_delete\_\_
- \_\_set\_\_
- \_\_get\_\_
- \_\_set_name\_\_

Class Customization:

- \_\_init_subclass\_\_
- \_\_prepare\_\_
- \_\_subclasses\_\_
- \_\_mro_entries\_\_

Object Customization:

- \_\_new\_\_
- \_\_del\_\_
- \_\_init\_\_
- \_\_sizeof\_\_ (meh?)
- \_\_hash\_\_

Async:

- \_\_await\_\_

Instance Checks:

- \_\_instancecheck\_\_
- \_\_subclasscheck\_\_
- \_\_subclasshook\_\_ ( for ABCs)

Generics:

- \_\_class_getitem\_\_

Callables:

- \_\_call\_\_

Containers:

- \_\_len\_\_
- \_\_length_hint\_\_
- \_\_getitem\_\_
- \_\_setitem\_\_
- \_\_delitem\_\_
- \_\_missing\_\_
- \_\_iter\_\_ + \_\_aiter\_\_
- \_\_reversed\_\_
- \_\_contains\_\_

Copy/Pickle:

- \_\_newobj\_\_
- \_\_newobj_ex\_\_
- \_\_getinitargs\_\_
- \_\_copy\_\_
- \_\_deepcopy\_\_
- \_\_getnewargs_ex\_\_
- \_\_getnewargs\_\_
- \_\_getstate\_\_
- \_\_setstate\_\_
- \_\_reduce\_\_
- \_\_reduce_ex\_\_

Buffers:

- \_\_buffer\_\_ ( Py 3.12)
- \_\_release_buffer\_\_ ( Py 3.12)

TODO:

- \_\_isabstractmethod\_\_ (is a property/attribute)
