---
title: François Delbrayelle - DevFest Lille 2019 - Doom, gloom or loom (notes)
---

# Doom, gloom or loom

Sujets : Threads, coroutines, JDK

13h00 - 14h00

Par [Rémi Forax](https://twitter.com/RemiForaxOff) (Université Paris Est Marne-la-Vallée). Merci !

La vidéo complète est en ligne sur la chaîne YouTube du [GDG France](https://www.youtube.com/watch?v=OYujKbItAXc).

Talk à propos du [projet Loom](http://openjdk.java.net/projects/loom) en développement pour les futures JDK et en particulier sur les __Fibers and Continuations__.

Threads :
- même espace mémoire
- si nombreux, cause de OutOfMemoryError
- scheduling géré par l'OS

Continuation :
- équivalant à une fonction
- suspension possible (nom temporaire de la méthode : `yield`)
- prend un ContinuationScope et un Runnable en entrée
- plusieurs points d'entrée
- gérée dans un Thread
- scheduling géré par la JVM (ou un framework)

__Le principe existe déjà en Kotlin avec les coroutines ou async/await de C# ou JS.__

Sans doute l'une des punchlines du jour :

> "Kotlin c'est la même chose que Java mais sans point-virgule !"

Fiber :
- ressemble beaucoup à un Thread
- englobe un Runnable/Callable
- se lance sur un Thread jusqu'à un appel bloquant
- Fiber délégue la suspension (`yield`) à la Continuation
- tous les appels bloquants font un `yield` en interne
- schedulé avec un ExecutorService
- prend une Continuation en entrée

Différences entres les Fibers (appelées aussi "Delimited Continuations") et les Threads :
- Pas de switch contexte au niveau de l'OS pour le scheduling explicite
- Pas besoin de réserver de la heap en avance => ne stocker que ce qui est nécessaire

Fibers et Continuations utilisés dans `Thread.sleep(...)` dans le projet Loom.

En résumé, Kotlin vs Loom :
- Kotlin a besoin d'un nouveau compilateur ; le bytecode gonfle mais rapide, monde à part
- Java Loom a besoin d'une JVM, pas gros mais pas rapide (pour l'instant), monde unifié

Question du public : ça sort quand ? Quand disponible sur une JDK future :)
