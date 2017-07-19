---
title: "Constructions diverses dans les expressions r&#233;guli&#232;res | Microsoft Docs"
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
  - ".NET Framework (expressions régulières), constructions diverses"
  - "constructions, divers"
  - "expressions régulières, constructions diverses"
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Constructions diverses dans les expressions r&#233;guli&#232;res
Les expressions régulières dans le .NET Framework incluent trois constructions de langage diverses.  L'un vous permet d'activer ou de désactiver des options correspondantes particulières au milieu d'un modèle d'expression régulière.  Les deux constructions restantes vous permettent d'inclure des commentaires dans une expression régulière.  
  
## Options inline  
 Vous pouvez définir ou désactiver des options de critères spéciaux spécifiques pour une partie d'une expression régulière en utilisant la syntaxe  
  
```  
(?imnsx-imnsx)  
```  
  
 Vous répertoriez les options à activer après le point d'interrogation et les options à désactiver après le signe moins.  Le tableau suivant décrit chaque option.  Pour plus d'informations sur chaque option, consultez [Options des expressions régulières](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Option|Description|  
|------------|-----------------|  
|`i`|Correspondance non sensible à la casse.|  
|`m`|Mode multiligne.|  
|`n`|Captures explicites uniquement. \(Les parenthèses ne jouent pas le rôle de groupes de capture.\)|  
|`s`|Mode sur une ligne.|  
|`x`|Ignorer l'espace blanc sans séquence d'échappement et autoriser les commentaires de mode de x.|  
  
 Toutes modifications dans les options d'expression régulières définies par le concept `(?imnsx-imnsx)` restent effectives jusqu'à la fin du groupe englobant.  
  
> [!NOTE]
>  La construction de regroupement de la `(?imnsx-imnsx:`*subexpression*`)` fournit une fonctionnalité identique pour une sous\-expression.  Pour plus d'informations, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 L'exemple suivant utilise les options `i`, `n` et `x` pour activer le non\-respect de la casse et les saisies explicites, et ignorer les espaces dans le mode d'expression régulière au milieu d'une expression régulière.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 L'exemple montre deux expressions régulières.  Le premier, `\b(D\w+)\s(d\w+)\b`, correspond aux deux mots consécutifs qui commencent par un « D » majuscule et un « d » minuscule.  La deuxième expression régulière, `\b(D\w+)(?ixn) \s (d\w+) \b`, utilise des options inline pour modifier ce mode, comme décrit dans le tableau suivant.  Une comparaison des résultats confirme l'effet de la construction `(?ixn)`.  
  
|Modèle|Description|  
|------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`(D\w+)`|Mettre en correspondance un « D » majuscule suivi d'un ou plusieurs caractères alphabétiques.  Il s'agit du premier groupe de capture.|  
|`(?ixn)`|De ce point, effectuez des comparaisons non sensibles à la casse, faites des saisies explicites uniquement et ignorez l'espace blanc dans le modèle d'expression régulière.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`(d\w+)`|Mettre en correspondance un « d » majuscule ou minuscule suivi d'un ou plusieurs caractères alphabétiques.  Ce groupe n'est pas capturé parce que l'option `n` \(capture explicite\) a été activée.|  
|`\b`|Mettre en correspondance la limite d'un mot.|  
  
## Commentaire inline  
 La construction `(?#` *comment*`)` vous permet d'inclure un commentaire inline dans une expression régulière.  Le moteur d'expressions régulières n'utilise aucune partie du commentaire dans les critères spéciaux, bien que le commentaire soit inclus dans la chaîne retournée par la méthode <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=fullName>.  Le commentaire se termine à la première parenthèse fermante.  
  
 L'exemple suivant répète le premier mode d'expression régulière de l'exemple de la section précédente.  Il ajoute deux commentaires inline à l'expression régulière pour indiquer si la comparaison respecte la casse.  Le mode d'expression régulière, `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b`, est défini comme suit.  
  
|Modèle|Description|  
|------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`(?# case-sensitive comparison)`|Commentaire.  Il n'affecte pas le comportement de mise en correspondance des modèles.|  
|`(D\w+)`|Mettre en correspondance un « D » majuscule suivi d'un ou plusieurs caractères alphabétiques.  Il s'agit du premier groupe de capture.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`(?ixn)`|De ce point, effectuez des comparaisons non sensibles à la casse, faites des saisies explicites uniquement et ignorez l'espace blanc dans le modèle d'expression régulière.|  
|`(?#case-insensitive comparison)`|Commentaire.  Il n'affecte pas le comportement de mise en correspondance des modèles.|  
|`(d\w+)`|Mettre en correspondance un « d » majuscule ou minuscule suivi d'un ou plusieurs caractères alphabétiques.  Il s'agit du deuxième groupe de capture.|  
|`\b`|Mettre en correspondance la limite d'un mot.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## Commentaire de fin de ligne  
 Un signe dièse \(`#`\) marque un commentaire en mode x, lequel démarre au caractère \# sans séquence d'échappement à la fin du modèle d'expression régulière et continue jusqu'à la fin de la ligne.  Pour utiliser cette construction, vous devez activer l'option `x` \(via les options inline\) ou fournir la valeur <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> au paramètre `option` lors de l'instanciation de l'objet <xref:System.Text.RegularExpressions.Regex> ou lors de l'appel d'une méthode <xref:System.Text.RegularExpressions.Regex> statique.  
  
 L'exemple suivant illustre le constructeur de commentaire de fin de ligne.  Il détermine si une chaîne est une chaîne au format composite qui inclut au moins un élément de mise en forme.  Le tableau suivant décrit les constructions du mode d'expression régulière :  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Modèle|Description|  
|------------|-----------------|  
|`\{`|Mettre en correspondance une accolade ouvrante.|  
|`\d+`|Mettre en correspondance un ou plusieurs chiffres décimaux.|  
|`(,-*\d+)*`|Mettre en correspondance zéro ou une occurrence d'une virgule, suivie d'un signe moins facultatif, suivi d'un ou plusieurs chiffres décimaux.|  
|`(\:\w{1,4}?)*`|Mettre en correspondance zéro ou une occurrence du signe deux\-points, suivi d'un à quatre espaces blancs \(mais le moins possible\).|  
|`(?#case insensitive comparison)`|Un commentaire inline.  Il n'a aucun effet sur le comportement de mise en correspondance des modèles.|  
|`\}`|Mettre en correspondance une accolade fermante.|  
|`(?x)`|Activez l'option espace blanc du modèle Ignorer afin que le commentaire de fin de ligne soit reconnu.|  
|`# Looks for a composite format item.`|Commentaire de fin de ligne.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Notez que, au lieu de fournir la construction `(?x)` dans l'expression régulière, le commentaire aurait également pu être reconnu en appelant la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName> et en lui passant la valeur d'énumération <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>.  
  
## Voir aussi  
 [Langage des expressions régulières \- Aide\-mémoire](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)