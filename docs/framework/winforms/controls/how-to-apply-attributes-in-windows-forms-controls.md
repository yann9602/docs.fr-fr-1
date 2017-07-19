---
title: "Comment&#160;: appliquer des attributs dans les contr&#244;les Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "attributs (Windows Forms), appliquer"
  - "contrôles (Windows Forms), appliquer des attributs"
  - "contrôles Windows Forms, appliquer des attributs"
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: appliquer des attributs dans les contr&#244;les Windows Forms
Pour développer des composants et des contrôles qui interagissent correctement avec l'environnement de design et s'exécutent correctement au moment de l'exécution, vous devez appliquer correctement des attributs aux classes et aux membres.  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser plusieurs attributs sur un contrôle personnalisé.  Le contrôle montre une fonction d'enregistrement simple.  Lorsque le contrôle est lié à une source de données, il affiche les valeurs envoyées par la source de données dans un contrôle <xref:System.Windows.Forms.DataGridView>.  Si une valeur dépasse la valeur spécifiée par la propriété `Threshold`, un événement `ThresholdExceeded` est déclenché.  
  
 Le `AttributesDemoControl` enregistre des valeurs avec une classe `LogEntry`.  La classe `LogEntry` est une classe de modèle, ce qui signifie qu'elle est paramétrée sur le type qu'elle enregistre.  Par exemple, si le `AttributesDemoControl` enregistre des valeurs de type `float`, chaque instance de `LogEntry` est déclarée et est utilisée comme suit.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  Dans la mesure où `LogEntry` est paramétré par un type arbitraire, il doit utiliser la réflexion pour fonctionner sur le type de paramètre.  Pour que la fonctionnalité de seuil fonctionne, le type de paramètre `T` doit implémenter l'interface <xref:System.IComparable>.  
  
 Le formulaire qui héberge le `AttributesDemoControl` interroge périodiquement un compteur de performance.  Chaque valeur est empaquetée dans un `LogEntry` du type approprié et ajoutée au <xref:System.Windows.Forms.BindingSource> du formulaire.  Le `AttributesDemoControl` reçoit la valeur via sa liaison de données et affiche la valeur dans un contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 Le premier exemple de code est l'implémentation `AttributesDemoControl`.  Le deuxième exemple de code montre un formulaire qui utilise le `AttributesDemoControl`.  
  
## Attributs de niveau classe  
 Certains attributs sont appliqués au niveau de la classe.  L'exemple de code suivant affiche les attributs qui sont appliqués communément à un contrôle Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### Attribut TypeConverter  
 <xref:System.ComponentModel.TypeConverterAttribute> est un autre attribut de niveau classe communément utilisé.  L'exemple de code suivant montre comment l'utiliser pour la classe `LogEntry`.  Cet exemple illustre également une implémentation d'un <xref:System.ComponentModel.TypeConverter> pour le type `LogEntry`, appelé `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## Attributs de niveau membre  
 Certains attributs sont appliqués au niveau du membre.  Les exemples de code suivants montrent quelques attributs qui sont appliqués communément aux propriétés de contrôles Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### Attribut AmbientValue  
 L'exemple suivant montre le <xref:System.ComponentModel.AmbientValueAttribute> et affiche un code qui prend en charge son interaction avec l'environnement de design.  Cette interaction est appelée *ambiance*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### Attributs Databinding  
 Les exemples suivants montrent une implémentation de liaison de données complexe.  Le <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> de niveau classe, indiqué précédemment, spécifie les propriétés `DataSource` et `DataMember` à utiliser pour la liaison des données.  Le <xref:System.ComponentModel.AttributeProviderAttribute> spécifie le type avec lequel la propriété `DataSource` créera une liaison.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## Compilation du code  
  
-   Le formulaire qui héberge le `AttributesDemoControl` requiert une référence à l'assembly `AttributesDemoControl` pour générer.  
  
## Voir aussi  
 <xref:System.IComparable>   
 <xref:System.Windows.Forms.DataGridView>   
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)   
 [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](../Topic/How%20to:%20Serialize%20Collections%20of%20Standard%20Types%20with%20the%20DesignerSerializationVisibilityAttribute.md)