---
title: "Comment : extraire un protocole et un numéro de port d'une URL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10ab05ac8b24c0658be2f27809137c6b0bd4834f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Comment : extraire un protocole et un numéro de port d'une URL
L’exemple suivant montre comment extraire un protocole et un numéro de port d’une URL.  
  
## <a name="example"></a>Exemple  
 L’exemple utilise le <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> méthode pour retourner le protocole suivi du signe deux-points suivi du numéro de port.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Le modèle d’expression régulière `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` peut être interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Commence la recherche de correspondance au début de la chaîne.|  
|`(?<proto>\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Nommer ce groupe `proto`.|  
|`://`|Mettre en correspondance un signe deux-points suivi de deux barres obliques.|  
|`[^/]+?`|Mettre en correspondance une ou plusieurs occurrences (mais le moins possible) de tout caractère autre qu’une barre oblique.|  
|`(?<port>:\d+)?`|Mettre en correspondance zéro ou une occurrence d’un signe deux-points suivi d’un ou de plusieurs caractères de chiffre. Nommer ce groupe `port`.|  
|`/`|Mettre en correspondance une barre oblique.|  
  
 Le <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> méthode développe le `${proto}${port}` séquence de remplacement, qui concatène la valeur des deux groupes nommés capturés dans le modèle d’expression régulière. Il s’agit d’une alternative pratique à la concaténation explicite des chaînes récupérées à partir de l’objet de la collection retournée par la <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> propriété.  
  
 L’exemple utilise le <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> méthode avec deux substitutions, `${proto}` et `${port}`, pour inclure les groupes capturés dans la chaîne de sortie. Vous pouvez récupérer les groupes capturés à partir de la correspondance <xref:System.Text.RegularExpressions.GroupCollection> de l’objet à la place, comme le montre le code suivant.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions régulières .NET](../../../docs/standard/base-types/regular-expressions.md)
