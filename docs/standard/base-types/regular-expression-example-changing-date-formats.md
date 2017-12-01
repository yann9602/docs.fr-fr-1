---
title: "Exemple d'expression régulière : modification des formats de date"
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
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eeaed0951018c989612691065c027ee46bd6655a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-example-changing-date-formats"></a>Exemple d'expression régulière : modification des formats de date
Le code suivant exemple utilise le <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> méthode pour remplacer les dates au format *mm*/*jj*/*yy* avec des dates qui la forme *jj*-*mm*-*yy*.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 Le code suivant montre comment la méthode `MDYToDMY` peut être appelée dans une application.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Commentaires  
 Le modèle d’expression régulière `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(?<month>\d{1,2})`|Mettre en correspondance un ou deux chiffres décimaux. Il s’agit du groupe capturé `month`.|  
|`/`|Mettre en correspondance la barre oblique.|  
|`(?<day>\d{1,2})`|Mettre en correspondance un ou deux chiffres décimaux. Il s’agit du groupe capturé `day`.|  
|`/`|Mettre en correspondance la barre oblique.|  
|`(?<year>\d{2,4})`|Mettre en correspondance de deux à quatre chiffres décimaux. Il s’agit du groupe capturé `year`.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
 Le modèle `${day}-${month}-${year}` définit la chaîne de remplacement comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`$(day)`|Ajouter la chaîne capturée par le groupe de capture `day`.|  
|`-`|Ajouter un trait d’union.|  
|`$(month)`|Ajouter la chaîne capturée par le groupe de capture `month`.|  
|`-`|Ajouter un trait d’union.|  
|`$(year)`|Ajouter la chaîne capturée par le groupe de capture `year`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions régulières .NET](../../../docs/standard/base-types/regular-expressions.md)
