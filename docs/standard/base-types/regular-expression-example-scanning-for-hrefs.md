---
title: "Exemple d'expression régulière : recherche de valeurs HREF"
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
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bc9db7317c7a73f70a2cb83322b8b3a4c3771b9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>Exemple d'expression régulière : recherche de valeurs HREF
L’exemple suivant recherche une chaîne d’entrée et affiche toutes les valeurs href="…" et leurs emplacements dans la chaîne.  
  
## <a name="the-regex-object"></a>Objet Regex  
 Étant donné que la `DumpHRefs` méthode peut être appelée plusieurs fois à partir du code utilisateur, il utilise le `static` (`Shared` en Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> (méthode). Cela permet au moteur d’expression régulière pour mettre en cache de l’expression régulière et évite d’instanciation d’un nouvel <xref:System.Text.RegularExpressions.Regex> objet chaque fois que la méthode est appelée. A <xref:System.Text.RegularExpressions.Match> objet est ensuite utilisé pour itérer sur toutes les correspondances dans la chaîne.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 L’exemple suivant illustre un appel à la méthode `DumpHRefs`.  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 Le modèle d'expression régulière `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` est interprété comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`href`|Correspond à la chaîne littérale « href ». La recherche de correspondance ne respecte pas la casse.|  
|`\s*`|Correspond à zéro, un ou plusieurs espaces blancs.|  
|`=`|Mettre en correspondance le signe égal.|  
|`\s*`|Correspond à zéro, un ou plusieurs espaces blancs.|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|Correspond à une des valeurs suivantes sans affecter le résultat à un groupe capturé :<br /><br /> -Un guillemet ou l’apostrophe, suivie de zéro ou plusieurs occurrences de n’importe quel caractère autre qu’un guillemet ou l’apostrophe, suivi par une apostrophe ou un guillemet. Le groupe nommé `1` est inclus dans ce modèle.<br />-Un ou plusieurs caractères autre qu’un espace blanc. Le groupe nommé `1` est inclus dans ce modèle.|  
|`(?<1>[^"']*)`|Affecte zéro, une ou plusieurs occurrences de tout caractère autre qu’un guillemet ou une apostrophe au groupe de capture nommé `1`.|  
|`"(?<1>\S+)`|Affecte un ou plusieurs caractères non espace blanc au groupe de capture nommé `1`.|  
  
## <a name="match-result-class"></a>Classe de résultats Match  
 Les résultats d’une recherche sont stockés dans le <xref:System.Text.RegularExpressions.Match> (classe), qui permet d’accéder à toutes les sous-chaînes extraites par la recherche. Il conserve également la chaîne recherchée et l’expression régulière utilisée, afin qu’il peut appeler le <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> méthode pour effectuer une nouvelle recherche commençant où la dernière s’est terminée.  
  
## <a name="explicitly-named-captures"></a>Captures explicitement nommées  
 Dans les expressions régulières classiques, les parenthèses de capture sont automatiquement numérotées dans l’ordre. Cela génère deux problèmes. Tout d’abord, si une expression régulière est modifiée par l’insertion ou la suppression d’un jeu de parenthèses, tout code qui fait référence aux captures numérotées doit être réécrit pour refléter la nouvelle numérotation. Ensuite, étant donné que différents jeux de parenthèses sont souvent utilisés pour fournir deux expressions différentes pour une correspondance acceptable, il peut s’avérer difficile de déterminer laquelle des deux expressions en fait retourné un résultat.  
  
 Pour résoudre ces problèmes, le <xref:System.Text.RegularExpressions.Regex> classe prend en charge la syntaxe `(?<name>…)` permettant de capturer une correspondance dans un emplacement spécifié (l’emplacement peut être nommé à l’aide d’une chaîne ou un entier ; entiers peuvent être rappelées plus rapidement). Ainsi, les autres correspondances de la même chaîne peuvent toutes être dirigées vers le même emplacement. En cas de conflit, la dernière correspondance placée dans un emplacement est la correspondance correcte. (Toutefois, la liste complète des différentes correspondances pour un seul emplacement est disponible. Consultez le <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection pour plus d’informations.)  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions régulières .NET](../../../docs/standard/base-types/regular-expressions.md)
