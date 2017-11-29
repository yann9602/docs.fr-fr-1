---
title: Gestion des exceptions (F#)
description: "Découvrez les principes fondamentaux de la gestion des exceptions dans F # et des liens vers des expressions et des fonctions de gestion des exceptions."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
ms.openlocfilehash: b61af66e0a70fdf9b86df37418c0284957d1f99e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling"></a>Gestion des exceptions

Cette section contient des informations sur la prise en charge de la gestion des exceptions en langage F#.


## <a name="exception-handling-basics"></a>Concepts de base de la gestion des exceptions
La gestion des exceptions constitue le moyen standard de gérer les conditions d’erreur dans le .NET Framework. Par conséquent, tout langage .NET doit prendre en charge ce mécanisme, notamment F#. Une *exception* est un objet qui encapsule des informations sur une erreur. Quand des erreurs se produisent, des exceptions sont déclenchées et l’exécution normale s’arrête. Le runtime recherche alors un gestionnaire approprié pour l’exception. La recherche démarre dans la fonction active et remonte dans la pile en passant par les couches d’appelants jusqu’à ce qu’un gestionnaire correspondant soit trouvé. Le gestionnaire est ensuite exécuté.

De plus, à mesure que la pile est déroulée, le runtime exécute le code présent dans les blocs `finally` pour garantir que les objets sont nettoyés correctement pendant le processus de déroulement.


## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----|-----------|
|[Types d'exceptions](exception-types.md)|Décrit comment déclarer un type d’exception.|
|[Exceptions : expression `try...with`](the-try-with-expression.md)|Décrit la construction de langage qui prend en charge la gestion des exceptions.|
|[Exceptions : expression `try...finally`](the-try-finally-expression.md)|Décrit la construction de langage qui vous permet d’exécuter du code de nettoyage à mesure que la pile se déroule quand une exception est levée.|
|[Exceptions : fonction `raise`](the-raise-Function.md)|Décrit comment lever un objet exception.|
|[Exceptions : fonction `failwith`](the-failwith-function.md)|Décrit comment générer une exception F# générale.|
|[Exceptions : fonction `invalidArg`](the-invalidArg-function.md)|Décrit comment générer une exception d’argument non valide.|
