---
layout: reference
title: `/` (quotient) operator
tab: documentation
unique_id: docspage
author: Tom Bentley
milestone: Milestone 1
---

# #{page.title}

The left-associative, binary `/` operator is used to compute the *quotient* of 
two operands.

## Usage 

    Natural three = 6 / 2;

## Description

### Definition

The `/` operator it defined as follows:

    lhs.castTo<N>().divided(rhs.castTo<N>());

See the [language specification](#{site.urls.spec}#arithmetic) for more details.

### Polymorphism

The `*` operator is [polymorphic](/documentation/reference/operator/operator-polymorphism). 
The meaning of `*` depends on the 
[`Numeric`](../../ceylon.language/Numeric) and
[`Castable`](../../ceylon.language/Castable) interfaces.


### Meaning of product for built-in types

For the built-in numeric types ([`Natural`](../../ceylon.language/Natural), 
[`Integer`](../../ceylon.language/Integer),
[`Float`](../../ceylon.language/Float),
[`Whole`](../../ceylon.language/Whole) and
[`Decimal`](../../ceylon.language/Decimal)) 
`*` performs normal mathematical division, subject to the limitations
of the relevant type.

### Widening

The types of the operands need not match because of the calls to `cast<N>()` 
in the definition of the operator. In other words assuming it's possible to 
widen one of the `lhs` or `rhs` so that it's the same type as the other then 
such a widening will automatically be performed. It is a compile time error if 
such a widening is not possible.

## See also

* [`Numeric`](../../ceylon.language/Numeric)
* [`Castable`](../../ceylon.language/Castable)
* [arithmetic operators](#{site.urls.spec}#arithmetic) in the 
  language specification
* [operator precedence](#{site.urls.spec}#operatorprecedence) in the 
  language specification
* [Operator polymorphism](/documentation/tour/language-module/#operator_polymorphism) 
  and 
  [Numeric operator semantics](/documentation/tour/language-module/#numeric_operator_semantics) 
  in the Tour of Ceylon
