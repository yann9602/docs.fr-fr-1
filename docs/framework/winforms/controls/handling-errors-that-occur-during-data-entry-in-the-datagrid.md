---
title: "Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms"
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
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 016a30e4b578ead199124d70cc12f240c74bf370
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms
Gestion des erreurs dans le magasin de données sous-jacent sont une fonctionnalité requise pour une application de saisie de données. Windows Forms <xref:System.Windows.Forms.DataGridView> contrôle facilite cette procédure en exposant les <xref:System.Windows.Forms.DataGridView.DataError> événement, qui est déclenché lorsque le magasin de données détecte une violation de contrainte ou une règle métier.  
  
 Dans cette procédure pas à pas, vous allez récupérer des lignes à partir de la `Customers` de table dans la base de données Northwind et les afficher dans un <xref:System.Windows.Forms.DataGridView> contrôle. Lorsqu’un doublon `CustomerID` est détectée dans une nouvelle ligne ou une ligne existante modifiée, le <xref:System.Windows.Forms.DataGridView.DataError> événement se produit, qui sera géré en affichant un <xref:System.Windows.Forms.MessageBox> qui décrit l’exception.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : gérer les erreurs que se produisent au cours de saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Accès à un serveur doté de la base de données Northwind SQL Server.  
  
## <a name="creating-the-form"></a>Création du formulaire  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Pour gérer les erreurs de saisie de données dans le contrôle DataGridView  
  
1.  Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un <xref:System.Windows.Forms.DataGridView> contrôle et un <xref:System.Windows.Forms.BindingSource> composant.  
  
     L’exemple de code suivant fournit l’initialisation de base et inclut un `Main` (méthode).  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données.  
  
     Cet exemple de code utilise un `GetData` méthode qui retourne un remplis <xref:System.Data.DataTable> objet. Vérifiez que vous le `connectionString` variable une valeur qui est appropriée pour votre base de données.  
  
    > [!IMPORTANT]
    >  Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  Implémentez un gestionnaire pour de votre formulaire <xref:System.Windows.Forms.Form.Load> événement qui initialise le <xref:System.Windows.Forms.DataGridView> et <xref:System.Windows.Forms.BindingSource> et configure la liaison de données.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  Gérer les <xref:System.Windows.Forms.DataGridView.DataError> événement sur le <xref:System.Windows.Forms.DataGridView>.  
  
     Si le contexte de l’erreur est une opération de validation, affichez l’erreur dans un <xref:System.Windows.Forms.MessageBox>.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.  
  
#### <a name="to-test-the-form"></a>Pour tester le formulaire  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
     Vous verrez un <xref:System.Windows.Forms.DataGridView> contrôle rempli avec des données à partir de la table Customers. Si vous entrez une valeur en double pour `CustomerID` et valider la modification, la valeur de cellule reprendra automatiquement et vous verrez un <xref:System.Windows.Forms.MessageBox> qui affiche l’erreur de saisie de données.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette application vous donne une connaissance élémentaire de la <xref:System.Windows.Forms.DataGridView> fonctionnalités du contrôle. Vous pouvez personnaliser l’apparence et le comportement de la <xref:System.Windows.Forms.DataGridView> contrôle de plusieurs manières :  
  
-   Modifier les styles de bordure et en-tête. Pour plus d’informations, consultez [Comment : modifier la bordure et les Styles de quadrillage dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Activer ou restreindre l’entrée d’utilisateur à le <xref:System.Windows.Forms.DataGridView> contrôle. Pour plus d’informations, consultez [Comment : empêcher l’ajout ligne et la suppression dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), et [Comment : rendre en lecture seule les colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Valider l’entrée d’utilisateur pour le <xref:System.Windows.Forms.DataGridView> contrôle. Pour plus d’informations, consultez [procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
-   Gérer des jeux de données très volumineux à l’aide du mode virtuel. Pour plus d’informations, consultez [procédure pas à pas : implémentation du Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Personnaliser l’apparence des cellules. Pour plus d’informations, consultez [Comment : personnaliser l’apparence des cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : définir des Styles de cellule par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour gérer les erreurs qui se produisent lors de l'entrée de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)
