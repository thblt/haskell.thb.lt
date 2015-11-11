---
title: Définition de fonctions
---
\label{defining-functions}

Une fonction se définit de la façon suivante:

\haskell
add :: a -> b  -- Signature de type, généralement optionnel.
add x = expr x
\eof

Une fonction infixe se définit en entourant son nom de parenthèses, comme pour l'utiliser en préfixe:

\haskell
(+*) a b = a + b + a * b
\eof

# Fonctions locales

On peut définir des fonctions dont la visibilité est limitée à une fonction. C'est utile pour définir des constantes, ou fournir des fonctions utilitaires qui n'ont pas besoin d'être disponibles au niveau du module. Haskell propose deux syntaxes: \hs{let}, qui place les variables locales *avant* le code de la fonction, et \hs{where},  qui les positionne *après*.

\begin{halfwidth}
\haskell
circLet :: Fractional a => a -> a
circLet radius = let pi   = 3.14
                     diam = 2 * radius
                 in pi * diam
\eof
\end{halfwidth}\hfill%
\begin{halfwidth}
	\haskell
circWhere :: Fractional a => a -> a
circWhere radius = pi * diam
    where pi   = 3.141592653589793
          diam = 2 * radius
	\eof
\end{halfwidth}

\begin{itemize}
\item Le choix de l'une ou de l'autre syntaxe est une question de lisibilité.
\item On peut les imbriquer: une fonction définie dans une clause \hs{let}/\hs{where} peut à son tour définir des fonctions locales, etc.
\item La visiblité des fonctions locales est limitée à la définition englobante.
\end{itemize}

# Fixité (précédence et associativité)
\label{defining-fixity}

L'associativité et la précédence sont collectivement nommées «fixité». La fixité d'une fonction infixe (et de n'importe quelle fonction préfixe dans sa forme infixe, comme \hs{`elem`}) est fixée par une déclaration \hs{infixl} (associatif à gauche), \hs{infixr} (associatif à droite) ou \hs{infix} (non-associatif
), suivie de l'ordre de précédence compris entre 0 et 9 et du nom de la fonction:

\haskell
(+*) :: Num a => a -> a -> a
infixl 9 +*
(+*) a b = a + b + a * b
\eof

Il est possible de définir la fixité d'une fonction locale, directement dans la clause \hs{let} ou \hs{where} où elle est définie.