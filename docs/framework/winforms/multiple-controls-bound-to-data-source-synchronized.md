---
title: "Comment : s’assurer que plusieurs contrôles liés à la même source de données restent synchronisés"
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
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 227ad36e87c3deceb7fefe3cd19013fc8e76c686
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>Comment : s’assurer que plusieurs contrôles liés à la même source de données restent synchronisés
Souvent, lorsque vous travaillez avec la liaison de données dans les Windows Forms, plusieurs contrôles sont liés à la même source de données. Dans certains cas, il peut être nécessaire de prendre des mesures supplémentaires pour garantir que les propriétés liées des contrôles restent synchronisées avec eux et à la source de données. Ces étapes sont nécessaires dans deux situations :  
  
-   Si la source de données n’implémente pas <xref:System.ComponentModel.IBindingList>et ainsi générer <xref:System.ComponentModel.IBindingList.ListChanged> événements de type <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
-   Si la source de données implémente <xref:System.ComponentModel.IEditableObject>.  
  
 Dans le premier cas, vous pouvez utiliser un <xref:System.Windows.Forms.BindingSource> pour lier la source de données aux contrôles. Dans ce cas, vous utilisez un <xref:System.Windows.Forms.BindingSource> et gérer le <xref:System.Windows.Forms.BindingSource.BindingComplete> événements et les appels <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> sur associé <xref:System.Windows.Forms.BindingManagerBase>.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment lier des contrôles de trois : deux contrôles de zone de texte et un <xref:System.Windows.Forms.DataGridView> contrôle, à la même colonne dans un <xref:System.Data.DataSet> à l’aide un <xref:System.Windows.Forms.BindingSource> composant. Cet exemple montre comment gérer les <xref:System.Windows.Forms.BindingSource.BindingComplete> événements et vérifiez que, quand la valeur de texte d’une zone de texte est modifiée, la zone de texte supplémentaires et <xref:System.Windows.Forms.DataGridView> contrôle sont mis à jour avec la valeur correcte.  
  
 L’exemple utilise un <xref:System.Windows.Forms.BindingSource> pour lier la source de données et les contrôles. Ou bien, vous pouvez lier les contrôles directement à la source de données et récupérer le <xref:System.Windows.Forms.BindingManagerBase> pour la liaison à partir du formulaire <xref:System.Windows.Forms.Control.BindingContext%2A> , puis gérer la <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> événement pour le <xref:System.Windows.Forms.BindingManagerBase>. Pour obtenir un exemple de procédure à suivre, consultez la page d’aide la <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> l’événement de <xref:System.Windows.Forms.BindingManagerBase>.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Cet exemple de code nécessite  
  
-   des références aux assemblys <xref:System>, <xref:System.Windows.Forms> et <xref:System.Drawing>.  
  
-   Un formulaire avec le <xref:System.Windows.Forms.Form.Load> événement géré et un appel à la `InitializeControlsAndDataSource` méthode dans l’exemple à partir du formulaire <xref:System.Windows.Forms.Form.Load> Gestionnaire d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : partager des données liées entre des formulaires à l'aide du composant BindingSource](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [Notification de modifications dans la liaison de données Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Interfaces participant à la liaison de données](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
