---
title: "Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms"
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
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 310f90c7b95d74f1fab8ab2e9871d6c1a0937c52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms
Vous pouvez exposer le tri et filtrage de <xref:System.Windows.Forms.BindingSource> contrôler via le <xref:System.Windows.Forms.BindingSource.Sort%2A> et <xref:System.Windows.Forms.BindingSource.Filter%2A> propriétés. Vous pouvez appliquer un tri simple lorsque la source de données sous-jacente est une <xref:System.ComponentModel.IBindingList>, et vous pouvez appliquer le filtrage et tri avancé lorsque la source de données est un <xref:System.ComponentModel.IBindingListView>. Le <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété requiert standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntaxe : une chaîne représentant le nom d’une colonne de données dans la source de données suivie `ASC` ou `DESC` pour indiquer si la liste doit être triée dans l’ordre croissant ou décroissant. Vous pouvez définir le tri avancé ou un tri sur plusieurs colonnes en séparant chaque colonne avec un séparateur de virgule. Le <xref:System.Windows.Forms.BindingSource.Filter%2A> propriété prend une expression de chaîne.  
  
> [!NOTE]
>  Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Pour filtrer les données avec le composant BindingSource  
  
-   Définir le <xref:System.Windows.Forms.BindingSource.Filter%2A> propriété expression que vous souhaitez utiliser.  
  
     Dans l’exemple de code suivant, l’expression est un nom de colonne suivi par la valeur souhaitée pour la colonne.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Pour trier les données avec le composant BindingSource  
  
1.  Définir le <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété le nom de colonne que vous souhaitez suivi `ASC` ou `DESC` pour indiquer l’ordre croissant ou décroissant.  
  
2.  Séparez plusieurs colonnes par une virgule.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant charge des données à partir de la table Customers de la base de données Northwind dans un <xref:System.Windows.Forms.DataGridView> contrôler, puis filtre et trie les données affichées.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour exécuter cet exemple, collez le code dans un formulaire contenant un <xref:System.Windows.Forms.BindingSource> nommé `BindingSource1` et un <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1`. Gérer les <xref:System.Windows.Forms.Form.Load> événement pour le formulaire et appelez `InitializeSortedFilteredBindingSource` dans la méthode de gestionnaire d’événements de charge.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [Guide pratique pour installer des exemples de bases de données](http://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [BindingSource, composant](../../../../docs/framework/winforms/controls/bindingsource-component.md)
