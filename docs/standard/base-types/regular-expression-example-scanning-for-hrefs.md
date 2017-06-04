---
title: "Exemple d&#39;expression r&#233;guli&#232;re&#160;: recherche de valeurs HREF | Microsoft Docs"
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
  - "recherche à l’aide d’expressions régulières, exemples"
  - "analyse de texte à l’aide d’expressions régulières, exemples"
  - "expressions régulières, exemples"
  - ".NET Framework (expressions régulières), exemples"
  - "expressions régulières (.NET Framework), exemples"
  - "mise en correspondance de modèles avec des expressions régulières, exemples"
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: 24
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 24
---
# Exemple d&#39;expression r&#233;guli&#232;re&#160;: recherche de valeurs HREF
L'exemple suivant recherche une chaîne d'entrée et affiche toutes les valeurs href\="..." et leurs emplacements dans la chaîne.  
  
## Objet Regex  
 Étant donné que la méthode `DumpHRefs` peut être appelée plusieurs fois depuis du code utilisateur, la méthode `static` \(`Shared` en Visual Basic\) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName> est utilisée.  Le moteur des expressions régulières peut ainsi mettre l'expression régulière en cache, ce qui évite la surcharge liée à l'instanciation d'un nouvel objet <xref:System.Text.RegularExpressions.Regex> à chaque appel à la méthode.  Un objet <xref:System.Text.RegularExpressions.Match> est ensuite utilisé pour itérer au sein de toutes les correspondances de la chaîne.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 L'exemple suivant illustre ensuite un appel à la méthode `DumpHRefs`.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Le modèle d'expression régulière `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|------------|-----------------|  
|`href`|Correspond à la chaîne littéral « href ».  Cette correspondance respecte la casse.|  
|`\s*`|Correspond à zéro, un ou plusieurs espaces blancs.|  
|`=`|Correspond au signe égal.|  
|`\s*`|Correspond à zéro, un ou plusieurs espaces blancs.|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|Correspond à l'un des éléments suivants sans assigner de résultat à un groupe capturé :<br /><br /> -   Un guillemet ou une apostrophe, suivi par zéro, une ou plusieurs occurrences de tout caractère autre qu'un guillemet ou une apostrophe, puis suivi par un guillemet ou une apostrophe.  Le groupe nommé `1` est inclus dans ce modèle.<br />-   Un ou plusieurs caractères autres que des espaces blancs.  Le groupe nommé `1` est inclus dans ce modèle.|  
|`(?<1>[^"']*)`|Assigne zéro, une ou plusieurs occurrences de tout caractère autre qu'un guillemet ou une apostrophe au groupe de capture nommé `1`.|  
|`"(?<1>\S+)`|Assigne un ou plusieurs caractères autres que des espaces blancs au groupe de capture nommé `1`.|  
  
## Classe des résultats d'une mise en correspondance  
 Les résultats d'une recherche sont stockés dans la classe <xref:System.Text.RegularExpressions.Match>, qui donne accès à toutes les sous\-chaînes extraites par la recherche.  Cette classe garde également en mémoire la chaîne recherchée et l'expression régulière utilisée, de manière à appeler la méthode <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=fullName> pour effectuer une nouvelle recherche commençant à l'endroit où la dernière s'est terminée.  
  
## Captures nommées explicitement  
 Dans les expressions régulières classiques, les parenthèses sont automatiquement numérotées dans l'ordre croissant.  Cela génère deux problèmes.  Tout d'abord, si une expression régulière est modifiée, par exemple par insertion ou ajout d'un jeu de parenthèses, l'ensemble du code qui renvoie aux captures numérotées doit être réécrit pour prendre en compte la nouvelle numérotation.  Ensuite, étant donné que différents jeux de parenthèses sont souvent utilisés pour fournir deux expressions différentes pour une correspondance acceptable, il est parfois difficile d'identifier laquelle de ces expressions a retourné un résultat.  
  
 Pour résoudre ces problèmes, la classe <xref:System.Text.RegularExpressions.Regex> prend en charge la syntaxe `(?<name>…)` permettant de capturer une correspondance dans un emplacement spécifié \(l'emplacement peut être nommé à l'aide d'une chaîne ou d'un entier, sachant que les entiers peuvent être rappelés plus rapidement\).  Ainsi, les différentes correspondances de la même chaîne peuvent être dirigées vers le même endroit.  En cas de conflit, la dernière correspondance placée dans un emplacement est considérée étant comme la bonne. \(Une liste complète des différentes correspondances existant pour un même emplacement est cependant disponible.  Consultez la collection <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=fullName> pour plus de détails.\)  
  
## Voir aussi  
 [Expressions régulières du .NET Framework](../../../docs/standard/base-types/regular-expressions.md)