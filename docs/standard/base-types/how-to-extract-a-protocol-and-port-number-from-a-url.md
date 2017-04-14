---
title: "Comment&#160;: extraire un protocole et un num&#233;ro de port d&#39;une URL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework (expressions régulières), exemples"
  - "analyser du texte avec des expressions régulières, exemples"
  - "mise en correspondance de modèles avec des expressions régulières, exemples"
  - "expressions régulières (.NET Framework), exemples"
  - "expressions régulières, exemples"
  - "rechercher avec des expressions régulières, exemples"
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: extraire un protocole et un num&#233;ro de port d&#39;une URL
L'exemple suivant extrait un protocole et un numéro de port d'une URL.  
  
## Exemple  
 L'exemple utilise la méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> pour retourner le protocole suivi du signe deux\-points, lui\-même suivi du numéro de port.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 Le modèle d'expression régulière `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` peut être interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|------------|-----------------|  
|`^`|Commence la recherche de correspondance au début de la chaîne.|  
|`(?<proto>\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques.  Nommez ce groupe `proto`.|  
|`://`|Mettre en correspondance le signe deux\-points suivis de deux barres obliques.|  
|`[^/]+?`|Mettre en correspondance une ou plusieurs occurrences \(mais le moins possible\) de tout caractère autre qu'une barre oblique.|  
|`(?<port>:\d+)?`|Mettre en correspondance zéro ou une occurrence du signe deux\-points suivi d'un ou de plusieurs caractères numériques.  Nommez ce groupe `port`.|  
|`/`|Mettre en correspondance une barre oblique.|  
  
 La méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> développe la séquence de remplacement `${proto}${port}`, qui concatène la valeur des deux groupes nommés capturés dans le modèle d'expression régulière.  C'est une alternative pratique à la concaténation explicite des chaînes récupérées de l'objet collection qui est retourné par la propriété <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=fullName>.  
  
 L'exemple utilise la méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> avec deux substitutions, `${proto}` et `${port}`, pour inclure les groupes capturés dans la chaîne de sortie.  Vous pouvez récupérer à la place les groupes capturés de l'objet <xref:System.Text.RegularExpressions.GroupCollection> de la correspondance, comme le montre le code suivant.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## Voir aussi  
 [Expressions régulières du .NET Framework](../../../docs/standard/base-types/regular-expressions.md)