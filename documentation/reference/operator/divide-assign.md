---
layout: reference
title: `/=` (divide assign) operator
tab: documentation
unique_id: docspage
author: Tom Bentley
milestone: Milestone 1
---

# #{page.title}

The right associative, binary `/=` operator divides it's left-hand operand by 
the amount given by its right-hand operand. 

## Usage 

    variable Float num := 1.0;
    num /= 2.0; // half num 

## Description

### Side effects

In the process of performing a divide & assign the left-hand argument 
may be evaluated *more than once*, in contrast to how this operator is defined
in some other languages. This doesn't usually cause problems, but if evaluating
the left-hand operand has side-effects it could result in unexpected behaviour,
as an example consider:

    void m(Float[] seq, Natural index) {
        seq[index++] /= 2.0;
    }

The above code doesn't half the `index`<sup>th</sup> element of `seq`, as it 
may appear, it instead halves the `index`<sup>th</sup> element and 
assigns the result to the (`index+1`)<sup>th</sup> element.

### Definition

The `/=` operator is defined as follows

    lhs:=lhs.divided(rhs.castTo<N>())

See the [language specification](#{site.urls.spec}#arithmetic) for more details.

### Polymorphism

The `/=` operator is [polymorphic](/documentation/reference/operator/operator-polymorphism). 
The definition of the `/=` operator depends 
on the [`Numeric`](../../ceylon.language/Numeric) and 
[`Castable`](../../ceylon.language/Castable) and
[`Settable`](../../ceylon.language/Settable) interfaces.

### Widening

Widening will be implemented in <!-- m2 -->

The types of the operands need not match because of the call to `castTo<N>()` 
in the definition of the operator. In other words assuming it's possible to 
widen the `rhs` so that it's the same type as the `lhs` then 
such a widening will automatically be performed. It is a compile time error if 
such a widening is not possible.

## See also

* [arithmetic operators](#{site.urls.spec}#arithmetic) in the 
  language specification
* [operator precedence](#{site.urls.spec}#operatorprecedence) in the 
  language specification
* [Operator polymorphism](/documentation/tour/language-module/#operator_polymorphism) 
  and 
  [Numeric operator semantics](/documentation/tour/language-module/#numeric_operator_semantics) 
  in the Tour of Ceylon
