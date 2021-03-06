---
navhome: /docs/
next: true
sort: 9
title: |* "bartar"
---

# `|* "bartar"` 

`[%brtr p=model q=hoon]`: form a gill, a wet one-armed 
core with sample.

## Expands to

```
=|  p
|%
+-  $
  q
--
```

## Syntax

Regular: *2-fixed*.

## Discussion

In a normal (dry) gate, your argument is converted into the
sample type.  In a generic (wet) gate or gill, your argument type
passes through the function, rather as if it was a macro (there
is still only one copy of the code, however).

Genericity is a powerful and dangerous tool.  Use gills only if
you think you know what you're doing. 

Just as with a [gate](../tis), we can recurse back into a gill 
with `$()`.

> `$()` expands to `%=($)` (["centis"](../../cen/tis)), accepting 
> a *jogging* body containing a list of changes to the subject.

## Examples

Wet and dry gates in a nutshell:

```
~zod:dojo> =foo |=([a=* b=*] [b a])
~zod:dojo> =bar |*([a=* b=*] [b a])
~zod:dojo> (foo %cat %dog)
[6.778.724 7.627.107]
~zod:dojo> (bar %cat %dog)
[%dog %cat]
```

The dry gate does not preserve the type of `a` and `b`; the wet
gate does.
