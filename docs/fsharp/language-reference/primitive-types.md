---
title: Types primitifs (F#)
description: "Découvrez les types primitifs fondamentaux utilisés dans le langage F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a>Types primitifs

Cette rubrique répertorie les types primitifs fondamentaux utilisés dans le langage F #. Elle fournit également les types .NET correspondants et les valeurs minimales et maximales pour chaque type.

## <a name="summary-of-primitive-types"></a>Résumé des Types primitifs
Le tableau suivant résume les propriétés des types F # primitifs.

|Type|Type .NET|Description|
|----|---------|-----------|
|`bool`|`System.Boolean`|Les valeurs possibles sont `true` et `false`.|
|`byte`|`System.Byte`|Valeurs comprises entre 0 et 255.|
|`sbyte`|`System.SByte`|Valeurs entre -128 et 127.|
|`int16`|`System.Int16`|Valeurs comprises entre-32 768 et 32 767.|
|`uint16`|`System.UInt16`|Valeurs comprises entre 0 et 65535.|
|`int`|`System.Int32`|Valeurs d’allant de -2,147,483,648 à 2 147 483 647.|
|`uint32`|`System.UInt32`|Valeurs de 0 à 4 294 967 295.|
|`int64`|`System.Int64`|Valeurs de -9,223,372,036,854,775,808 à 9,223,372,036,854,775,807.|
|`uint64`|`System.UInt64`|Valeurs comprises entre 0 et 18,446,744,073,709,551,615.|
|`nativeint`|`System.IntPtr`|Un pointeur natif comme un entier signé.|
|`unativeint`|`System.UIntPtr`|Un pointeur natif en tant qu’entier non signé.|
|`char`|`System.Char`|Valeurs de caractères Unicode.|
|`string`|`System.String`|Texte Unicode.|
|`decimal`|`System.Decimal`|Type de données qui comporte au moins 28 chiffres significatifs à virgule flottante.|
|`unit`|non applicable|Indique l’absence d’une valeur réelle. Le type n'a qu’une seule valeur formelle, ce qui est indiquée `()`. La valeur de l’unité, `()`, est souvent utilisé comme espace réservé où une valeur est requise, mais aucune valeur réelle n’est disponible ou de sens.|
|`void`|`System.Void`|Indique le type ou la valeur.|
|`float32, single`|`System.Single`|Un type à virgule flottante 32 bits.|
|`float, double`|`System.Double`|Un type à virgule flottante 64 bits.|

>[!NOTE]
Vous pouvez effectuer des calculs avec des entiers trop grands pour le type d’entier 64 bits à l’aide de la [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type. `bigint`n’est pas considéré comme un type primitif ; Il est l’abréviation de `System.Numerics.BigInteger`.

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)
