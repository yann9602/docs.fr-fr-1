---
title: "Proc&#233;dure pas &#224; pas&#160;: gestion des erreurs qui se produisent lors de la saisie de donn&#233;es dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "entrée de données, gestion des erreurs"
  - "grilles de données, gestion des erreurs"
  - "DataGridView (contrôle Windows Forms), gestion des erreurs"
  - "gestion des erreurs, entrée de données"
  - "gestion des erreurs, DataGridView (contrôle)"
  - "procédures pas à pas (Windows Forms), DataGridView (contrôle)"
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Proc&#233;dure pas &#224; pas&#160;: gestion des erreurs qui se produisent lors de la saisie de donn&#233;es dans le contr&#244;le DataGridView Windows Forms
Gérer les erreurs du magasin de données sous\-jacent est une fonctionnalité requise pour une application de saisie de données.  Le contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms facilite ceci en exposant l'événement <xref:System.Windows.Forms.DataGridView.DataError> qui est déclenché lorsque le magasin de données détecte une violation de contrainte ou de règle métier.  
  
 Dans cette procédure pas à pas, vous allez récupérer des lignes de la table `Customers` dans l'exemple de base de données Northwind et les afficher dans un contrôle <xref:System.Windows.Forms.DataGridView>.  Lorsqu'une valeur `CustomerID` en double est détectée dans une nouvelle ligne ou dans une ligne existante modifiée, l'événement <xref:System.Windows.Forms.DataGridView.DataError> se produira, et sera géré par l'affichage d'une <xref:System.Windows.Forms.MessageBox> décrivant l'exception.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : gérer les erreurs qui se produisent lors de l'entrée de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Accès à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind  
  
## Création du formulaire  
  
#### Pour gérer des erreurs de saisie de données dans le contrôle DataGridView  
  
1.  Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un contrôle <xref:System.Windows.Forms.DataGridView> et un composant <xref:System.Windows.Forms.BindingSource>.  
  
     L'exemple de code suivant fournit l'initialisation de base et inclut une méthode `Main`.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données.  
  
     Cet exemple de code utilise une méthode  `GetData`  qui retourne un objet <xref:System.Data.DataTable> rempli.  Soyez sûr que vous définissez la variable `connectionString` avec une valeur appropriée pour votre base de données.  
  
    > [!IMPORTANT]
    >  Le stockage d'informations sensibles, par exemple, un mot de passe, dans la chaîne de connexion peut affecter la sécurité de votre application.  L'utilisation de l'authentification Windows \(également appelée sécurité intégrée\) offre un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui initialise les <xref:System.Windows.Forms.DataGridView> et <xref:System.Windows.Forms.BindingSource> et configure la liaison de données.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  Gérez l'événement <xref:System.Windows.Forms.DataGridView.DataError> sur la <xref:System.Windows.Forms.DataGridView>.  
  
     Si le contexte pour l'erreur est une opération de validation, affichez l'erreur dans une <xref:System.Windows.Forms.MessageBox>.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## Test de l'application  
 Vous pouvez à présent tester le formulaire afin de vous assurer qu'il se comporte comme prévu.  
  
#### Pour tester le formulaire  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
     Vous observerez un contrôle <xref:System.Windows.Forms.DataGridView> rempli de données provenant du tableau Customers.  Si vous entrez une valeur en double pour `CustomerID` et validez la modification, la valeur de la cellule se rétablira automatiquement et une <xref:System.Windows.Forms.MessageBox> signalera l'erreur de saisie.  
  
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
 [Saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [Comment : gérer les erreurs qui se produisent lors de l'entrée de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)   
 [Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)   
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)