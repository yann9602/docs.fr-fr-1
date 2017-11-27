---
title: Attributs (F#)
description: "Découvrez comment les attributs F # pour activer les métadonnées à appliquer à une construction de programmation."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 95c001e6-3708-4d04-a850-d855f78eb51e
ms.openlocfilehash: 88098e51d19a86f501c35abe3408524378f147b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="attributes"></a>Attributs

Attributs activent les métadonnées à appliquer à une construction de programmation.

## <a name="syntax"></a>Syntaxe

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Remarques

Dans la syntaxe précédente, le *cible* est facultatif et, s’il est présent, spécifie le type d’entité de programme auquel l’attribut s’applique. Les valeurs valides pour *cible* sont affichés dans le tableau figurant plus loin dans ce document.

Le *-nom de l’attribut* fait référence au nom (éventuellement qualifié avec des espaces de noms) d’un type d’attribut valide, avec ou sans le suffixe `Attribute` qui est généralement utilisé dans les noms de type d’attribut. Par exemple, le type `ObsoleteAttribute` peut être abrégé `Obsolete` dans ce contexte.

Le *arguments* sont les arguments au constructeur pour le type d’attribut. Si un attribut possède un constructeur par défaut, la liste d’arguments et les parenthèses peuvent être omis. Attributs prennent en charge les arguments positionnels et les arguments nommés. *Arguments de position* sont des arguments qui sont utilisés dans l’ordre dans lequel elles apparaissent. Arguments nommés peuvent être utilisés si l’attribut a des propriétés publiques. Vous pouvez les définir à l’aide de la syntaxe suivante dans la liste d’arguments.

```
*property-name* = *property-value*
```

Ces initialisations de propriété peuvent être dans n’importe quel ordre, mais ils doivent suivre les arguments positionnels. Voici un exemple d’un attribut qui utilise des arguments de position et les initialisations de propriété.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

Dans cet exemple, l’attribut est `DllImportAttribute`, utilisé ici sous forme abrégée. Le premier argument est un paramètre positionnel et le second est une propriété.

Les attributs sont une construction de programmation .NET qui permet à un objet appelé un *attribut* à associer à un type ou un autre élément de programme. L’élément de programme auquel un attribut est appliqué est appelé le *cible de l’attribut*. L’attribut contient généralement des métadonnées sur sa cible. Dans ce contexte, les métadonnées peuvent être des données sur le type autres que les champs et leurs membres.

Attributs en F # peuvent être appliqués aux constructions de programmation suivantes : fonctions, méthodes, assemblys, modules, types (classes, enregistrements, structures, interfaces, délégués, énumérations, unions et ainsi de suite), constructeurs, propriétés, champs, paramètres, paramètres de type et les valeurs de retour. Les attributs ne sont pas autorisées sur `let` liaisons à l’intérieur des classes, des expressions ou des expressions de flux de travail.

En règle générale, la déclaration d’attribut apparaît directement avant la déclaration de l’attribut cible. Plusieurs déclarations d’attributs peuvent être utilisées ensemble, comme suit.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

Vous pouvez interroger les attributs au moment de l’exécution en utilisant la réflexion .NET.

Vous pouvez déclarer plusieurs attributs individuellement, comme dans l’exemple de code précédent, ou vous pouvez les déclarer dans un jeu de crochets si vous utilisez un point-virgule pour séparer les différents attributs et les constructeurs, comme indiqué ici.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Les attributs généralement rencontrés incluent le `Obsolete` attribut, les attributs en matière de sécurité, d’attributs pour la prise en charge COM, les attributs relatifs à la propriété du code et les attributs indiquant si un type peut être sérialisé. L’exemple suivant illustre l’utilisation de la `Obsolete` attribut.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Pour les cibles d’attribut `assembly` et `module`, vous appliquez les attributs à un niveau supérieur `do` liaison dans votre assembly. Vous pouvez inclure le mot clé `assembly` ou `module` dans la déclaration d’attribut, comme suit.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Si vous omettez la cible d’attribut pour un attribut appliqué à un `do` de liaison, le compilateur F # tente de déterminer la cible d’attribut qui est appropriée pour cet attribut. Plusieurs classes d’attributs ont un attribut de type `System.AttributeUsageAttribute` qui inclut des informations sur les cibles possibles prises en charge pour cet attribut. Si la `System.AttributeUsageAttribute` indique que l’attribut prend en charge les fonctions en tant que cibles, l’attribut est pris à appliquer au point d’entrée principal du programme. Si la `System.AttributeUsageAttribute` indique que l’attribut prend en charge des assemblys comme cibles, le compilateur prend l’attribut à appliquer à l’assembly. La plupart des attributs ne s’appliquent pas aux fonctions et assemblys, mais dans les cas où ils le font, l’attribut est pris à appliquer à la fonction du programme principal. Si l’attribut cible est spécifiée explicitement, l’attribut est appliqué à la cible spécifiée.

Bien que vous n’avez généralement pas besoin de spécifier l’attribut cible explicitement, les valeurs valides pour *cible* dans un attribut sont affichés dans le tableau ci-dessous, ainsi que des exemples d’utilisation.

<table>
  <tr>
    <th>Cible de l’attribut</td>
    <th>Exemple</td> 
  </tr>
  <tr>
    <td>assembly</td>
    <td>`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</td> 
  </tr>
  <tr>
    <td>return</td>
    <td>' fonction1 permettent de x : [<return: Obsolete>] int = x + 1'</td> 
  </tr>
  <tr>
    <td>champ</td>
    <td>' [<field: DefaultValue>] les x: int mutable val'</td> 
  </tr>
  <tr>
    <td>propriété</td>
    <td>' [<property: Obsolete>] cela. MyProperty = x'</td> 
  </tr>
  <tr>
    <td>Param</td>
    <td>' membre cela. MyMethod ([<param: Out>] x : ref<int>) = x : = 10'</td> 
  </tr>
  <tr>
    <td>type</td>
    <td>
        ```
        [<type: StructLayout(Sequential)>] type MyStruct = struct x : byte y : fin de type int```
    </td> 
  </tr>
</table>

## <a name="see-also"></a>Voir aussi

[Informations de référence du langage F#](index.md)
