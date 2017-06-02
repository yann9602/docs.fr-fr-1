---
title: "Proc&#233;dure pas &#224; pas&#160;: validation des donn&#233;es dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "données (Windows Forms), validation"
  - "grilles de données, valider des données"
  - "validation des données, Windows Forms"
  - "DataGridView (contrôle Windows Forms), validation des données"
  - "valider des données, Windows Forms"
  - "procédures pas à pas (Windows Forms), DataGridView (contrôle)"
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# Proc&#233;dure pas &#224; pas&#160;: validation des donn&#233;es dans le contr&#244;le DataGridView Windows Forms
Lorsque vous affichez les fonctionnalités d'entrée de données aux utilisateurs, vous devez fréquemment valider les données entrées dans votre formulaire.  La classe <xref:System.Windows.Forms.DataGridView> offre un moyen pratique pour valider les données avant qu'elles le soient au magasin de données.  Vous pouvez valider les données en gérant l'événement <xref:System.Windows.Forms.DataGridView.CellValidating>, qui est déclenché par la <xref:System.Windows.Forms.DataGridView> lorsque la cellule active change.  
  
 Dans cette procédure pas à pas, vous allez récupérer des lignes de la table `Customers` dans l'exemple de base de données Northwind et les afficher dans un contrôle <xref:System.Windows.Forms.DataGridView>.  Lorsqu'un utilisateur modifiera une cellule dans la colonne `CompanyName` et essaiera de quitter la cellule, le gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.CellValidating> examinera la nouvelle chaîne du nom de société pour vérifier qu'elle n'est pas vide. Si la nouvelle valeur est une chaîne vide, la <xref:System.Windows.Forms.DataGridView> empêchera le curseur de l'utilisateur de quitter la cellule avant qu'une chaîne non vide ait été entrée.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : valider des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Accès à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind  
  
## Création du formulaire  
  
#### Pour valider des données entrées dans une DataGridView  
  
1.  Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un contrôle <xref:System.Windows.Forms.DataGridView> et un composant <xref:System.Windows.Forms.BindingSource>.  
  
     L'exemple de code suivant fournit l'initialisation de base et inclut une méthode `Main`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données.  
  
     Cet exemple de code utilise une méthode  `GetData`  qui retourne un objet <xref:System.Data.DataTable> rempli.  Soyez sûr que vous définissez la variable `connectionString` avec une valeur appropriée pour votre base de données.  
  
    > [!IMPORTANT]
    >  Le stockage d'informations sensibles, par exemple, un mot de passe, dans la chaîne de connexion peut affecter la sécurité de votre application.  L'utilisation de l'authentification Windows, également qualifiée de sécurité intégrée, constitue un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui initialise les <xref:System.Windows.Forms.DataGridView> et <xref:System.Windows.Forms.BindingSource> et configure la liaison de données.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  Implémentez les gestionnaires pour les événements <xref:System.Windows.Forms.DataGridView.CellValidating> et <xref:System.Windows.Forms.DataGridView.CellEndEdit> du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
     Le gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.CellValidating> est l'endroit où vous déterminez si la valeur d'une cellule dans la colonne `CompanyName` est vide.  Si la valeur de la cellule n'est pas validée, donnez à la propriété <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> de la classe <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=fullName> la valeur `true`.  De cette manière, le contrôle <xref:System.Windows.Forms.DataGridView> empêche le curseur de quitter la cellule.  Définissez la propriété <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> sur la ligne à l'aide d'une chaîne explicative.  Cela affiche une icône d'erreur avec une info\-bulle qui contient le texte d'erreur.  Dans le gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.CellEndEdit>, définissez la propriété <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> sur la ligne à l'aide de la chaîne vide.  L'événement <xref:System.Windows.Forms.DataGridView.CellEndEdit> se produit uniquement lorsque la cellule quitte le mode édition, ce qu'elle ne peut faire en cas d'échec de validation.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## Test de l'application  
 Vous pouvez à présent tester le formulaire afin de vous assurer qu'il se comporte comme prévu.  
  
#### Pour tester le formulaire  
  
-   Compilez et exécutez l'application.  
  
     Vous verrez une <xref:System.Windows.Forms.DataGridView> remplie de données de la table `Customers`.  Pour modifier une valeur, double\-cliquez sur la cellule voulue dans la colonne `CompanyName`.  Si vous supprimez tous les caractères et appuyez sur la touche TAB pour quitter la cellule, la <xref:System.Windows.Forms.DataGridView> vous empêche de le faire.  Lorsque vous tapez une chaîne non vide dans la cellule, le contrôle <xref:System.Windows.Forms.DataGridView> vous permet de quitter la cellule.  
  
## Étapes suivantes  
 Cette application vous donne une présentation basique des capacités du contrôle <xref:System.Windows.Forms.DataGridView>.  Vous pouvez personnaliser l'apparence et le comportement du contrôle <xref:System.Windows.Forms.DataGridView> de plusieurs manières :  
  
-   Changez les styles de bordure et d'en\-tête.  Pour plus d'informations, consultez [Comment : modifier les styles de bordures et de quadrillage dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Activez ou restreignez les entrées d'utilisateur au contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations, consultez [Comment : empêcher l'ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md) et [Comment : définir une colonne en lecture seule dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Recherchez dans les entrées d'utilisateur les erreurs relatives à la base de données.  Pour plus d'informations, consultez [Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Gérez de très grandes quantités de données à l'aide du mode virtuel.  Pour plus d'informations, consultez [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Personnalisez l'apparence des cellules.  Pour plus d'informations, consultez [Comment : personnaliser l'apparence des cellules du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : définir des styles de police et de couleur dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [Saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [Comment : valider des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)   
 [Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)   
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)