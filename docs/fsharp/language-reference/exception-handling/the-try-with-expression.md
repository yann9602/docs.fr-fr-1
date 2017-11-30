---
title: "Exceptions : expression try...with (F#)"
description: "Découvrez comment utiliser l’expression F # 'try... with' pour la gestion des exceptions."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 36721076-95cd-4636-ae43-79dd512bee6c
ms.openlocfilehash: 163dfab49d4aaf23123800246fae2cad33e2257c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-trywith-expression"></a>Exceptions : expression try...with

Cette rubrique décrit la `try...with` expression, l’expression qui est utilisée pour la gestion des exceptions dans le langage F #.


## <a name="syntax"></a>Syntaxe

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>Remarques
Le `try...with` expression est utilisée pour gérer les exceptions en F #. Il est similaire à la `try...catch` instruction en langage c#. Dans la syntaxe précédente, le code dans *expression1* peut générer une exception. Le `try...with` expression retourne une valeur. Si aucune exception n’est levée, l’expression entière retourne la valeur de *expression1*. Si une exception est levée, chaque *modèle* est ensuite comparé avec l’exception et pour le premier modèle correspondant, correspondant *expression*, appelé le *Gestionnaire d’exceptions*, pour cette branche est exécutée, et l’expression globale retourne la valeur de l’expression dans ce gestionnaire d’exceptions. Si aucun modèle ne correspond, l’exception se propage la pile des appels jusqu'à ce qu’un gestionnaire correspondant est trouvé. Les types des valeurs retournées de chaque expression dans les gestionnaires d’exceptions doivent correspondre au type retourné de l’expression dans le `try` bloc.

Souvent, le fait qu’une erreur s’est produite également signifie qu’il n’existe aucune valeur valide pouvant être renvoyées par les expressions dans chaque gestionnaire d’exceptions. Un modèle fréquent consiste à avoir le type de l’expression à être un type d’option. L’exemple de code suivant illustre ce modèle.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Les exceptions peuvent être des exceptions .NET, ou ils peuvent être des exceptions F #. Vous pouvez définir des exceptions F # à l’aide de la `exception` (mot clé).

Vous pouvez utiliser divers modèles de filtrer sur le type d’exception et d’autres conditions ; les options sont résumées dans le tableau suivant.


|Modèle|Description|
|-------|-----------|
|:? *type d’exception*|Correspond au type d’exception .NET spécifié.|
|:? *type d’exception* comme *identificateur*|Correspond au type d’exception .NET spécifié, mais donne une valeur nommée à l’exception.|
|*nom de l’exception*(*arguments*)|Correspond à un type d’exception F # et lie les arguments.|
|*identifier*|Correspond à n’importe quelle exception et lie le nom à l’objet exception. Équivalent à **: ? System.Exception comme***identificateur*|
|*identificateur* lorsque *condition*|Correspond à une exception si la condition est true.|

## <a name="examples"></a>Exemples
Les exemples de code suivants illustrent l’utilisation des divers modèles de gestionnaire d’exception.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]
    
>[!NOTE] 
Le `try...with` construction est une expression séparée de la `try...finally` expression. Par conséquent, si votre code requiert à la fois un `with` bloc et un `finally` bloc, vous devez imbriquer les deux expressions.

>[!NOTE] 
Vous pouvez utiliser `try...with` dans les workflows asynchrones et autres expressions de calcul, dans lequel cas une version personnalisée de la `try...with` expression est utilisée. Pour plus d’informations, consultez [Workflows asynchrones](../asynchronous-workflows.md), et [Expressions de calcul](../computation-expressions.md).


## <a name="see-also"></a>Voir aussi
[Gestion des exceptions](index.md)

[Types d'exceptions](exception-types.md)

[Exceptions : expression `try...finally`](the-try-finally-expression.md)
