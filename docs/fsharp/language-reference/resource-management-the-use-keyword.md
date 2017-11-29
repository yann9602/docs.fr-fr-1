---
title: "Gestion des ressources : mot clé « use » (F#)"
description: "Découvrez le F # mot-clé 'use' et la fonction « à l’aide », qui peut contrôler l’initialisation et la libération des ressources."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 00c3040e-859f-4dad-a7b5-7b8d44dc232c
ms.openlocfilehash: d4e8626f07f1c77e52e8fabd5ccc07dbf1fa8ddd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="resource-management-the-use-keyword"></a>Gestion des ressources : mot clé « use »

Cette rubrique décrit le mot clé `use` et `using` (fonction), qui peut contrôler l’initialisation et la libération de ressources.

## <a name="resources"></a>Ressources
Le terme *ressource* est utilisé dans plusieurs façons. Oui, les ressources peuvent être des données qu’une application utilise, tels que des chaînes, des graphiques et autres, mais dans ce contexte, *ressources* fait référence aux ressources de système d’exploitation ou des logiciels, tels que les contextes de périphérique de graphiques, des descripteurs de fichiers, réseau base de données et les connexions, les objets d’accès concurrentiel tels que les handles d’attente et ainsi de suite. L’utilisation de ces ressources par les applications implique l’acquisition de la ressource à partir du système d’exploitation ou d’autre fournisseur de ressources, suivie de la libération de la ressource pour le pool afin qu’il peut être fourni à une autre application. Des problèmes se produisent lorsque les applications ne libèrent pas de ressources vers le pool commun.

## <a name="managing-resources"></a>Gestion des ressources
Pour gérer efficacement et de façon responsable les ressources dans une application, vous devez libérer les ressources rapidement et de manière prévisible. Le .NET Framework vous permet de faire cela en fournissant le `System.IDisposable` interface. Un type qui implémente `System.IDisposable` a le `System.IDisposable.Dispose` (méthode), ce qui libère les ressources correctement. Applications bien écrites garantissent que `System.IDisposable.Dispose` est appelé rapidement lorsqu’un objet qui contient une ressource limitée n’est plus nécessaire. Heureusement, la plupart des langages .NET fournissent la prise en charge pour ce faire, et F # ne fait pas exception. Il existe deux constructions de langage utiles qui prennent en charge le modèle de suppression : le `use` liaison et la `using` (fonction).

## <a name="use-binding"></a>Utilisez la liaison
Le `use` (mot clé) a un écran semblable à celle de la `let` liaison :

Utilisez *valeur* = *expression*

Il fournit les mêmes fonctionnalités qu’un `let` de liaison, mais ajoute un appel à `Dispose` sur la valeur lorsque la valeur est hors de portée. Notez que le compilateur insère un contrôle de valeur null sur la valeur, afin que si la valeur est `null`, l’appel à `Dispose` n’est pas tentée.

L’exemple suivant montre comment fermer automatiquement un fichier à l’aide de la `use` (mot clé).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
Vous pouvez utiliser `use` dans les expressions de calcul, auquel cas une version personnalisée de la `use` expression est utilisée. Pour plus d’informations, consultez [séquences](sequences.md), [Workflows asynchrones](asynchronous-workflows.md), et [Expressions de calcul](computation-expressions.md).


## <a name="using-function"></a>à l’aide de la fonction
Le `using` fonction a la forme suivante :

`using`(*expression1*) *fonction ou expression lambda*

Dans un `using` expression, *expression1* crée l’objet doit être supprimé. Le résultat de *expression1* (l’objet qui doit être supprimé) devienne un argument, *valeur*à *fonction ou lambda*, qui est soit une fonction qui attend un seul argument d’un type qui correspond à la valeur restant produits par *expression1*, ou une expression lambda qui attend un argument de ce type. À la fin de l’exécution de la fonction, le runtime appelle `Dispose` et libère les ressources (sauf si la valeur est `null`, auquel cas l’appel à Dispose n’est pas tentée).

L’exemple suivant illustre la `using` expression avec une expression lambda.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

L’exemple suivant montre la `using` expression avec une fonction.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Notez que la fonction peut être une fonction qui a des arguments déjà appliqués. L’exemple de code suivant illustre cela. Il crée un fichier qui contient la chaîne `XYZ`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

Le `using` (fonction) et le `use` liaison sont de façon presque équivalente pour accomplir la même chose. Le `using` (mot clé) permet de contrôler quand `Dispose` est appelée. Lorsque vous utilisez `using`, `Dispose` est appelée à la fin de la fonction ou une expression lambda ; lorsque vous utilisez la `use` (mot clé), `Dispose` est appelée à la fin du bloc de code contenant. En règle générale, vous préférez utiliser `use` au lieu du `using` (fonction).


## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)
