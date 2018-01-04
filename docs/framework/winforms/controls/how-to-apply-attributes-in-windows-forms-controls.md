---
title: "Comment : appliquer des attributs dans les contrôles Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e4d5bfb445ce6ed37ad1dc63d92fde833ac9870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Comment : appliquer des attributs dans les contrôles Windows Forms
Pour développer des composants et des contrôles qui interagissent correctement avec l’environnement de conception et s’exécutent correctement au moment de l’exécution, vous devez appliquer correctement des attributs aux classes et membres.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l’utilisation de plusieurs attributs sur un contrôle personnalisé. Le contrôle montre une fonction d’enregistrement simple. Lorsque le contrôle est lié à une source de données, il affiche les valeurs envoyées par la source de données dans un <xref:System.Windows.Forms.DataGridView> contrôle. Si une valeur dépasse la valeur spécifiée par la `Threshold` propriété, un `ThresholdExceeded` événement est déclenché.  
  
 Le `AttributesDemoControl` enregistre des valeurs avec une `LogEntry` classe. Le `LogEntry` est une classe de modèle, ce qui signifie qu’elle est paramétrée sur le type auquel il se connecte. Par exemple, si le `AttributesDemoControl` enregistre des valeurs de type `float`, chaque `LogEntry` instance est déclarée et utilisée comme suit.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  Étant donné que `LogEntry` est paramétré par un type arbitraire, il doit utiliser la réflexion pour fonctionner sur le type de paramètre. Pour la fonctionnalité de seuil fonctionne, le type de paramètre `T` doit implémenter la <xref:System.IComparable> interface.  
  
 Le formulaire qui héberge le `AttributesDemoControl` interroge périodiquement un compteur de performances. Chaque valeur est empaquetée dans un `LogEntry` du type approprié et ajoutée à du formulaire <xref:System.Windows.Forms.BindingSource>. Le `AttributesDemoControl` reçoit la valeur via sa liaison de données et affiche la valeur dans un <xref:System.Windows.Forms.DataGridView> contrôle.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 Le premier exemple de code est le `AttributesDemoControl` implémentation. Le deuxième exemple de code montre un formulaire qui utilise le `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Attributs de niveau classe  
 Certains attributs sont appliqués au niveau de la classe. L’exemple de code suivant affiche les attributs qui sont généralement appliquées à un contrôle Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>Attribut TypeConverter  
 <xref:System.ComponentModel.TypeConverterAttribute>est un autre attribut de niveau classe couramment utilisé. L’exemple de code suivant illustre son utilisation pour la `LogEntry` classe. Cet exemple illustre également une implémentation d’un <xref:System.ComponentModel.TypeConverter> pour le `LogEntry` type, appelé `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Attributs au niveau de membre  
 Certains attributs sont appliqués au niveau du membre. Les exemples de code suivants montrent certains attributs qui sont couramment appliqués aux propriétés des contrôles Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>Attribut de AmbientValue  
 L’exemple suivant illustre la <xref:System.ComponentModel.AmbientValueAttribute> et affiche un code qui prend en charge son interaction avec l’environnement de conception. Cette interaction est appelée *ambiance*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Attributs de liaison de données  
 Les exemples suivants montrent une implémentation de la liaison de données complexe. Niveau de la classe <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, comme illustré précédemment, spécifie la `DataSource` et `DataMember` propriétés à utiliser pour la liaison de données. Le <xref:System.ComponentModel.AttributeProviderAttribute> Spécifie le type auquel la `DataSource` propriété crée une liaison.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Le formulaire qui héberge le `AttributesDemoControl` requiert une référence à la `AttributesDemoControl` assembly afin de générer.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [Comment : sérialiser des Collections de Types Standard avec DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
