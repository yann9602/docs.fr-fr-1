---
title: "Cha&#238;nes de format TimeSpan standard. | Microsoft Docs"
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
  - "spécificateurs de format, intervalle de temps standard"
  - "spécificateurs de format, intervalles de temps"
  - "chaînes de format"
  - "mise en forme (.NET Framework), heure"
  - "mise en forme (.NET Framework), intervalles de temps"
  - "chaînes de format standard, intervalles de temps"
  - "chaînes de format d'intervalle de temps standard"
  - "chaînes de format TimeSpan standard"
  - "heure (.NET Framework), mettre en forme"
  - "intervalles de temps (.NET Framework), mettre en forme"
ms.assetid: 9f6c95eb-63ae-4dcc-9c32-f81985c75794
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Cha&#238;nes de format TimeSpan standard.
Une chaîne de format <xref:System.TimeSpan> standard utilise un spécificateur de format pour définir la représentation textuelle d'une valeur <xref:System.TimeSpan> qui résulte d'une opération de mise en forme.  Toute chaîne de format contenant plusieurs caractères alphabétiques, y compris un espace blanc, est interprétée comme une chaîne de format <xref:System.TimeSpan> personnalisée.  Pour plus d'informations, consultez [Chaînes de format TimeSpan personnalisées](../../../docs/standard/base-types/custom-timespan-format-strings.md).  
  
 Les représentations sous forme de chaîne de valeurs <xref:System.TimeSpan> sont produites par des appels aux surcharges de la méthode <xref:System.TimeSpan.ToString%2A?displayProperty=fullName>, ainsi que par les méthodes qui prennent en charge la mise en forme composite, telles que <xref:System.String.Format%2A?displayProperty=fullName>.  Pour plus d’informations, consultez [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md) et [Mise en forme composite](../../../docs/standard/base-types/composite-formatting.md).  L'exemple suivant illustre l'utilisation de chaînes de format standard dans des opérations de mise en forme.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Les chaînes de format <xref:System.TimeSpan> standard sont également utilisées par les méthodes <xref:System.TimeSpan.ParseExact%2A?displayProperty=fullName> et <xref:System.TimeSpan.TryParseExact%2A?displayProperty=fullName> pour définir le format requis des chaînes d'entrée pour les opérations d'analyse.  \(L'analyse convertit la représentation sous forme de chaîne d'une valeur en cette valeur.\) L'exemple suivant illustre l'utilisation de chaînes de format standard dans des opérations d'analyse.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a> Le tableau suivant répertorie les spécificateurs de format d'intervalle de temps standard.  
  
|Spécificateur de format|Nom|Description|Exemples|  
|-----------------------------|---------|-----------------|--------------|  
|"c"|Format constant \(invariant\)|Ce spécificateur ne dépend pas de la culture.  Son format est le suivant : `[-][d’.’]hh’:’mm’:’ss[‘.’fffffff]`.<br /><br /> \(les chaînes de format "t" et "T" produisent les mêmes résultats\)<br /><br /> Pour plus d'informations, consultez [Spécificateur de format constant \("c"\)](#Constant).|`TimeSpan.Zero` \-\> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` \-\> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` \-\> 3.17:25:30.5000000|  
|"g"|Format court général|Ce spécificateur retourne uniquement ce qui est nécessaire.  Il dépend de la culture et prend la forme suivante : `[-][d’:’]h’:’mm’:’ss[.FFFFFFF]`.<br /><br /> Pour plus d'informations, consultez [Spécificateur de format court général \("g"\)](#GeneralShort).|`New TimeSpan(1, 3, 16, 50, 500)` \-\> 1:3:16:50.5 \(en\-US\)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)` \-\> 1:3:16:50,5 \(fr\-FR\)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` \-\> 1:3:16:50.599 \(en\-US\)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` \-\> 1:3:16:50,599 \(fr\-FR\)|  
|"G"|Format long général|Ce spécificateur retourne toujours les jours et sept chiffres fractionnaires.  Il dépend de la culture et prend la forme suivante : `[-]d’:’hh’:’mm’:’ss.fffffff`.<br /><br /> Pour plus d'informations, consultez [Spécificateur de format long général \("G"\)](#GeneralLong).|`New TimeSpan(18, 30, 0)` \-\> 0:18:30:00.0000000 \(en\-US\)<br /><br /> `New TimeSpan(18, 30, 0)` \-\> 0:18:30:00,0000000 \(fr\-FR\)|  
  
<a name="Constant"></a>   
## Spécificateur de format constant \("c"\)  
 Le spécificateur de format "c" retourne la représentation sous forme de chaîne d'une valeur <xref:System.TimeSpan> au format suivant :  
  
 \[\-\]\[*d*.\]*hh*:*mm*:*ss*\[.*fffffff*\]  
  
 Les éléments entre crochets \(\[ et \]\) sont facultatifs.  Le point \(.\) et les deux\-points \(:\) sont des symboles littéraux.  Le tableau suivant décrit les éléments restants.  
  
|Élément|Description|  
|-------------|-----------------|  
|*\-*|Signe négatif facultatif, qui indique un intervalle de temps négatif.|  
|*d*|Nombre facultatif de jours, sans zéros non significatifs.|  
|*hh*|Nombre d'heures, allant de "00" à "23".|  
|*mm*|Nombre de minutes, allant de "00" à "59".|  
|*ss*|Nombre de secondes, allant de "0" à "59".|  
|*fffffff*|Partie fractionnaire facultative d'une seconde.  Sa valeur peut varier de "0000001" \(une graduation ou un dix\-millionième de seconde\) à "9999999" \(9 999 999 dix\-millionièmes de seconde ou une seconde moins une graduation\).|  
  
 Contrairement aux spécificateurs de format "g" et "G", le spécificateur de format "c" ne dépend pas de la culture.  Il produit la représentation sous forme de chaîne d'une valeur <xref:System.TimeSpan> qui est invariante et commune à toutes les versions du .NET Framework antérieures au [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. "  "c" est la chaîne de format <xref:System.TimeSpan> par défaut. La méthode <xref:System.TimeSpan.ToString?displayProperty=fullName> met en forme une valeur d'intervalle de temps à l'aide de la chaîne de format "c".  
  
> [!NOTE]
>  <xref:System.TimeSpan> prend également en charge les chaînes de format standard "t" et "T", dont le comportement est identique à celui de la chaîne de format standard "c".  
  
 L'exemple suivant instancie deux objets <xref:System.TimeSpan>, les utilise pour effectuer des opérations arithmétiques, puis affiche le résultat.  Dans chaque cas, il utilise la mise en forme composite pour afficher la valeur <xref:System.TimeSpan> à l'aide du spécificateur de format "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [Retour au tableau](#Top)  
  
<a name="GeneralShort"></a>   
## Spécificateur de format court général \("g"\)  
 Le spécificateur de format "g" <xref:System.TimeSpan> retourne la représentation sous forme de chaîne d'une valeur <xref:System.TimeSpan> dans un format compact, en incluant uniquement les éléments qui sont nécessaires.  Son format est le suivant :  
  
 \[\-\]\[*d*:\]*h*:*mm*:*ss*\[.*FFFFFFF*\]  
  
 Les éléments entre crochets \(\[ et \]\) sont facultatifs.  Le signe deux\-points \(:\) est un symbole littéral.  Le tableau suivant décrit les éléments restants.  
  
|Élément|Description|  
|-------------|-----------------|  
|*\-*|Signe négatif facultatif, qui indique un intervalle de temps négatif.|  
|*d*|Nombre facultatif de jours, sans zéros non significatifs.|  
|*h*|Nombre d'heures, allant de "0" à "23", sans zéros non significatifs.|  
|*mm*|Nombre de minutes, allant de "00" à "59".|  
|*ss*|Nombre de secondes, allant de "00" à "59".|  
|*.*|Séparateur des fractions de seconde.  Il équivaut à la propriété <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> de la culture spécifiée, sans substitutions par l'utilisateur.|  
|*FFFFFFF*|Fractions de seconde.  Le moins de chiffres possible sont affichés.|  
  
 Tout comme le spécificateur de format "G", le spécificateur de format "g" est localisé.  Son séparateur de fraction de seconde est basé sur la propriété <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> de la culture actuelle ou de la culture spécifiée.  
  
 L'exemple suivant instancie deux objets <xref:System.TimeSpan>, les utilise pour effectuer des opérations arithmétiques, puis affiche le résultat.  Dans chaque cas, il utilise la mise en forme composite pour afficher la valeur <xref:System.TimeSpan> à l'aide du spécificateur de format "g".  De plus, il met en forme la valeur <xref:System.TimeSpan> à l'aide des conventions de format de la culture système actuelle \(dans le cas présent, Anglais \- États\-Unis ou en\-US\) et de la culture Français \- France \(fr\-FR\).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [Retour au tableau](#Top)  
  
<a name="GeneralLong"></a>   
## Spécificateur de format long général \("G"\)  
 Le spécificateur de format "G" <xref:System.TimeSpan> retourne la représentation sous forme de chaîne d'une valeur <xref:System.TimeSpan> sous une forme longue comprenant toujours les jours et les fractions de secondes.  La chaîne qui résulte du spécificateur de format standard "G" est au format suivant :  
  
 \[\-\]*d*:*hh*:*mm*:*ss*.*fffffff*  
  
 Les éléments entre crochets \(\[ et \]\) sont facultatifs.  Le signe deux\-points \(:\) est un symbole littéral.  Le tableau suivant décrit les éléments restants.  
  
|Élément|Description|  
|-------------|-----------------|  
|*\-*|Signe négatif facultatif, qui indique un intervalle de temps négatif.|  
|*d*|Nombre de jours, sans zéros non significatifs.|  
|*hh*|Nombre d'heures, allant de "00" à "23".|  
|*mm*|Nombre de minutes, allant de "00" à "59".|  
|*ss*|Nombre de secondes, allant de "00" à "59".|  
|*.*|Séparateur des fractions de seconde.  Il équivaut à la propriété <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> de la culture spécifiée, sans substitutions par l'utilisateur.|  
|*fffffff*|Fractions de seconde.|  
  
 Tout comme le spécificateur de format "G", le spécificateur de format "g" est localisé.  Son séparateur de fraction de seconde est basé sur la propriété <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> de la culture actuelle ou de la culture spécifiée.  
  
 L'exemple suivant instancie deux objets <xref:System.TimeSpan>, les utilise pour effectuer des opérations arithmétiques, puis affiche le résultat.  Dans chaque cas, il utilise la mise en forme composite pour afficher la valeur <xref:System.TimeSpan> à l'aide du spécificateur de format "G".  De plus, il met en forme la valeur <xref:System.TimeSpan> à l'aide des conventions de format de la culture système actuelle \(dans le cas présent, Anglais \- États\-Unis ou en\-US\) et de la culture Français \- France \(fr\-FR\).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [Retour au tableau](#Top)  
  
## Voir aussi  
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)   
 [Chaînes de format TimeSpan personnalisées](../../../docs/standard/base-types/custom-timespan-format-strings.md)   
 [Analyse de chaînes](../../../docs/standard/base-types/parsing-strings.md)