---
title: "Expressions C# - Visite guidée du langage C# | Microsoft Docs"
description: "Les expressions, opérandes et opérateurs sont des blocs de construction du langage C#"
keywords: ".NET, csharp, expression, opérateur, opérande"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 66eae1fcb7eca4572c49dca78bc31155464a6920
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---

<a id="expressions" class="xliff"></a>

# Expressions

Les *expressions* sont construites à partir de *d’opérandes* et *d’opérateurs*. Les opérateurs d’une expression indiquent les opérations à appliquer aux opérandes. Parmi les exemples d’opérateurs figurent `+`, `-`, `*`, `/` et `new`. Les littéraux, les champs, les variables locales et les expressions sont des exemples d’opérandes.

Quand une expression contient plusieurs opérateurs, la *priorité* des opérateurs contrôle l'ordre dans lequel les opérateurs individuels sont évalués. Par exemple, l’expression `x + y * z` est évaluée comme `x + (y * z)`, car l’opérateur `*` a une priorité plus élevée que `+`.

Lorsqu’un opérande se produit entre deux opérateurs de même priorité, *l’associativité* des opérateurs détermine l’ordre dans lequel les opérations sont effectuées :

*    À l’exception des opérateurs d’assignation, tous les opérateurs binaires sont *associatifs sur leur gauche*, ce qui signifie que les opérations sont effectuées de gauche à droite. Par exemple, `x + y + z` est évalué comme étant `(x + y) + z`.
*    Les opérateurs d’assignation et l’opérateur conditionnel (`?:`) sont *associatifs sur leur droite*, ce qui signifie que les opérations sont effectuées de droite à gauche. Par exemple, `x = y = z` est évalué comme étant `x = (y = z)`.

La priorité et l’associativité peuvent être contrôlées à l’aide de parenthèses. Par exemple, `x + y * z` multiplie d’abord `y` par `z`, puis ajoute le résultat à `x`, mais `(x + y) * z` ajoute d’abord `x` et `y`, puis multiplie le résultat par `z`.

La plupart des opérateurs peuvent être *surchargés*. La surcharge d’opérateur autorise la spécification d’implémentations d’opérateurs définies par l’utilisateur pour les opérations où l’un des deux opérandes ou les deux sont d’un type classe ou struct défini par l’utilisateur.

Voici un résumé des opérateurs de C# répertoriant les catégories d’opérateurs dans l’ordre de priorité, de la plus élevée à la plus basse. Les opérateurs de la même catégorie ont la même priorité. Sous chaque catégorie se trouve une liste d’expressions dans cette catégorie, ainsi que la description de ce type d’expression.

* Principale
    - `x.m` : Accès au membre
    - `x(...)` : Méthode et appel de délégué
    - `x[...]` : Tableau et accès d'indexeur
    - `x++` : Post-incrémentation
    - `x--` : Post-décrémentation
    - `new T(...)` : Création d'objet et de délégué
    - `new T(...){...}` : Création d'objet avec l'initialiseur
    - `new {...}` : Initialiseur d'objet anonyme
    - `new T[...]` : Création de tableau
    - `typeof(T)` : Permet d’obtenir l’objet @System.Type pour `T`
    - `checked(x)` : Évaluer l'expression dans le contexte vérifié (checked)
    - `unchecked(x)` : Évaluer l'expression dans le contexte non vérifié (unchecked)
    - `default(T)` : Obtenir la valeur par défaut de type `T`
    - `delegate {...}` : Fonction anonyme (méthode anonyme)
* Unaire
    - `+x` : Identité
    - `-x` : Négation
    - `!x` : Négation logique
    - `~x` : Négation d'opération de bits
    - `++x` : Pré-incrémentation
    - `--x` : Pré-décrémentation
    - `(T)x` : Convertir explicitement `x` en type `T`
    - `await x` : Attendre de façon asynchrone la fin de `x`
* Multiplication
    - `x * y` : Multiplication
    - `x / y` : Division
    - `x % y` : Reste
* Addition
    - `x + y` : Addition, concaténation de chaînes, combinaison de délégués
    - `x – y` : Soustraction, suppression de délégué
* Shift
    - `x << y` : Décalage à gauche
    - `x >> y` : Décalage à droite
* Relations et test de type
    - `x < y` : Inférieur à
    - `x > y` : Supérieur à
    - `x <= y` : Inférieur ou égal
    - `x >= y` : Supérieur ou égal
    - `x is T` : Renvoie `true` si `x` est un `T`, `false` dans le cas contraire
    - `x as T` : Renvoie `x` de type `T`, ou `null` si `x` n’est pas un `T`
* Égalité
    - `x == y` : Égal
    - `x != y` : Différent de
* AND logique
    - `x & y` : Opération de bits entière AND, Boolean logique AND
* XOR logique
    - `x ^ y` : Opération de bits entière XOR, Boolean logique XOR
* OR logique
    - `x | y` ; Opération de bits entière OR, Boolean logique OR
* AND conditionnel
    - `x && y` : Prend la valeur `y` uniquement si `x` n’est pas `false`
* OR conditionnel
    - `x || y` : Prend la valeur `y` uniquement si `x` n’est pas `true`
* Fusion de Null
    - `x ?? y`: Prend la valeur `y` si `x` est null, `x` dans le cas contraire
* Conditionnel
    - `x ? y : z` : Évalue `y` so `x` est `true`, `z` si `x` est `false`
* Attribution ou fonction anonyme
    - `x = y` : Attribution
    - `x op= y` : Assignation composée ; les opérateurs pris en charge sont
        - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
    - `(T x) => y` : Fonction anonyme (expression lambda)

>[!div class="step-by-step"]
[Précédent](types-and-variables.md)
[Suivant](statements.md)

