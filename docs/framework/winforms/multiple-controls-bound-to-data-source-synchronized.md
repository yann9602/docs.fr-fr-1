---
title: "Comment&#160;: s&#39;assurer que plusieurs contr&#244;les li&#233;s &#224; la m&#234;me source de donn&#233;es restent synchronis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles (Windows Forms), lier plusieurs"
  - "contrôles (Windows Forms), synchroniser avec une source de données"
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: s&#39;assurer que plusieurs contr&#244;les li&#233;s &#224; la m&#234;me source de donn&#233;es restent synchronis&#233;s
Souvent, lors de l'utilisation de la liaison de données dans les Windows Forms, plusieurs contrôles sont liés à la même source de données.  Dans certains cas, il peut être nécessaire d'effectuer des étapes supplémentaires pour garantir que les propriétés liées des contrôles restent synchronisées les unes avec les autres et avec la source de données.  Ces étapes sont nécessaires dans deux situations :  
  
-   Si la source de données n'implémente pas <xref:System.ComponentModel.IBindingList> et génère par conséquent des événements <xref:System.ComponentModel.IBindingList.ListChanged> de type <xref:System.ComponentModel.ListChangedType>.  
  
-   Si la source de données implémente <xref:System.ComponentModel.IEditableObject>.  
  
 Dans le premier cas, vous pouvez utiliser un <xref:System.Windows.Forms.BindingSource> pour lier la source de données aux contrôles.  Dans le second cas, vous utilisez un <xref:System.Windows.Forms.BindingSource>, gérez l'événement <xref:System.Windows.Forms.BindingSource.BindingComplete> et appelez <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> sur la <xref:System.Windows.Forms.BindingManagerBase> associée.  
  
## Exemple  
 L'exemple de code suivant montre comment lier trois contrôles, deux contrôles de zone de texte et un contrôle <xref:System.Windows.Forms.DataGridView> à la même colonne dans un <xref:System.Data.DataSet> à l'aide d'un composant <xref:System.Windows.Forms.BindingSource>.  Cet exemple montre comment gérer l'événement <xref:System.Windows.Forms.BindingSource.BindingComplete> et garantir que, lorsque la valeur texte d'une zone de texte est modifiée, la zone de texte supplémentaire et le contrôle <xref:System.Windows.Forms.DataGridView> sont mis à jour avec la valeur correcte.  
  
 L'exemple utilise un <xref:System.Windows.Forms.BindingSource> pour lier la source de données et les contrôles.  Vous pouvez également lier directement les contrôles à la source de données et récupérer la <xref:System.Windows.Forms.BindingManagerBase> pour la liaison à partir d'un <xref:System.Windows.Forms.Control.BindingContext%2A> du formulaire, puis gérer l'événement <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> pour la <xref:System.Windows.Forms.BindingManagerBase>.  Pour obtenir un exemple de cette procédure, consultez la page d'aide sur l'événement <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> de <xref:System.Windows.Forms.BindingManagerBase>.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## Compilation du code  
  
-   Cet exemple de code nécessite les actions ou les éléments suivants :  
  
-   Références aux assemblys <xref:System>, <xref:System.Windows.Forms> et <xref:System.Drawing>.  
  
-   Formulaire avec l'événement <xref:System.Windows.Forms.Form.Load> géré et appel à la méthode `InitializeControlsAndDataSource` dans l'exemple du gestionnaire d'événements <xref:System.Windows.Forms.Form.Load> du formulaire.  
  
## Voir aussi  
 [Comment : partager des données liées entre des formulaires à l'aide du composant BindingSource](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)   
 [Notification de modifications dans la liaison de données Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [Interfaces participant à la liaison de données](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)   
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)