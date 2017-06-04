---
title: "Comment&#160;: g&#233;n&#233;rer des notifications de modifications &#224; l&#39;aide d&#39;un BindingSource et de l&#39;interface INotifyPropertyChanged | Microsoft Docs"
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
  - "BindingSource (composant Windows Forms), et IPropertyChange"
  - "BindingSource (composant Windows Forms), exemples"
  - "notifications de modifications"
  - "notifications de modifications, déclencher"
  - "sources de données, détecter des modifications"
  - "exemples (Windows Forms), BindingSource (composant)"
  - "INotifyPropertyChanged (interface), utiliser avec BindingSource"
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: g&#233;n&#233;rer des notifications de modifications &#224; l&#39;aide d&#39;un BindingSource et de l&#39;interface INotifyPropertyChanged
Le composant <xref:System.Windows.Forms.BindingSource> détecte automatiquement les modifications apportées à une source de données quand le type contenu dans la source de données implémente l'interface <xref:System.ComponentModel.INotifyPropertyChanged> et déclenche des événements <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> quand une valeur de propriété est modifiée.  Cela est utile, car les contrôles liés à <xref:System.Windows.Forms.BindingSource> sont alors automatiquement mis à jour en cas de modification des valeurs de la source de données.  
  
> [!NOTE]
>  Si votre source de données implémente <xref:System.ComponentModel.INotifyPropertyChanged> et que vous exécutez des opérations asynchrones, vous ne devez pas modifier la source de données sur un thread d'arrière\-plan.  Au lieu de cela, vous devez lire les données sur un thread d'arrière\-plan et les fusionner dans une liste sur le thread d'interface utilisateur.  
  
## Exemple  
 L'exemple de code suivant illustre une implémentation simple de l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.  Il montre également comment <xref:System.Windows.Forms.BindingSource> transmet automatiquement une modification de source de données à un contrôle lié quand <xref:System.Windows.Forms.BindingSource> est lié à une liste du type <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Si vous utilisez l'attribut `CallerMemberName`, les appels à la méthode `NotifyPropertyChanged` ne doivent pas obligatoirement spécifier le nom de la propriété comme argument de chaîne.  Pour plus d'informations, consultez [Informations relatives à l'appelant](../Topic/Caller%20Information%20\(C%23%20and%20Visual%20Basic\).md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.ComponentModel.INotifyPropertyChanged>   
 [Composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [Comment : générer des notifications de modifications à l'aide de la méthode ResetItem de BindingSource](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)