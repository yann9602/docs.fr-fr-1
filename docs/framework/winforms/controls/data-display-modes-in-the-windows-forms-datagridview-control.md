---
title: "Modes d'affichage des données dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc7fd3d3012053d8c40edf5fdce8af45c62c98c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Modes d'affichage des données dans le contrôle DataGridView Windows Forms
Le <xref:System.Windows.Forms.DataGridView> contrôle peut afficher des données en trois modes distincts : dépendant, indépendant et virtuel. Choisissez le mode plus approprié en fonction de vos besoins.  
  
## <a name="unbound"></a>Indépendant  
 Le mode indépendant est approprié pour l’affichage de petites quantités de données que vous gérez par programme. Ne pas attacher le <xref:System.Windows.Forms.DataGridView> contrôle directement à une source de données comme en mode dépendant. Au lieu de cela, vous devez remplir le contrôle vous-même, généralement à l’aide de la <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> (méthode).  
  
 Le mode indépendant peut être particulièrement utile pour les données statiques en lecture seule, ou lorsque vous souhaitez fournir votre propre code qui interagit avec un magasin de données externe. Lorsque vous souhaitez que vos utilisateurs d’interagir avec une source de données externe, toutefois, vous utiliserez en général le mode dépendant.  
  
 Pour obtenir un exemple qui utilise en lecture seule indépendant <xref:System.Windows.Forms.DataGridView>, consultez [Comment : créer un contrôle de DataGridView Windows Forms indépendant](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>Lié  
 Mode dépendant convient pour la gestion des données à l’aide d’une interaction automatique avec le magasin de données. Vous pouvez attacher le <xref:System.Windows.Forms.DataGridView> contrôle directement à sa source de données en définissant le <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriété. Lorsque le contrôle est lié aux données, les lignes de données sont envoyées et extraites sans nécessiter une gestion explicite de votre part. Lorsque le <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> propriété est `true`, chaque colonne dans votre source de données entraîne une colonne correspondante doit être créé dans le contrôle. Si vous préférez créer vos propres colonnes, vous pouvez définir cette propriété `false` et utiliser le <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> propriété à lier chaque colonne lorsque vous le configurez. Cela est utile lorsque vous souhaitez utiliser un type de colonne autre que les types qui sont générés par défaut. Pour plus d’informations, consultez [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).  
  
 Pour obtenir un exemple qui utilise une limite <xref:System.Windows.Forms.DataGridView> du contrôle, consultez [procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Vous pouvez également ajouter des colonnes indépendantes à un <xref:System.Windows.Forms.DataGridView> contrôle en mode dépendant. Cela est utile lorsque vous souhaitez afficher une colonne de boutons ou des liens qui permettent aux utilisateurs d’effectuer des actions sur des lignes spécifiques. Il est également utile afficher les colonnes avec des valeurs calculées à partir de colonnes liées. Vous pouvez remplir les valeurs de cellule pour les colonnes calculées dans un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CellFormatting> événement. Si vous utilisez un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> comme source de données, cependant, vous souhaiterez peut-être utiliser le <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> propriété pour créer une colonne calculée à la place. Dans ce cas, le <xref:System.Windows.Forms.DataGridView> contrôle traitera la colonne calculée comme toute autre colonne dans la source de données.  
  
 Tri par colonnes indépendantes en mode dépendant n’est pas pris en charge. Si vous créez une colonne indépendante en mode dépendant qui contient des valeurs modifiables par l’utilisateur, vous devez implémenter le mode virtuel pour maintenir ces valeurs lorsque le contrôle est trié selon une colonne dépendante.  
  
## <a name="virtual"></a>Virtuel  
 Avec le mode virtuel, vous pouvez implémenter vos propres opérations de gestion de données. Cela est nécessaire pour conserver les valeurs des colonnes indépendantes en mode dépendant lorsque le contrôle est trié par colonnes dépendantes. La principale utilisation du mode virtuel est toutefois, pour optimiser les performances lors de l’interaction avec de grandes quantités de données.  
  
 Vous attachez la <xref:System.Windows.Forms.DataGridView> contrôle à un cache que vous gérez et votre code contrôle quand les lignes de données sont envoyées et extraites. Pour minimiser l’encombrement mémoire, le cache doit être de taille comparable au nombre de lignes actuellement affichées. Lorsque l’utilisateur fait défiler de nouvelles lignes dans la vue, votre code demande de nouvelles données à partir du cache et vide éventuellement les anciennes données de la mémoire.  
  
 Lorsque vous implémentez le mode virtuel, vous devrez suivre lorsqu’une nouvelle ligne est nécessaire dans le modèle de données et lorsque pour annuler l’ajout de la nouvelle ligne. L’implémentation exacte de cette fonctionnalité dépend de l’implémentation du modèle de données et la sémantique de transaction du modèle de données ; Indique si la validation étendue est au niveau de la cellule ou la ligne.  
  
 Pour plus d’informations sur le mode virtuel, consultez [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md). Pour obtenir un exemple qui montre comment utiliser des événements de mode virtuel, consultez [procédure pas à pas : implémentation du Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>  
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Procédure pas à pas : création d’un contrôle DataGridView Windows Forms non lié](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 [Guide pratique pour lier des données au contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)
