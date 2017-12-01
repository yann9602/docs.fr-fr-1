---
title: "Analyse de chaînes numériques dans .NET"
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
- parsing strings, numeric strings
- numeric strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c9bb58b0d7b45ca197653742844be01ac3bbe41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-numeric-strings-in-net"></a>Analyse de chaînes numériques dans NET
Tous les types numériques disposent de deux méthodes d’analyse statiques, `Parse` et `TryParse`, que vous pouvez utiliser pour convertir la représentation sous forme de chaîne d’un nombre en type numérique. Ces méthodes vous permettent d’analyser les chaînes qui ont été générées à l’aide de chaînes de format documentées dans [Chaînes de format numériques standard](../../../docs/standard/base-types/standard-numeric-format-strings.md) et [Chaînes de format numériques personnalisées](../../../docs/standard/base-types/custom-numeric-format-strings.md). Par défaut, les méthodes `Parse` et `TryParse` peuvent convertir correctement les chaînes qui contiennent uniquement des chiffres décimaux intégraux en valeurs entières. Ils peuvent convertir correctement les chaînes qui contiennent des chiffres décimaux intégraux et fractionnaires, des séparateurs de groupe et un séparateur décimal en valeurs à virgule flottante. La méthode `Parse` lève une exception si l’opération échoue, tandis que la méthode `TryParse` retourne `false`.  
  
## <a name="parsing-and-format-providers"></a>Analyse et fournisseurs de format  
 En général, les représentations sous forme de chaîne de valeurs numériques varient selon la culture. Les éléments des chaînes numériques, tels que les symboles monétaires, les séparateurs de groupes (ou de milliers) et les séparateurs décimaux, varient selon la culture. Les méthodes d’analyse utilisent implicitement ou explicitement un fournisseur de format qui identifie ces variantes spécifiques à la culture. Si aucun fournisseur de format n’est spécifié dans un appel à la `Parse` ou `TryParse` (méthode), le fournisseur de format associé à la culture du thread en cours (la <xref:System.Globalization.NumberFormatInfo> objet retourné par la <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> propriété) est utilisé.  
  
 Un fournisseur de format est représenté par un <xref:System.IFormatProvider> mise en œuvre. Cette interface a un membre unique, la <xref:System.IFormatProvider.GetFormat%2A> méthode, dont le paramètre unique est un <xref:System.Type> objet qui représente le type à mettre en forme. Cette méthode retourne l’objet qui fournit des informations de mise en forme. .NET prend en charge les deux <xref:System.IFormatProvider> mises en œuvre pour analyser des chaînes numériques :  
  
-   A <xref:System.Globalization.CultureInfo> dont l’objet <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> méthode retourne un <xref:System.Globalization.NumberFormatInfo> objet qui fournit des informations de mise en forme propres à la culture.  
  
-   A <xref:System.Globalization.NumberFormatInfo> dont l’objet <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> méthode est retournée.  
  
 L’exemple suivant tente de convertir chaque chaîne d’un tableau à un <xref:System.Double> valeur. Il commence par essayer d’analyser la chaîne à l’aide d’un fournisseur de format qui reflète les conventions de la culture anglophone (États-Unis). Si cette opération lève une <xref:System.FormatException>, il tente d’analyser la chaîne à l’aide d’un fournisseur de format qui reflète les conventions de la culture Français (France).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analyse et valeurs NumberStyles  
 Les éléments de style (par exemple, un espace blanc, séparateurs de groupes et séparateur décimal) que l’opération d’analyse peut gérer sont définis par un <xref:System.Globalization.NumberStyles> valeur d’énumération. Par défaut, les chaînes qui représentent des valeurs entières sont analysées à l’aide de la <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> valeur, qui autorise uniquement des chiffres, blancs de début et de fin et un signe de début. Les chaînes qui représentent des valeurs à virgule flottante sont analysées à l’aide d’une combinaison de la <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> et <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> valeurs ; ce style composite autorise des chiffres décimaux, ainsi que de début et de fin d’un espace blanc, un signe de début, un séparateur décimal, un groupe séparateur et un exposant. En appelant une surcharge de la `Parse` ou `TryParse` méthode qui inclut un paramètre de type <xref:System.Globalization.NumberStyles> et en définissant un ou plusieurs <xref:System.Globalization.NumberStyles> indicateurs, vous pouvez contrôler les éléments de style qui peuvent être présents dans la chaîne pour l’opération d’analyse réussisse.  
  
 Par exemple, une chaîne qui contient un séparateur de groupes ne peut pas être convertie en un <xref:System.Int32> à l’aide de la <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> (méthode). Toutefois, la conversion réussit si vous utilisez la <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> indicateur, comme l’illustre l’exemple suivant.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  L’opération d’analyse utilise toujours les conventions de mise en forme d’une culture particulière. Si vous ne spécifiez pas une culture en passant un <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo> de l’objet, la culture associée au thread actuel est utilisée.  
  
 Le tableau suivant répertorie les membres de le <xref:System.Globalization.NumberStyles> énumération et décrit les effets de l’opération d’analyse.  
  
|Valeur NumberStyles|Effet sur la chaîne à analyser|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Seuls les chiffres sont autorisés.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Le séparateur décimal et les chiffres fractionnaires sont autorisés. Pour les valeurs entières, le seul chiffre fractionnaire autorisé est zéro. Séparateurs décimaux valides sont déterminés par le <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> ou <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> propriété.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|Les caractères « e » ou « E » peuvent être utilisés pour indiquer une notation exponentielle. Consultez <xref:System.Globalization.NumberStyles> pour plus d’informations.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|L’espace blanc de début est autorisé.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|L’espace blanc de fin est autorisé.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Un signe positif ou négatif peut précéder les chiffres.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Un signe positif ou négatif peut suivre les chiffres.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Les parenthèses peuvent être utilisées pour indiquer des valeurs négatives.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Le séparateur de groupes est autorisé. Le caractère de séparation de groupe est déterminé par le <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> ou <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> propriété.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Le symbole monétaire est autorisé. Le symbole monétaire est défini par le <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> propriété.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|La chaîne à analyser est interprétée comme un nombre hexadécimal. Elle peut inclure les chiffres hexadécimaux 0-9, A-F et a-f. Cet indicateur peut être utilisé uniquement pour analyser des valeurs entières.|  
  
 En outre, le <xref:System.Globalization.NumberStyles> énumération fournit les styles composites suivants, qui comprennent plusieurs <xref:System.Globalization.NumberStyles> indicateurs.  
  
|Valeur NumberStyles composite|Membres|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Inclut le <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, et <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> styles. Il s’agit du style par défaut utilisé pour analyser des valeurs entières.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Inclut le <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, et <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> styles.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Inclut le <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, et <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> styles.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Comprend tous les styles à l’exception de <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> et <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Comprend tous les styles à l’exception de <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Inclut le <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, et <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> styles.|  
  
## <a name="parsing-and-unicode-digits"></a>Analyse et chiffres Unicode  
 La norme Unicode définit des points de code pour les chiffres dans différents systèmes d’écriture. Par exemple, les points de code U+0030 à U+0039 représentent les chiffres latins de base 0 à 9, les points de code de U+09E6 à U+09EF représentent les chiffres bengalis compris entre 0 et 9, et les points de code U+FF10 à U+FF19 représentent les chiffres pleine chasse compris entre 0 et 9. Toutefois, les seuls chiffres identifiés par les méthodes d’analyse sont les chiffres latins de base 0 à 9 avec des points de code compris entre U+0030 et U+0039. Si une chaîne est passé à un méthode d’analyse numérique qui contient tous les autres chiffres, la méthode lève un <xref:System.FormatException>.  
  
 L’exemple suivant utilise la <xref:System.Int32.Parse%2A?displayProperty=nameWithType> méthode pour analyser des chaînes qui se composent de chiffres dans différents systèmes d’écriture. Comme l’indique le résultat de l’exemple, la tentative d’analyse des chiffres latins de base réussit, mais la tentative d’analyse des chiffres pleine chasse, arabe-hindi et bengali échoue.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Globalization.NumberStyles>  
 [Analyse de chaînes](../../../docs/standard/base-types/parsing-strings.md)  
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)
