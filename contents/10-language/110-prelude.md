---
title: Le Prélude
---
\label{prelude}

Le Prélude (\hsMod{Prelude}) est la librairie fondamentale d'Haskell. Contrairement aux autres modules, il est importé implicitement (cette importation peut néanmoins être contrôlée avec une \qsee{clause \hsKw{import}}{import} explicite).

L'implémentation de référence \parencite[\nopp I, 9]{Haskell2010} est écrite en Haskell.

Il est particulièrement intéressant de noter que parmi les définitions fournies par le Prélude, un certain nombre sont, dans la plupart des langages procéduraux, définies au niveau du compilateur. Parmi celles-ci, on trouve notamment les opérateurs booléens court-circuitants, dont l'implémentation est rendue triviale par le principe d'évaluation paresseuse:

\begin{itemize}
\item Les opérateurs booléens court-circuitants :
\end{itemize}

\haskellN
module Prelude (
    module PreludeList, module PreludeText, module PreludeIO,
    Bool(False, True),
    Maybe(Nothing, Just),
    Either(Left, Right),
    Ordering(LT, EQ, GT),
    Char, String, Int, Integer, Float, Double, Rational, IO,

--      These built-in types are defined in the Prelude, but
--      are denoted by built-in syntax, and cannot legally
--      appear in an export list.
--  List type: []((:), [])
--  Tuple types: (,)((,)), (,,)((,,)), etc.
--  Trivial type: ()(())
--  Functions: (->)

    Eq((==), (/=)),
    Ord(compare, (<), (<=), (>=), (>), max, min),
    Enum(succ, pred, toEnum, fromEnum, enumFrom, enumFromThen,
         enumFromTo, enumFromThenTo),
    Bounded(minBound, maxBound),
    Num((+), (-), (*), negate, abs, signum, fromInteger),
    Real(toRational),
    Integral(quot, rem, div, mod, quotRem, divMod, toInteger),
    Fractional((/), recip, fromRational),
    Floating(pi, exp, log, sqrt, (**), logBase, sin, cos, tan,
             asin, acos, atan, sinh, cosh, tanh, asinh, acosh, atanh),
    RealFrac(properFraction, truncate, round, ceiling, floor),
    RealFloat(floatRadix, floatDigits, floatRange, decodeFloat,
              encodeFloat, exponent, significand, scaleFloat, isNaN,
              isInfinite, isDenormalized, isIEEE, isNegativeZero, atan2),
    Monad((>>=), (>>), return, fail),
    Functor(fmap),
    mapM, mapM_, sequence, sequence_, (=<<),
    maybe, either,
    (&&), (||), not, otherwise,
    subtract, even, odd, gcd, lcm, (^), (^^),
    fromIntegral, realToFrac,
    fst, snd, curry, uncurry, id, const, (.), flip, ($), until,
    asTypeOf, error, undefined,
    seq, ($!)
  ) where
\eof
Noms exportés par le Prélude d'Haskell 2010 \parencite[\nopp I, 9]{Haskell2010}