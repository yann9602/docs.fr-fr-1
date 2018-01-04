---
title: "Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e349a33c90d08606da09ebdf32de6dedb8d6a52c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms
Lorsque vous utilisez un <xref:System.Windows.Forms.DataGridView> pour la modification des données dans votre application, vous souhaiterez souvent donner aux utilisateurs la possibilité d’ajouter de nouvelles lignes de données dans le magasin de données. Le <xref:System.Windows.Forms.DataGridView> contrôle prend en charge cette fonctionnalité en fournissant une ligne pour les nouveaux enregistrements, qui est toujours affichée comme la dernière ligne. Il est marqué avec un astérisque (*) dans son en-tête de ligne. Les sections suivantes décrivent certains éléments que doit prendre en compte lorsque vous programmez avec la ligne pour les nouveaux enregistrements est activé.  
  
## <a name="displaying-the-row-for-new-records"></a>Affichage de la ligne pour les nouveaux enregistrements  
 Utilisez le <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriété pour indiquer si la ligne pour les nouveaux enregistrements est affichée. La valeur par défaut de cette propriété est `true`.  
  
 Pour les données liée au cas, la ligne pour les nouveaux enregistrements s’affichera si le <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriété du contrôle et la <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> propriété de la source de données sont toutes deux `true`. Si une est `false` la ligne n’est pas affichée.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Remplissage de la ligne pour les nouveaux enregistrements avec des données par défaut  
 Lorsque l’utilisateur sélectionne la ligne pour les nouveaux enregistrements en tant que la ligne actuelle, le <xref:System.Windows.Forms.DataGridView> incrémente le <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> événement.  
  
 Cet événement fournit l’accès à la nouvelle <xref:System.Windows.Forms.DataGridViewRow> et vous permet de remplir la nouvelle ligne avec les données par défaut. Pour plus d’informations, consultez [Comment : spécifier les valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>La Collection de lignes  
 La ligne pour les nouveaux enregistrements est contenue dans le <xref:System.Windows.Forms.DataGridView> du contrôle <xref:System.Windows.Forms.DataGridView.Rows%2A> collection mais se comporte différemment dans les deux points de vue :  
  
-   Impossible de supprimer la ligne pour les nouveaux enregistrements de la <xref:System.Windows.Forms.DataGridView.Rows%2A> collection par programme. Un <xref:System.InvalidOperationException> est levée si cette opération est tentée. L’utilisateur ne peut également ne peut pas supprimer la ligne pour les nouveaux enregistrements. Le <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> méthode ne supprime pas cette ligne à partir de la <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.  
  
-   Aucune ligne ne peut être ajouté après la ligne pour les nouveaux enregistrements. Un <xref:System.InvalidOperationException> est levée si cette opération est tentée. Par conséquent, la ligne pour les nouveaux enregistrements est toujours la dernière ligne dans le <xref:System.Windows.Forms.DataGridView> contrôle. Les méthodes sur <xref:System.Windows.Forms.DataGridViewRowCollection> qui ajoute des lignes —<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, et <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, appellent toutes les méthodes d’insertion en interne lorsque la ligne pour les nouveaux enregistrements est présente.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Personnalisation visuelle de la ligne pour les nouveaux enregistrements  
 Lorsque la ligne pour les nouveaux enregistrements est créée, il est basé sur la ligne spécifiée par le <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> propriété. Les styles de cellules qui ne sont pas spécifiés pour cette ligne sont hérités d’autres propriétés. Pour plus d’informations sur l’héritage de style de cellule, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Les valeurs initiales affichées par les cellules dans la ligne pour les nouveaux enregistrements sont récupérées à partir de chaque cellule <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> propriété. Pour les cellules de type <xref:System.Windows.Forms.DataGridViewImageCell>, cette propriété retourne un espace réservé d’image. Sinon, cette propriété retourne `null`. Vous pouvez substituer cette propriété pour retourner une valeur personnalisée. Toutefois, ces valeurs initiales peuvent être remplacées par un <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> Gestionnaire d’événements lorsque le focus passe à la ligne pour les nouveaux enregistrements.  
  
 Les icônes standards pour l’en-tête de cette ligne, qui sont une flèche ou un astérisque, ne sont pas exposées publiquement. Si vous souhaitez personnaliser les icônes, vous devrez créer un personnalisé <xref:System.Windows.Forms.DataGridViewRowHeaderCell> classe.  
  
 Les icônes standard utilisent le <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> propriété de le <xref:System.Windows.Forms.DataGridViewCellStyle> en cours d’utilisation par la cellule d’en-tête de ligne. Les icônes standards ne sont pas rendus si il n’est pas suffisamment d’espace pour les afficher complètement.  
  
 Si une valeur de chaîne est défini par la cellule d’en-tête de ligne, et s’il n’est pas assez de place pour le texte et l’icône, l’icône est d’abord supprimé.  
  
## <a name="sorting"></a>Tri  
 En mode indépendant, les nouveaux enregistrements seront toujours être ajoutés à la fin de la <xref:System.Windows.Forms.DataGridView> même si l’utilisateur a trié le contenu de la <xref:System.Windows.Forms.DataGridView>. L’utilisateur doit appliquer encore le tri pour trier la ligne à la position correcte ; Ce comportement est semblable à celui de la <xref:System.Windows.Forms.ListView> contrôle.  
  
 Dans les données modes dépendants et virtuels, le comportement d’insertion lorsqu’un tri est appliqué sera dépendants de l’implémentation du modèle de données. Pour [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], la ligne est immédiatement placée à la position correcte.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Autres remarques sur la ligne pour les nouveaux enregistrements  
 Vous ne pouvez pas définir le <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> propriété de cette ligne à `false`. Un <xref:System.InvalidOperationException> est levée si cette opération est tentée.  
  
 La ligne pour les nouveaux enregistrements est toujours créée dans l’état non sélectionné.  
  
## <a name="virtual-mode"></a>Mode virtuel  
 Si vous implémentez le mode virtuel, vous devez effectuer le suivi d’une ligne pour les nouveaux enregistrements est nécessaire dans le modèle de données et quand annuler l’ajout de la ligne. L’implémentation exacte de cette fonctionnalité dépend de l’implémentation du modèle de données et sa sémantique de transaction, par exemple, si la validation étendue est au niveau de la cellule ou la ligne. Pour plus d’informations, consultez [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour spécifier des valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)
