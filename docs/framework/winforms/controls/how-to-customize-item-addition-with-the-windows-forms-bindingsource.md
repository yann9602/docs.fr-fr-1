---
title: "Comment&#160;: personnaliser l&#39;ajout d&#39;&#233;l&#233;ments avec le composant BindingSource Windows Forms | Microsoft Docs"
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
  - "contrôles [Windows Forms], création d’éléments"
  - "composant BindingSource [Windows Forms], personnalisation de l’ajout d’élément avec"
  - "exemples [Windows Forms], composant BindingSource"
  - "composant BindingSource [Windows Forms], exemples"
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: personnaliser l&#39;ajout d&#39;&#233;l&#233;ments avec le composant BindingSource Windows Forms
Quand vous utilisez un composant <xref:System.Windows.Forms.BindingSource> pour lier un contrôle Windows Forms à une source de données, vous pouvez être contraint de personnaliser la création de nouveaux éléments. Le composant <xref:System.Windows.Forms.BindingSource> simplifie cette personnalisation en fournissant l'événement <xref:System.Windows.Forms.BindingSource.AddingNew>, qui est généralement déclenché quand le contrôle lié doit créer un élément. Votre gestionnaire d'événements peut fournir tout comportement personnalisé nécessaire \(par exemple, appeler une méthode sur un service web ou obtenir un nouvel objet à partir d'une fabrique de classe\).  
  
> [!NOTE]
>  Quand un élément est ajouté en gérant l'événement <xref:System.Windows.Forms.BindingSource.AddingNew>, cet ajout ne peut pas être annulé.  
  
## Exemple  
 L'exemple suivant montre comment lier un contrôle <xref:System.Windows.Forms.DataGridView> à une fabrique de classe à l'aide d'un composant <xref:System.Windows.Forms.BindingSource>. Quand l'utilisateur clique sur la nouvelle ligne du contrôle <xref:System.Windows.Forms.DataGridView>, l'événement <xref:System.Windows.Forms.BindingSource.AddingNew> est déclenché. Le gestionnaire d'événements crée un objet `DemoCustomer`, qui est affecté à la propriété <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=fullName>. Cela provoque l'ajout du nouvel objet `DemoCustomer` à la liste du composant <xref:System.Windows.Forms.BindingSource> et son affichage sur la nouvelle ligne du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande associée à [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou à [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez les pages [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également la page [Comment : compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.BindingNavigator>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [Composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)