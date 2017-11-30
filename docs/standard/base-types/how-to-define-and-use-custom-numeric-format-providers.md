---
title: "Comment : définir et utiliser des fournisseurs de format numérique personnalisés"
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
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- custom numeric format strings
- numbers [.NET Framework], custom numeric format strings
- displaying date and time data
- format providers [.NET Framework]
- custom format strings
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e44a909eb92f0d9dfa21980a918a2d370dcf427
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Comment : définir et utiliser des fournisseurs de format numérique personnalisés
Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] vous donne un contrôle étendu sur la représentation sous forme de chaîne de valeurs numériques. Il prend en charge les fonctionnalités suivantes pour personnaliser le format des valeurs numériques :  
  
-   Chaînes de format numériques standard, qui fournissent un ensemble prédéfini de formats pour convertir des nombres dans leur représentation sous forme de chaîne. Vous pouvez les utiliser avec n’importe quel numérique mise en forme de méthode, telles que <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, qui a un `format` paramètre. Pour plus d’informations, consultez [des chaînes de Format numériques Standard](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
-   Chaînes de format numériques personnalisées, qui fournissent un ensemble de symboles pouvant être combinés pour définir des spécificateurs de format numériques personnalisés. Ils peuvent également être utilisés avec toute numérique mise en forme de méthode, telles que <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, qui a un `format` paramètre. Pour plus d’informations, consultez [les chaînes de Format numériques personnalisées](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   Personnalisé <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo> objets qui définissent les symboles et les modèles utilisés pour afficher les représentations sous forme de chaîne de valeurs numériques de format. Vous pouvez les utiliser avec n’importe quel numérique mise en forme de méthode, telles que <xref:System.Int32.ToString%2A>, qui a un `provider` paramètre. En règle générale, le `provider` paramètre est utilisé pour spécifier la mise en forme propres à la culture.  
  
 Dans certains cas (par exemple, quand une application doit afficher un numéro de compte mis en forme, un numéro d’identification ou un code postal), ces trois techniques sont inappropriées. Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] vous permet également de définir un objet de mise en forme qui n’est ni un <xref:System.Globalization.CultureInfo> ni un <xref:System.Globalization.NumberFormatInfo> objet afin de déterminer la mise en forme une valeur numérique. Cette rubrique fournit des instructions détaillées pour l’implémentation de ce type d’objet et fournit un exemple qui met en forme les numéros de téléphone.  
  
### <a name="to-define-a-custom-format-provider"></a>Pour définir un fournisseur de format personnalisé  
  
1.  Définissez une classe qui implémente le <xref:System.IFormatProvider> et <xref:System.ICustomFormatter> interfaces.  
  
2.  Implémentez la méthode <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>. <xref:System.IFormatProvider.GetFormat%2A>est une méthode de rappel que la méthode de mise en forme (comme le <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> méthode) appelle pour récupérer l’objet qui est réellement chargé d’effectuer la mise en forme personnalisée. Une implémentation classique des <xref:System.IFormatProvider.GetFormat%2A> effectue les opérations suivantes :  
  
    1.  Détermine si le <xref:System.Type> objet passé en tant que méthode paramètre représente un <xref:System.ICustomFormatter> interface.  
  
    2.  Si le paramètre ne représente pas la <xref:System.ICustomFormatter> interface, <xref:System.IFormatProvider.GetFormat%2A> retourne un objet qui implémente le <xref:System.ICustomFormatter> interface qui est chargé de fournir la mise en forme personnalisée. En général, l’objet de mise en forme personnalisée retourne lui-même.  
  
    3.  Si le paramètre ne représente pas la <xref:System.ICustomFormatter> interface, <xref:System.IFormatProvider.GetFormat%2A> retourne `null`.  
  
3.  Implémentez la méthode <xref:System.ICustomFormatter.Format%2A>. Cette méthode est appelée par le <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> (méthode) et est chargée de retourner la représentation sous forme de chaîne d’un nombre. En général, l’implémentation de la méthode implique les étapes suivantes :  
  
    1.  Si vous le souhaitez, assurez-vous que la méthode est légitimement destinée à fournir des services de mise en forme en examinant le `provider` paramètre. Pour mettre en forme des objets qui implémentent les deux <xref:System.IFormatProvider> et <xref:System.ICustomFormatter>, vous devez tester le `provider` égalité avec l’objet en cours de mise en forme du paramètre.  
  
    2.  Déterminez si l’objet de mise en forme doit prendre en charge les spécificateurs de format personnalisés. (Par exemple, un spécificateur de format « N » peut indiquer qu’un numéro de téléphone américain doit être au format NANP, tandis qu’un spécificateur de format « I » peut indiquer une sortie au format ITU-T Recommandation E.123.) Si des spécificateurs de format sont utilisés, la méthode doit gérer le spécificateur de format spécifique. Il est passé à la méthode dans le `format` paramètre. Si aucun spécificateur n’est présent, la valeur de la `format` paramètre est <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3.  Récupérer la valeur numérique est passée à la méthode comme étant le `arg` paramètre. Effectuez toute opération requise pour le convertir en sa représentation sous forme de chaîne.  
  
    4.  Retourner la représentation sous forme de chaîne de le `arg` paramètre.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Pour utiliser un objet de mise en forme numérique personnalisé  
  
1.  Créez une instance de la classe de mise en forme personnalisée.  
  
2.  Appelez le <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> mise en forme de la méthode, en lui passant l’objet de mise en forme personnalisée, le spécificateur de mise en forme (ou <xref:System.String.Empty?displayProperty=nameWithType>, si un n’est pas utilisé) et la valeur numérique à mettre en forme.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit un fournisseur de format numérique personnalisé nommé `TelephoneFormatter` qui convertit un nombre représentant un numéro de téléphone aux États-Unis au format NANP ou E.123 correspondant. La méthode gère deux spécificateurs de format, « N » (qui génère le format NANP) et « I » (qui génère le format E.123 international).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 Le fournisseur de format numérique personnalisée peut être utilisé uniquement avec la <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> (méthode). Autres surcharges des méthodes de mise en forme numérique (tel que `ToString`) qui ont un paramètre de type <xref:System.IFormatProvider> passent toutes les <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implémentation un <xref:System.Type> objet qui représente le <xref:System.Globalization.NumberFormatInfo> type. En retour, normalement, la méthode pour retourner un <xref:System.Globalization.NumberFormatInfo> objet. Si elle n’est pas le cas, le fournisseur de format numérique personnalisée est ignoré et le <xref:System.Globalization.NumberFormatInfo> pour la culture actuelle est utilisée à la place de l’objet. Dans l’exemple, le `TelephoneFormatter.GetFormat` méthode gère le risque qu’il peut être passé inappropriée en une valeur numérique mise en forme de la méthode en examinant le paramètre de méthode et en retournant `null` s’il représente un type autre que <xref:System.ICustomFormatter>.  
  
 Si un fournisseur de format numérique personnalisée prend en charge un jeu de spécificateurs de format, vérifiez que vous fournissez un comportement par défaut si aucun spécificateur de format n’est fourni dans l’élément de format utilisé dans le <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> appel de méthode. Dans l’exemple, « N » est le spécificateur de format par défaut. Cela permet de convertir un nombre en un numéro de téléphone mis en forme en fournissant un spécificateur de format explicite. L’exemple suivant illustre un appel de méthode de ce type.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Mais il permet également la conversion si aucun spécificateur de format n’est présent. L’exemple suivant illustre un appel de méthode de ce type.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Si aucun spécificateur de format par défaut n’est défini, votre implémentation de la <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> méthodes doivent inclure le code semblable au suivant pour que .NET puissent fournir la mise en forme que votre code ne prend pas en charge.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 Dans le cas de cet exemple, la méthode qui implémente <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> est destiné à servir d’une méthode de rappel pour le <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> (méthode). Par conséquent, il examine les `formatProvider` paramètre pour déterminer si elle contient une référence à le `TelephoneFormatter` objet. Toutefois, la méthode peut également être appelée directement à partir du code. Dans ce cas, vous pouvez utiliser la `formatProvider` paramètre pour fournir un <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo> objet qui fournit des informations de mise en forme propres à la culture.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Compiler le code à la ligne de commande à l’aide de csc.exe ou vb.exe. Pour compiler le code dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], placez-le dans un modèle de projet application console.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)
