---
title: "Constructions de backreference dans les expressions r&#233;guli&#232;res | Microsoft Docs"
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
  - ".NET Framework (expressions régulières), constructions de backreference"
  - "références arrière"
  - "constructions, backreference"
  - "expressions régulières, constructions de backreference"
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Constructions de backreference dans les expressions r&#233;guli&#232;res
Les références arrières offrent un moyen commode pour identifier un caractère répété ou une sous\-chaîne dans une chaîne.  Par exemple, si la chaîne d'entrée contient plusieurs occurrences d'une sous\-chaîne arbitraire, vous pouvez mettre en correspondance la première occurrence avec un groupe de capture, puis utiliser une backreference pour faire correspondre les occurrences ultérieures de la sous\-chaîne.  
  
> [!NOTE]
>  Une syntaxe séparée est utilisée pour faire référence aux groupes de capture nommés et numérotés dans les chaînes de remplacement.  Pour plus d'informations, consultez [Substitutions](../../../docs/standard/base-types/substitutions-in-regular-expressions.md).  
  
 Le .NET Framework définit des éléments de langage différents pour qu'ils fassent référence aux groupes de capture comptés et nommés.  Pour plus d'informations sur les groupes de capture, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## Backreferences numérotées  
 Une référence arrière numérotée utilise la syntaxe suivante :  
  
 `\` *number*  
  
 où *number* est la position ordinale du groupe de capture dans l'expression régulière.  Par exemple, `\4` correspond au contenu du quatrième groupe de capture.  Si *number* n'est pas défini dans le modèle d'expression régulière, une erreur d'analyse se produit, et le moteur des expressions régulières lève une exception <xref:System.ArgumentException>.  Par exemple, l'expression régulière `\b(\w+)\s\1` est valide, parce que `(\w+)` est le premier et unique groupe de capture dans l'expression.  En revanche, `\b(\w+)\s\2` n'est pas valide et lève une exception d'argument, parce qu'il y a aucun groupe de capture numéroté `\2`.  
  
 Notez l'ambiguïté qui existe entre les codes d'échappement octaux \(tels que `\16`\) et les backreferences `\`*number* utilisant la même notation.  Cette ambiguïté est résolue comme suit :  
  
-   Les expressions `\1` jusqu'à `\9` sont toujours interprétées comme références arrières et non comme des codes octaux.  
  
-   Si le premier chiffre d'une expression à plusieurs chiffres est 8 ou 9 \(tel que `\80` ou `\91`\), l'expression est interprétée comme un littéral.  
  
-   Les expressions de `\10` et supérieur sont considérées comme des backreferences s'il y a un backreference qui correspond à ce nombre; sinon, elles sont interprétées comme codes octaux.  
  
-   Si une expression régulière contient un backreference à un numéro de groupe indéfini, une erreur d'analyse se produit et le moteur des expressions régulières lève une exception <xref:System.ArgumentException>.  
  
 Si l'ambiguïté est un problème, vous pouvez utiliser la `\k<`*name*`>`, qui est sans équivoque et qui ne peut pas être confondue avec les codes des caractères octaux.  De la même façon, les codes hexadécimaux tels que `\xdd` ne sont pas ambigus et ne peuvent pas être confondus avec les backreferences.  
  
 L'exemple suivant trouve des caractères doubles dans une chaîne.  Il définit une expression régulière, `(\w)\1`, qui se compose des éléments suivants.  
  
|Élément|Description|  
|-------------|-----------------|  
|`(\w)`|Mettre en correspondance un caractère alphabétique et l'assigner au premier groupe de capture.|  
|`\1`|Mettre en correspondance le caractère suivant qui est identique à la valeur du premier groupe de capture.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## Backreferences nommées  
 Une référence arrière nommée est définie à l'aide de la syntaxe suivante :  
  
 `\k<` *name* `>`  
  
 ou :  
  
 `\k'` *name* `'`  
  
 où *name* est le nom d'un groupe de capture défini dans le modèle d'expression régulière.  Si *name* n'est pas défini dans le modèle d'expression régulière, une erreur d'analyse se produit, et le moteur des expressions régulières lève une exception <xref:System.ArgumentException>.  
  
 L'exemple suivant trouve des caractères doubles dans une chaîne.  Il définit une expression régulière, `(?<char>\w)\k<char>`, qui se compose des éléments suivants.  
  
|Élément|Description|  
|-------------|-----------------|  
|`(?<char>\w)`|Mettre en correspondance un caractère alphabétique et l'assigner à un groupe de capture nommé `char`.|  
|`\k<char>`|Mettre en correspondance le caractère suivant qui est identique à la valeur du groupe de capture `char`.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 Notez que *name* peut également être la représentation sous forme de chaîne d'un nombre.  Par exemple, l'exemple suivant utilise l'expression régulière `(?<2>\w)\k<2>` pour rechercher des caractères alphabétiques doublés dans une chaîne.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## Mise en correspondance de backreferences  
 Une backreference renvoie à la définition la plus récente d'un groupe \(définition située à l'extrême gauche, lorsque la recherche s'effectue de gauche à droite\).  Lorsqu'un groupe effectue plusieurs captures, une backreference renvoie à la plus récente.  
  
 L'exemple suivant inclut un modèle d'expression régulière, `(?<1>a)(?<1>\1b)*`, qui redéfinit le groupe nommé \\1.  Le tableau suivant décrit chaque mode de l'expression régulière.  
  
|Modèle|Description|  
|------------|-----------------|  
|`(?<1>a)`|Mettre en correspondance le caractère « a » et assigner le résultat au groupe de capture nommé `1`.|  
|`(?<1>\1b)*`|Mettre en correspondance 0 ou 1 occurrence du groupe nommé `1` avec un « b » et assigner le résultat au groupe de capture nommé `1`.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 Lors de la comparaison de l'expression régulière avec la chaîne d'entrée \(« aababb »\), le moteur des expressions régulières exécute les opérations suivantes :  
  
1.  Il commence au début de la chaîne, et met en correspondance « a » avec l'expression `(?<1>a)`.  La valeur du groupe `1` est maintenant « a ».  
  
2.  Il avance jusqu'au deuxième caractère, et fait correspondre la chaîne « ab » avec l'expression `\1b` ou « ab ».  Il assigne ensuite le résultat, « ab » à `\1`.  
  
3.  Il avance jusqu'au quatrième caractère.  L'expression `(?<1>\1b)` sera mise en correspondance aucune ou plusieurs fois, pour que la chaîne « abb » corresponde à l'expression `\1b`.  Il réassigne le résultat, « abb », à `\1`.  
  
 Dans cet exemple, `*` un quantificateur en boucle \-\- il est évalué à plusieurs reprises jusqu'à ce que le moteur des expressions régulières ne puisse pas correspondre au modèle qu'il définit.  Les quantifieurs en boucle ne suppriment pas les définitions de groupe.  
  
 Si un groupe n'a capturé aucune sous\-chaîne, une backreference à ce groupe n'est pas définie et ne trouve aucune correspondance.  Cela est illustré par le modèle d'expression régulière `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, défini comme suit :  
  
|Modèle|Description|  
|------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(\p{Lu}{2})`|Mettre en correspondance deux lettres majuscules.  Il s'agit du premier groupe de capture.|  
|`(\d{2})?`|Mettre en correspondance zéro ou une occurrence de deux chiffres décimaux.  Il s'agit du deuxième groupe de capture.|  
|`(\p{Lu}{2})`|Mettre en correspondance deux lettres majuscules.  Il s'agit du troisième groupe de capture.|  
|`\b`|Terminez la correspondance sur la limite d'un mot.|  
  
 Une chaîne d'entrée peut correspondre à cette expression régulière même si les deux chiffres décimaux définis par le deuxième groupe de capture ne sont pas présents.  L'exemple suivant montre que, bien que la correspondance soit réussie, un groupe de capture vide est trouvé entre deux groupes de capture réussis.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## Voir aussi  
 [Langage des expressions régulières \- Aide\-mémoire](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)