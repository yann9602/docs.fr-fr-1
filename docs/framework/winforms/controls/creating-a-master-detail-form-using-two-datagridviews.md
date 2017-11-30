---
title: "Procédure pas à pas : Création d’un formulaire maître / détail utilisant deux contrôles de DataGridView Windows Forms"
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
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0d213d70d6f12cb8b574f07457c1b20317670d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Procédure pas à pas : création d'un formulaire maître/détail qui utilise deux contrôles DataGridView Windows Forms
Un des scénarios plus courants pour l’utilisation de la <xref:System.Windows.Forms.DataGridView> contrôle est le *maître/détail* formulaire, dans lequel une relation parent/enfant entre deux tables de base de données s’affiche. Sélection de lignes dans la table principale entraîne la table de détail mettre à jour avec les données enfants correspondantes.  
  
 Implémentation d’un formulaire maître/détail est facile à l’aide de l’interaction entre le <xref:System.Windows.Forms.DataGridView> contrôle et le <xref:System.Windows.Forms.BindingSource> composant. Dans cette procédure pas à pas, vous allez créer le formulaire à l’aide de deux <xref:System.Windows.Forms.DataGridView> contrôles et deux <xref:System.Windows.Forms.BindingSource> composants. L’écran affiche deux tables connexes dans la base de données Northwind SQL Server : `Customers` et `Orders`. Lorsque vous avez terminé, vous aurez un formulaire qui affiche tous les clients dans la base de données dans le master <xref:System.Windows.Forms.DataGridView> et toutes les commandes du client sélectionné dans le détail <xref:System.Windows.Forms.DataGridView>.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un maître/détail formulaire à l’aide de deux contrôles DataGridView Windows Forms](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Accès à un serveur doté de la base de données Northwind SQL Server.  
  
## <a name="creating-the-form"></a>Création du formulaire  
  
#### <a name="to-create-a-masterdetail-form"></a>Pour créer un formulaire maître/détail  
  
1.  Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient deux <xref:System.Windows.Forms.DataGridView> contrôles et deux <xref:System.Windows.Forms.BindingSource> composants. Le code suivant fournit l’initialisation de base et inclut un `Main` (méthode). Si vous utilisez la [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] concepteur pour créer votre formulaire, vous pouvez utiliser le code généré par concepteur au lieu de ce code, mais veillez à utiliser les noms indiqués dans les déclarations de variables.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données. Cet exemple utilise un `GetData` méthode remplit une <xref:System.Data.DataSet> d’objet, ajoute un <xref:System.Data.DataRelation> objet au jeu de données et lie le <xref:System.Windows.Forms.BindingSource> composants. Veillez à définir la variable `connectionString` avec une valeur appropriée pour votre base de données.  
  
    > [!IMPORTANT]
    >  Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  Implémenter un gestionnaire pour de votre formulaire <xref:System.Windows.Forms.Form.Load> événements qui lie la <xref:System.Windows.Forms.DataGridView> des contrôles à la <xref:System.Windows.Forms.BindingSource> composants et appelle le `GetData` (méthode). L’exemple suivant inclut le code qui se redimensionne <xref:System.Windows.Forms.DataGridView> colonnes pour correspondre les données affichées.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.  
  
#### <a name="to-test-the-form"></a>Pour tester le formulaire  
  
-   Compilez et exécutez l'application.  
  
     Vous verrez deux <xref:System.Windows.Forms.DataGridView> contrôles au-dessus de l’autre. Au-dessus se trouvent les clients de Northwind `Customers` table et en bas sont les `Orders` correspondant au client sélectionné. Lorsque vous sélectionnez des lignes différentes dans le coin supérieur <xref:System.Windows.Forms.DataGridView>, le contenu de la limite inférieure <xref:System.Windows.Forms.DataGridView> changent en conséquence.  
  
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
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour créer un formulaire maître/détail utilisant deux contrôles DataGridView Windows Form](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)  
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)
