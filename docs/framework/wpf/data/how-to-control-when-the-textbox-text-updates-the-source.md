---
title: "Comment&#160;: contr&#244;ler quand le texte TextBox met &#224; jour la source | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "liaison de données, planification de mises à jour de source"
  - "mises à jour de source, planification de"
  - "planification de mises à jour de source"
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: contr&#244;ler quand le texte TextBox met &#224; jour la source
Cette rubrique décrit comment utiliser la propriété <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> pour contrôler le minutage des mises à jour de la [source de liaison](GTMT).  Le rubrique utilise le contrôle <xref:System.Windows.Controls.TextBox> comme exemple.  
  
## Exemple  
 La propriété <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> a une valeur par défaut <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de <xref:System.Windows.Data.UpdateSourceTrigger>.  Cela signifie que si un application a une <xref:System.Windows.Controls.TextBox> avec une propriété <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> liée aux données, le texte que vous saisissez dans la <xref:System.Windows.Controls.TextBox> ne met pas à jour la source jusqu'à ce que la <xref:System.Windows.Controls.TextBox> perde le focus \(par exemple, lorsque vous cliquez en dehors de la <xref:System.Windows.Controls.TextBox>\).  
  
 Si vous souhaitez que la source soit mise à jour pendant votre saisie, définissez le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de la liaison <xref:System.Windows.Data.UpdateSourceTrigger>.  Dans l'exemple suivant, les propriétés `Text` de la <xref:System.Windows.Controls.TextBox> et du <xref:System.Windows.Controls.TextBlock> sont liées à la même propriété source.  La propriété <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de la liaison <xref:System.Windows.Controls.TextBox> a la valeur <xref:System.Windows.Data.UpdateSourceTrigger>.  
  
 [!code-xml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 Par conséquent, le <xref:System.Windows.Controls.TextBlock> affiche le même mot \(car la source change\) lorsque l'utilisateur entre le texte dans la <xref:System.Windows.Controls.TextBox>, comme illustré dans la capture d'écran suivante de l'exemple :  
  
 ![Capture d'écran : exemple de liaison de données simple](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 Si vous avez un formulaire de boîte de dialogue ou pouvant être modifié par l'utilisateur et que vous souhaitez exécuter les mises à jour de la source jusqu'à ce que l'utilisateur ait fini de modifier les champs et ait cliqué sur « OK », vous pouvez définir la valeur <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de vos liaisons sur <xref:System.Windows.Data.UpdateSourceTrigger>, comme indiqué dans l'exemple suivant :  
  
 [!code-xml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Lorsque vous définissez la valeur <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> sur <xref:System.Windows.Data.UpdateSourceTrigger>, la valeur source change uniquement lorsque l'application appelle la méthode <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>.  L'exemple suivant montre comment appeler <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> pour `itemNameTextBox` :  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  Vous pouvez utiliser la même technique pour les propriétés d'autres contrôles, mais gardez à l'esprit que la plupart des autres propriétés ont une valeur <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> par défaut de <xref:System.Windows.Data.UpdateSourceTrigger>.  Pour plus d'informations, consultez la page de propriétés <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
> [!NOTE]
>  La propriété <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> traite les mises à jour de la source et ne concerne donc que les liaisons <xref:System.Windows.Data.BindingMode> ou <xref:System.Windows.Data.BindingMode>.  Pour les liaisons <xref:System.Windows.Data.BindingMode> et <xref:System.Windows.Data.BindingMode>, l'objet source doit fournir des notifications de modification de la propriété.  Pour plus d'informations, consultez les exemples figurant dans cette rubrique.  Vous pouvez aussi consulter [Implémenter la notification des modifications de propriétés](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
## Voir aussi  
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)