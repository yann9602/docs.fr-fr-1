---
title: "Exemple d&#39;expression r&#233;guli&#232;re&#160;: modification des formats de date | Microsoft Docs"
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
  - "recherche avec des expressions régulières, exemples"
  - "analyse de texte avec des expressions régulières, exemples"
  - "expressions régulières, exemples"
  - ".NET Framework (expressions régulières), exemples"
  - "expressions régulières (.NET Framework), exemples"
  - "mise en correspondance de modèles avec des expressions régulières, exemples"
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Exemple d&#39;expression r&#233;guli&#232;re&#160;: modification des formats de date
L'exemple de code suivant utilise la méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=fullName> pour remplacer les dates au format *mm*\/*dd*\/*yy* par des dates au format *dd*\-*mm*\-*yy*.  
  
## Exemple  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 L'exemple de code suivant montre comment appeler la méthode `MDYToDMY` dans une application.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## Commentaires  
 Le modèle d'expression régulière  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(?<month>\d{1,2})`|Mettre en correspondance un ou deux chiffres décimaux.  Il s'agit du groupe capturé `month`.|  
|`/`|Mettre en correspondance la barre oblique.|  
|`(?<day>\d{1,2})`|Mettre en correspondance un ou deux chiffres décimaux.  Il s'agit du groupe capturé `day`.|  
|`/`|Mettre en correspondance la barre oblique.|  
|`(?<year>\d{2,4})`|Mettre en correspondance de deux à quatre chiffres décimaux.  Il s'agit du groupe capturé `year`.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  
  
 Le modèle `${day}-${month}-${year}` définit la chaîne de remplacement comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|------------|-----------------|  
|`$(day)`|Ajoutez la chaîne capturée par le groupe de capture `day`.|  
|`-`|Ajoutez un trait d'union.|  
|`$(month)`|Ajoutez la chaîne capturée par le groupe de capture `month`.|  
|`-`|Ajoutez un trait d'union.|  
|`$(year)`|Ajoutez la chaîne capturée par le groupe de capture `year`.|  
  
## Voir aussi  
 [Expressions régulières du .NET Framework](../../../docs/standard/base-types/regular-expressions.md)