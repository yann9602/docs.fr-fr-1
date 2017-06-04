---
title: "Analyse de cha&#238;nes num&#233;riques dans .NET Framework | Microsoft Docs"
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
  - "analyse de chaînes, chaînes numériques"
  - "chaînes numériques"
  - "énumérations (.NET Framework), analyser des chaînes"
  - "types de base, analyse de chaînes"
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# Analyse de cha&#238;nes num&#233;riques dans .NET Framework
Tous les types numériques disposent de deux méthodes d'analyse statiques, `Parse` et `TryParse`, que vous pouvez utiliser pour convertir la représentation sous forme de chaîne d'un nombre en type numérique.  Ces méthodes vous permettent d'analyser les chaînes qui ont été générées à l'aide de chaînes de format documentées dans [Chaînes de format numériques standard](../../../docs/standard/base-types/standard-numeric-format-strings.md) et [Chaînes de format numériques personnalisées](../../../docs/standard/base-types/custom-numeric-format-strings.md).  Par défaut, les méthodes `Parse` et `TryParse` peuvent convertir correctement les chaînes qui contiennent uniquement des chiffres intégraux décimaux en valeurs entières.  Ils peuvent convertir correctement les chaînes qui contiennent des chiffres décimaux intégraux et fractionnaires, des séparateurs de groupe et un séparateur décimal en valeurs à virgule flottante.  La méthode `Parse` lève une exception si l'opération échoue, tandis que la méthode `TryParse` retourne `false`.  
  
## Analyse et fournisseurs de format  
 En général, les représentations sous forme de chaîne de valeurs numériques varient selon la culture.  Les éléments des chaînes numériques, tels que les symboles monétaires, les séparateurs de groupes \(ou de milliers\) et les séparateurs décimaux, varient selon la culture.  Les méthodes d'analyse utilisent implicitement ou explicitement un fournisseur de format qui identifie ces variantes spécifiques à la culture.  Si aucun fournisseur de format n'est spécifié dans un appel à la méthode `Parse` ou `TryParse`, le fournisseur de format associé à la culture du thread en cours \(l'objet <xref:System.Globalization.NumberFormatInfo> retourné par la propriété <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=fullName> \) est utilisé.  
  
 Un fournisseur de format est représenté par une implémentation <xref:System.IFormatProvider>.  Cette interface possède un seul membre, la méthode <xref:System.IFormatProvider.GetFormat%2A>, dont l'unique paramètre est un objet <xref:System.Type> qui représente le type à mettre en forme.  Cette méthode retourne l'objet qui fournit des informations de mise en forme.  Le .NET Framework prend en charge les deux implémentations <xref:System.IFormatProvider> suivantes pour analyser les chaînes numériques :  
  
-   Un objet <xref:System.Globalization.CultureInfo> dont la méthode <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=fullName> retourne un objet <xref:System.Globalization.NumberFormatInfo> qui fournit des informations de mise en forme propres à la culture.  
  
-   Un objet <xref:System.Globalization.NumberFormatInfo> dont la méthode <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=fullName> se retourne elle\-même.  
  
 L'exemple suivant essaie de convertir chaque chaîne d'un tableau en une valeur <xref:System.Double>.  Il commence par essayer d'analyser la chaîne à l'aide d'un fournisseur de format qui reflète les conventions de la culture anglophone \(États\-Unis\).  Si cette opération lève une exception <xref:System.FormatException>, elle tente d'analyser la chaîne à l'aide d'un fournisseur de format qui reflète les conventions de la culture française \(France\).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## Analyse et valeurs NumberStyles  
 Les éléments de style \(tels que les espaces blancs, les séparateurs de groupe et le séparateur décimal\) que l'opération d'analyse peut gérer sont définis par une valeur d'énumération <xref:System.Globalization.NumberStyles>.  Par défaut, les chaînes qui représentent des valeurs entières sont analysées à l'aide de la valeur <xref:System.Globalization.NumberStyles?displayProperty=fullName>, qui autorise uniquement les chiffres numériques, les espaces blancs de début et de fin et un signe de début.  Les chaînes qui représentent des valeurs à virgule flottante sont analysées à l'aide d'une combinaison des valeurs <xref:System.Globalization.NumberStyles?displayProperty=fullName> et <xref:System.Globalization.NumberStyles?displayProperty=fullName>. Ce style composite autorise les chiffres décimaux avec un espace blanc de début et de fin, un signe de début, un séparateur décimal, un séparateur de groupes et un exposant.  Lorsque vous appelez une surcharge de la méthode `Parse` ou `TryParse` qui inclut un paramètre de type <xref:System.Globalization.NumberStyles> et que vous définissez un ou plusieurs indicateurs <xref:System.Globalization.NumberStyles>, vous pouvez contrôler les éléments de style pouvant être présents dans la chaîne pour que l'opération d'analyse aboutisse.  
  
 Par exemple, une chaîne qui contient un séparateur de groupes ne peut pas être convertie en valeur de <xref:System.Int32> à l'aide de la méthode de <xref:System.Int32.Parse%28System.String%29?displayProperty=fullName>.  Toutefois, la conversion réussit si vous utilisez l'indicateur <xref:System.Globalization.NumberStyles?displayProperty=fullName>, comme le montre l'exemple suivant montre.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  L'opération d'analyse utilise toujours les conventions de mise en forme d'une culture particulière.  Si vous ne spécifiez pas de culture en passant un objet <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo>, la culture associée au thread en cours est utilisée.  
  
 Le tableau suivant répertorie les membres de l'énumération <xref:System.Globalization.NumberStyles> et décrit l'effet qu'ils ont sur l'opération d'analyse.  
  
|Valeur NumberStyles|Effet sur la chaîne à analyser|  
|-------------------------|------------------------------------|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Seuls les chiffres sont autorisés.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Le séparateur décimal et les chiffres fractionnaires sont autorisés.  Pour les valeurs entières, le seul chiffre fractionnaire autorisé est zéro.  Les séparateurs décimaux valides sont déterminés par la propriété <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=fullName> ou <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=fullName>.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Les caractères « e » ou « E » peuvent être utilisés pour indiquer une notation exponentielle.  Pour plus d'informations, consultez <xref:System.Globalization.NumberStyles>.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|L'espace blanc de début est autorisé.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|L'espace blanc de fin est autorisé.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Un signe positif ou négatif peut précéder les chiffres.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Un signe positif ou négatif peut suivre les chiffres.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Les parenthèses peuvent être utilisées pour indiquer des valeurs négatives.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Le séparateur de groupes est autorisé.  Le caractère de séparation de groupe est déterminé par la propriété <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=fullName> ou <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=fullName>.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Le symbole monétaire est autorisé.  Le symbole monétaire est défini par la propriété <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=fullName>.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|La chaîne à analyser est interprétée comme un nombre hexadécimal.  Elle peut inclure les chiffres hexadécimaux 0\-9, A\-F et a\-f.  Cet indicateur peut être utilisé uniquement pour analyser des valeurs entières.|  
  
 En outre, l'énumération <xref:System.Globalization.NumberStyles> fournit les styles composites suivants, qui comprennent plusieurs indicateurs <xref:System.Globalization.NumberStyles>.  
  
|Valeur NumberStyles composite|Comprend des membres|  
|-----------------------------------|--------------------------|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Comprend les styles <xref:System.Globalization.NumberStyles?displayProperty=fullName>, <xref:System.Globalization.NumberStyles?displayProperty=fullName> et <xref:System.Globalization.NumberStyles?displayProperty=fullName>.  Il s'agit du style par défaut utilisé pour analyser des valeurs entières.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Comprend les styles <xref:System.Globalization.NumberStyles?displayProperty=fullName>, <xref:System.Globalization.NumberStyles?displayProperty=fullName>, <xref:System.Globalization.NumberStyles?displayProperty=fullName>, <xref:System.Globalization.NumberStyles?displayProperty=fullName>, <xref:System.Globalization.NumberStyles?displayProperty=fullName> et <xref:System.Globalization.NumberStyles?displayProperty=fullName>.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Comprend les styles <xref:System.Globalization.NumberStyles?displayProperty=fullName>, <xref:System.Globalization.NumberStyles?displayProperty=fullName>, <xref:System.Globalization.NumberStyles?displayProperty=fullName>, <xref:System.Globalization.NumberStyles?displayProperty=fullName> et <xref:System.Globalization.NumberStyles?displayProperty=fullName>.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Comprend tous les styles, à l'exception de <xref:System.Globalization.NumberStyles?displayProperty=fullName> et <xref:System.Globalization.NumberStyles?displayProperty=fullName>.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Comprend tous les styles, à l'exception de <xref:System.Globalization.NumberStyles?displayProperty=fullName>.|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|Comprend les styles <xref:System.Globalization.NumberStyles?displayProperty=fullName>, <xref:System.Globalization.NumberStyles?displayProperty=fullName> et <xref:System.Globalization.NumberStyles?displayProperty=fullName>.|  
  
## Analyse et chiffres Unicode  
 La norme Unicode définit des points de code pour les chiffres dans différents systèmes d'écriture.  Par exemple, les points de code U\+0030 à U\+0039 représentent les chiffres latins de base 0 à 9, les points de code de U\+09E6 à U\+09EF représentent les chiffres bengalis compris entre 0 et 9, et les points de code U\+FF10 à U\+FF19 représentent les chiffres pleine chasse compris entre 0 et 9.  Toutefois, les seuls chiffres identifiés par les méthodes d'analyse sont les chiffres latins de base 0\-9 avec des points de code compris entre U\+0030 et U\+0039.  Si une chaîne est passée à une méthode d'analyse numérique qui contient tout autre chiffre, la méthode lève une exception <xref:System.FormatException>.  
  
 L'exemple suivant utilise la méthode <xref:System.Int32.Parse%2A?displayProperty=fullName> pour analyser des chaînes qui se composent de chiffres provenant de différents systèmes d'écriture.  Comme l'indique le résultat de l'exemple, la tentative d'analyse des chiffres latins de base réussit, mais la tentative d'analyse des chiffres pleine chasse, arabe\-hindi et bengali échoue.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## Voir aussi  
 <xref:System.Globalization.NumberStyles>   
 [Analyse de chaînes](../../../docs/standard/base-types/parsing-strings.md)   
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)