---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un formulaire ma&#238;tre/d&#233;tail qui utilise deux contr&#244;les DataGridView Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "02/15/2017"
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
  - "DataGridView (contrôle Windows Forms), formulaire maître/détail"
  - "listes maître/détails, afficher sur les Windows Forms"
  - "tables parent-enfant, afficher sur les Windows Forms"
  - "procédures pas à pas (Windows Forms), DataGridView (contrôle)"
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un formulaire ma&#238;tre/d&#233;tail qui utilise deux contr&#244;les DataGridView Windows Forms
L'un des scénarios les plus communs d'utilisation du contrôle <xref:System.Windows.Forms.DataGridView> est le formulaire *maître\/détail* qui présente une relation parent\/enfant entre deux tables de base de données.  La sélection de lignes dans la table principale entraîne la mise à jour de la table secondaire avec les données enfants correspondantes.  
  
 L'implémentation d'un formulaire maître\/détail est facile à l'aide de l'interaction entre le contrôle <xref:System.Windows.Forms.DataGridView> et le composant <xref:System.Windows.Forms.BindingSource>.  Dans cette procédure pas à pas, vous générerez le formulaire à l'aide de deux contrôles <xref:System.Windows.Forms.DataGridView> et de deux composants <xref:System.Windows.Forms.BindingSource>.  Le formulaire montrera deux tables connexes dans l'exemple de base de données de SQL Server Northwind : `Customers` et `Orders`.  Lorsque vous aurez terminé, vous disposerez d'un formulaire présentant tous les clients de la base de données dans le <xref:System.Windows.Forms.DataGridView> maître et toutes les commandes pour le client sélectionné dans le <xref:System.Windows.Forms.DataGridView> détail.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un formulaire maître\/détail utilisant deux contrôles DataGridView Windows Form](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagrids.md).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Accès à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind  
  
## Création du formulaire.  
  
#### Pour créer un formulaire maître\/détail  
  
1.  Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient deux contrôles <xref:System.Windows.Forms.DataGridView> et deux composants <xref:System.Windows.Forms.BindingSource>.  Le code suivant fournit l'initialisation de base et inclut une méthode `Main`.  Si vous utilisez le concepteur [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] pour créer votre formulaire, vous pouvez utiliser le code généré par le concepteur au lieu de celui\-ci, mais veillez à utiliser les noms indiqués dans les déclarations de variables ci\-dessous.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données.  Cet exemple utilise une méthode `GetData` qui remplit un objet <xref:System.Data.DataSet>, ajoute un objet <xref:System.Data.DataRelation> au jeu de données et lie les composants <xref:System.Windows.Forms.BindingSource>.  Veillez à définir la variable `connectionString` avec une valeur appropriée pour votre base de données.  
  
    > [!IMPORTANT]
    >  Le stockage d'informations sensibles, par exemple, un mot de passe, dans la chaîne de connexion peut affecter la sécurité de votre application.  L'utilisation de l'authentification Windows \(également appelée sécurité intégrée\) offre un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui lie les contrôles <xref:System.Windows.Forms.DataGridView> aux composants <xref:System.Windows.Forms.BindingSource> et appelle la méthode `GetData`.  L'exemple suivant comprend un code qui redimensionne les colonnes <xref:System.Windows.Forms.DataGridView> en fonction des données affichées.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## Test de l'application  
 Vous pouvez à présent tester le formulaire afin de vous assurer qu'il se comporte comme prévu.  
  
#### Pour tester le formulaire  
  
-   Compilez et exécutez l'application.  
  
     Vous observerez deux contrôles <xref:System.Windows.Forms.DataGridView>, l'un au\-dessus de l'autre.  Au\-dessus se trouvent les clients de la table `Customers` de Northwind et au\-dessous, les `Orders` correspondant au client sélectionné.  À mesure que vous sélectionnez différentes lignes dans le <xref:System.Windows.Forms.DataGridView> du haut, le contenu du <xref:System.Windows.Forms.DataGridView> du bas change en conséquence.  
  
## Étapes suivantes  
 Cette application vous donne une présentation basique des capacités du contrôle <xref:System.Windows.Forms.DataGridView>.  Vous pouvez personnaliser l'apparence et le comportement du contrôle <xref:System.Windows.Forms.DataGridView> de plusieurs manières :  
  
-   Changez les styles de bordure et d'en\-tête.  Pour plus d'informations, consultez [Comment : modifier les styles de bordures et de quadrillage dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Activez ou restreignez les entrées d'utilisateur au contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations, consultez [Comment : empêcher l'ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md) et [Comment : définir une colonne en lecture seule dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Validez l'entrée d'utilisateur dans le contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations, consultez [Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
-   Gérez de très grandes quantités de données à l'aide du mode virtuel.  Pour plus d'informations, consultez [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Personnalisez l'apparence des cellules.  Pour plus d'informations, consultez [Comment : personnaliser l'apparence des cellules du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Comment : créer un formulaire maître\/détail utilisant deux contrôles DataGridView Windows Form](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagrids.md)   
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)