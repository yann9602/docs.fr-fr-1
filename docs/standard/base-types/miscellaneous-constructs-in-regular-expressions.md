---
title: "Constructions diverses dans les expressions régulières"
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
- constructs, miscellaneous
- .NET Framework regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9b33d196a7af9bc5a1f81c1624bbd98fea074319
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Constructions diverses dans les expressions régulières
Les expressions régulières dans .NET incluent trois constructions de langage diverses. L’une d’elles vous permet d’activer ou de désactiver des options de mise en correspondance particulières au milieu d’un modèle d’expression régulière. Grâce aux deux autres, vous pouvez inclure des commentaires dans une expression régulière.  
  
## <a name="inline-options"></a>Options inline  
 Vous pouvez définir ou désactiver des options de mise en correspondance de modèle spécifiques pour une partie d’une expression régulière en utilisant la syntaxe suivante :  
  
```  
(?imnsx-imnsx)  
```  
  
 Vous répertoriez les options à activer après le point d’interrogation et les options à désactiver après le signe moins. Le tableau suivant décrit chaque option. Pour plus d’informations sur chaque option, consultez [Options des expressions régulières](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Option|Description|  
|------------|-----------------|  
|`i`|Correspondance qui ne respecte pas la casse.|  
|`m`|Mode multiligne.|  
|`n`|Captures explicites uniquement. (Les parenthèses ne font pas office de groupes de capture.)|  
|`s`|Mode à ligne simple.|  
|`x`|Ignorer un espace blanc sans séquence d’échappement et autoriser les commentaires en mode x.|  
  
 Des modifications dans les options des expressions régulières définies par le `(?imnsx-imnsx)` construire reste en vigueur jusqu'à la fin du groupe englobant.  
  
> [!NOTE]
>  Le `(?imnsx-imnsx:` *sous-expression* `)` construction de regroupement fournit des fonctionnalités identiques pour une sous-expression. Pour plus d’informations, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 L’exemple suivant utilise le `i`, `n`, et `x` options pour activer le non-respect de la casse et les captures explicites et pour ignorer l’espace blanc dans le modèle d’expression régulière au milieu d’une expression régulière.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 L’exemple définit deux expressions régulières. La première, `\b(D\w+)\s(d\w+)\b`, correspond à deux mots consécutifs qui commencent par un « D » majuscule et un « d » minuscule. La seconde expression régulière, `\b(D\w+)(?ixn) \s (d\w+) \b`, utilise des options inline pour modifier ce modèle, comme décrit dans le tableau suivant. Une comparaison des résultats confirme l’effet de la construction `(?ixn)`.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`(D\w+)`|Mettre en correspondance un « D » majuscule suivi d’un ou de plusieurs caractères alphabétiques. Il s’agit du premier groupe de capture.|  
|`(?ixn)`|À partir de ce point, effectuer des comparaisons sans respect de la casse, effectuer seulement des captures explicites et ignorer l’espace blanc dans le modèle d’expression régulière.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`(d\w+)`|Mettre en correspondance un « d » majuscule ou minuscule suivi d’un ou de plusieurs caractères alphabétiques. Ce groupe n’est pas capturé, car le `n` (capture explicite) a été activée...|  
|`\b`|Mettre en correspondance la limite d'un mot.|  
  
## <a name="inline-comment"></a>Commentaire inline  
 Le `(?#` *commentaire* `)` construction vous permet d’inclure un commentaire inline dans une expression régulière. Le moteur des expressions régulières n’utilise pas de n’importe quelle partie du commentaire dans les critères spéciaux, bien que le commentaire est inclus dans la chaîne retournée par la <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> (méthode). Le commentaire se termine à la première parenthèse fermante.  
  
 L’exemple suivant répète le premier modèle d’expression régulière de l’exemple de la section précédente. Il ajoute deux commentaires inline à l’expression régulière pour indiquer si la comparaison respecte la casse. Le modèle d’expression régulière, `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b`, est défini comme suit.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`(?# case-sensitive comparison)`|Un commentaire. Il n’affecte pas le comportement de mise correspondance du modèle.|  
|`(D\w+)`|Mettre en correspondance un « D » majuscule suivi d’un ou de plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`(?ixn)`|À partir de ce point, effectuer des comparaisons sans respect de la casse, effectuer seulement des captures explicites et ignorer l’espace blanc dans le modèle d’expression régulière.|  
|`(?#case-insensitive comparison)`|Un commentaire. Il n’affecte pas le comportement de mise correspondance du modèle.|  
|`(d\w+)`|Mettre en correspondance un « d » majuscule ou minuscule suivi d’un ou de plusieurs caractères alphabétiques. Il s’agit du deuxième groupe de capture.|  
|`\b`|Mettre en correspondance la limite d'un mot.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Commentaire de fin de ligne  
 Un signe dièse (`#`) marque un commentaire en mode x, qui commence au caractère # sans séquence d’échappement à la fin du modèle d’expression régulière et continue jusqu'à la fin de la ligne. Pour utiliser cette construction, vous devez activer la `x` option (via les options inline) ou fournir le <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> valeur le `option` paramètre lors de l’instanciation le <xref:System.Text.RegularExpressions.Regex> objet ou l’appel de statique <xref:System.Text.RegularExpressions.Regex> (méthode).  
  
 L’exemple suivant illustre la construction du commentaire de fin de ligne. Il détermine si une chaîne est une chaîne de format composite qui inclut au moins un élément de format. Le tableau suivant décrit les constructions dans le modèle d’expression régulière :  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\{`|Mettre en correspondance une accolade ouvrante.|  
|`\d+`|Mettre en correspondance un ou plusieurs chiffres décimaux.|  
|`(,-*\d+)*`|Mettre en correspondance zéro ou une occurrence d’une virgule, suivie d’un signe moins facultatif, suivi par un ou plusieurs chiffres décimaux.|  
|`(\:\w{1,4}?)*`|Mettre en correspondance zéro ou une occurrence d’un signe deux-points, suivi par un à quatre espaces blancs, mais le moins possible.|  
|`(?#case insensitive comparison)`|Un commentaire inline. Il n’a aucun effet sur le comportement de la mise en correspondance du modèle.|  
|`\}`|Mettre en correspondance une accolade fermante.|  
|`(?x)`|Activer l’option permettant d’ignorer l’espace blanc dans le modèle, afin que le commentaire de fin de ligne soit reconnu.|  
|`# Looks for a composite format item.`|Un commentaire de fin de ligne.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Notez que, au lieu de fournir le `(?x)` construire dans l’expression régulière, le commentaire pourrait également avoir été reconnu en appelant le <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> (méthode) et en lui passant le <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> valeur d’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [Langage des expressions régulières - Aide-mémoire](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
