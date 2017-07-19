---
title: "Comment&#160;: d&#233;finir et utiliser des fournisseurs de format num&#233;rique personnalis&#233;s | Microsoft Docs"
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
  - "chaînes de format personnalisées"
  - "chaînes de format numérique personnalisées"
  - "afficher les données de date et d'heure"
  - "fournisseurs de format (.NET Framework)"
  - "mise en forme (.NET Framework), nombres"
  - "mise en forme des nombres (.NET Framework)"
  - "nombres (.NET Framework), chaînes de format numérique personnalisées"
  - "chaînes de format numériques (.NET Framework)"
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: d&#233;finir et utiliser des fournisseurs de format num&#233;rique personnalis&#233;s
Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] vous permet de contrôler la représentation sous forme de chaîne de valeurs numériques.  Les fonctionnalités suivantes sont prises en charge pour personnaliser le format des valeurs numériques :  
  
-   Chaînes de format numérique standard qui fournissent un jeu prédéfini de formats pour convertir des nombres dans leur représentation sous forme de chaîne.  Vous pouvez les utiliser avec toute méthode de mise en forme numérique, telle que <xref:System.Decimal.ToString%28System.String%29?displayProperty=fullName>, qui possède un paramètre `format`.  Pour plus d'informations, consultez [Chaînes de format numériques standard](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
-   Chaînes de format numérique personnalisées qui fournissent un jeu des symboles pouvant être combinés pour définir des spécificateurs de format numérique personnalisés.  Vous pouvez également les utiliser avec toute méthode de mise en forme numérique, telle que <xref:System.Decimal.ToString%28System.String%29?displayProperty=fullName>, qui possède un paramètre `format`.  Pour plus d'informations, consultez [Chaînes de format numériques personnalisées](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   Objets <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo> personnalisés qui définissent les symboles et modèles de format utilisés pour afficher les représentations sous forme de chaîne de valeurs numériques.  Vous pouvez les utiliser avec toute méthode de mise en forme numérique, telle que <xref:System.Int32.ToString%2A>, qui possède un paramètre `provider`.  En général, le paramètre `provider` est utilisé pour spécifier une mise en forme spécifique à la culture.  
  
 Dans certains cas \(par exemple, lorsqu'une application doit afficher un numéro de compte mis en forme, un numéro d'identification ou un code postal\), ces trois techniques ne sont pas appropriées.  Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] vous permet également de définir un objet de mise en forme qui n'est ni un objet <xref:System.Globalization.CultureInfo>, ni un objet <xref:System.Globalization.NumberFormatInfo> pour déterminer comment une valeur numérique est mise en forme.  Cette rubrique fournit des instructions pas à pas pour implémenter ce type d'objet et propose un exemple de mise en forme de numéros de téléphone.  
  
### Pour définir un fournisseur de format personnalisé  
  
1.  Définissez une classe qui implémente les interfaces <xref:System.IFormatProvider> et <xref:System.ICustomFormatter>.  
  
2.  Implémentez la méthode <xref:System.IFormatProvider.GetFormat%2A?displayProperty=fullName>.  <xref:System.IFormatProvider.GetFormat%2A> est une méthode de rappel que la méthode de mise en forme \(telle que la méthode [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> \) appelle pour extraire l'objet qui est réellement chargé de l'exécution de la mise en forme personnalisée.  En général, l'implémentation de <xref:System.IFormatProvider.GetFormat%2A> donne les résultats suivants :  
  
    1.  Détermine si l'objet <xref:System.Type> passé comme paramètre de méthode représente une interface <xref:System.ICustomFormatter>.  
  
    2.  Si le paramètre représente l'interface <xref:System.ICustomFormatter>, <xref:System.IFormatProvider.GetFormat%2A> retourne un objet qui implémente l'interface <xref:System.ICustomFormatter> chargée de fournir la mise en forme personnalisée.  En général, l'objet de mise en forme personnalisée se retourne lui\-même.  
  
    3.  Si le paramètre ne représente pas l'interface <xref:System.ICustomFormatter>, <xref:System.IFormatProvider.GetFormat%2A> retourne `null`.  
  
3.  Implémentez la méthode <xref:System.ICustomFormatter.Format%2A>.  Cette méthode appelée par [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> est chargée de retourner la représentation sous forme de chaîne d'un nombre.  L'implémentation de la méthode implique généralement ce qui suit :  
  
    1.  Si vous le souhaitez, assurez\-vous que la méthode est légitimement destinée à fournir des services de mise en forme en examinant le paramètre `provider`.  Pour mettre en forme des objets qui implémentent <xref:System.IFormatProvider> et <xref:System.ICustomFormatter>, vous devez tester l'égalité du paramètre `provider` avec l'objet de mise en forme actuel.  
  
    2.  Déterminez si l'objet de mise en forme doit prendre en charge des spécificateurs de format personnalisés. \(Par exemple, un « N » spécificateur de format peut m'indiquer qu'un numéro de téléphone depuis les États\-Unis doit être générée au format de NANP, et «I» peut afficher la sortie au format de la recommandation E.123 d'ITU\-T.\) Si les spécificateurs de format sont utilisés, la méthode doit gérer le spécificateur de format spécifique.  Il est passé à la méthode dans le paramètre `format`.  Si aucun spécificateur n'est présent, la valeur du paramètre `format` est <xref:System.String.Empty?displayProperty=fullName>.  
  
    3.  Récupérez la valeur numérique passée à la méthode comme paramètre `arg`.  Effectuez les opérations requises pour procéder à sa conversion sous forme de chaîne.  
  
    4.  Retournez la représentation sous forme de chaîne du paramètre `arg`.  
  
### Pour utiliser un objet de mise en forme numérique personnalisé  
  
1.  Créez une nouvelle instance de la classe de mise en forme personnalisée.  
  
2.  Appelez la méthode de mise en forme [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> en lui passant l'objet de mise en forme personnalisée, le spécificateur de mise en forme \(ou <xref:System.String.Empty?displayProperty=fullName> si aucun spécificateur n'est utilisé\) et la valeur numérique à mettre en forme.  
  
## Exemple  
 L'exemple suivant définit un fournisseur de formats numériques personnalisé nommé `TelephoneFormatter` qui convertit un nombre qui représente un numero de telephone a son format NANP ou E.123.  La méthode gère deux spécificateurs de format : "N" \(résultat affiché au format NANP\) et "I" \(résultat affiché au format E.123 international\).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Le fournisseur de format numérique personnalisé ne peut être utilisé qu'avec la méthode [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName>.  Les autres surcharges des méthodes de mise en forme numériques \(telles que `ToString`\) qui possèdent un paramètre de type <xref:System.IFormatProvider> passent toutes à l'implémentation <xref:System.IFormatProvider.GetFormat%2A?displayProperty=fullName> un objet <xref:System.Type> représentant le type <xref:System.Globalization.NumberFormatInfo>.  Normalement, la méthode doit retourner un objet <xref:System.Globalization.NumberFormatInfo>.  Si ce n'est pas le cas, le fournisseur de format numérique personnalisé est ignoré et l'objet <xref:System.Globalization.NumberFormatInfo> de la culture actuelle est utilisé à la place.  Dans l'exemple, si l'objet n'a pas été correctement passé à une méthode de mise en forme numérique, la méthode `TelephoneFormatter.GetFormat` examine le paramètre de méthode et retourne `null` s'il représente un type autre que <xref:System.ICustomFormatter>.  
  
 Si un fournisseur de format numérique personnalisé prend en charge un jeu de spécificateurs de format, n'oubliez pas de spécifier un comportement par défaut si aucun spécificateur de format n'est fourni dans l'élément de format utilisé dans l'appel de méthode [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName>.  Dans l'exemple, "N" est le spécificateur de format par défaut.  Ainsi, en fournissant un spécificateur de format explicite, vous pouvez convertir un nombre en un numéro de téléphone mis en forme.  L'exemple suivant illustre ce type d'appel de méthode.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 La conversion est également possible si aucun spécificateur de format n'est présent.  L'exemple suivant illustre ce type d'appel de méthode.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Si aucun spécificateur de format par défaut n'est défini, votre implémentation de la méthode <xref:System.ICustomFormatter.Format%2A?displayProperty=fullName> doit inclure du code tel que le suivant afin que le .NET Framework puisse fournir une mise en forme non prise en charge par votre code.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 Dans cet exemple, la méthode qui implémente <xref:System.ICustomFormatter.Format%2A?displayProperty=fullName> doit normalement servir de méthode de rappel pour la méthode [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName>.  Par conséquent, elle examine le paramètre `formatProvider` pour déterminer s'il contient une référence à l'objet `TelephoneFormatter` actuel.  Toutefois, la méthode peut également être appelée directement du code.  Dans ce cas, vous pouvez utiliser le paramètre `formatProvider` pour fournir un objet <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo> qui apporte des informations de mise en forme spécifiques à la culture.  
  
## Compilation du code  
 Compilez le code sur la ligne de commande à l'aide de csc.exe ou vb.exe.  Pour compiler le code dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], placez\-le dans un modèle de projet d'application console.  
  
## Voir aussi  
 [Exécution d'opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)