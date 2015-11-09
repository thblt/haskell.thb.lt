---
title:  Classes de type
---
\label{typeclasses}

Les classes de type ne sont pas des classes au sens que ce terme possède en POO.
Elles sont plus proches de ce qu'on nomme des interfaces : elles décrivent des fonctions pour lesquelles un type qui appartient à la classe fournit une implémentation.

# Dérivation automatique

Les types crées avec \hsKw{data} et \hsKw{newtype} peuvent dériver automatiquement certains \qsee{classes de type}{typeclasses}.

## Avec \hsKw{data}

# Dérivation manuelle

\haskell
class EvalToBool a where
    toBool :: a -> Bool

instance EvalToBool Integer where
    toBool x = x /= 0
\eof