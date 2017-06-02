---
title: "Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es dans des applications hybrides | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "liaison de données (interopérabilité WPF)"
  - "applications hybrides (interopérabilité WPF)"
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: 39
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 36
---
# Proc&#233;dure pas &#224; pas&#160;: liaison de donn&#233;es dans des applications hybrides
La liaison d'une source de données à un contrôle est essentielle pour fournir aux utilisateurs l'accès aux données sous\-jacentes, que vous utilisiez [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Cette procédure pas à pas montre comment vous pouvez utiliser la liaison de données dans les applications hybrides qui incluent à la fois des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   création du projet ;  
  
-   Définition du modèle de données.  
  
-   Spécification de la disposition du formulaire.  
  
-   Spécification des liaisons de données.  
  
-   Affichage de données en utilisant l'interopérabilité.  
  
-   Ajout de la source de données au projet.  
  
-   Liaison à la source de données.  
  
 Pour obtenir l'intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [Liaison de données dans des applications hybrides, exemple](http://go.microsoft.com/fwlink/?LinkID=159983).  
  
 Lorsque vous avez terminé, vous disposerez de connaissances relatives aux fonctionnalités de liaison de données dans les applications hybrides.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Accès à la base de données Northwind exécutée sur Microsoft SQL Server..  
  
## Création du projet  
  
#### Pour créer et paramétrer le projet  
  
1.  Créez un projet d'application WPF nommé `WPFWithWFAndDatabinding`.  
  
2.  Dans l'Explorateur de solutions, ajoutez une référence aux assemblys suivants.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Ouvrez MainWindow.xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  Dans l'élément <xref:System.Windows.Window>, ajoutez le mappage d'espaces de noms [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] suivant.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Nommez<xref:System.Windows.Controls.Grid> l'élément `mainGrid` par défaut en attribuant la propriété <xref:System.Windows.FrameworkElement.Name%2A>.  
  
     [!code-xml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## Définition du modèle de données  
 La liste principale des clients est affichée dans un contrôle <xref:System.Windows.Controls.ListBox>.  L'exemple de code suivant définit un objet <xref:System.Windows.DataTemplate> nommé `ListItemsTemplate` qui contrôle l'arborescence d'éléments visuels du contrôle <xref:System.Windows.Controls.ListBox>.  Ce <xref:System.Windows.DataTemplate> est attribué à la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> du contrôle <xref:System.Windows.Controls.ListBox>.  
  
#### Pour définir le modèle de données  
  
-   Copiez le code XAML suivant dans la déclaration de l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## Spécification de la disposition du formulaire  
 La disposition du formulaire est définie par une grille comportant trois lignes et trois colonnes.  Les contrôles <xref:System.Windows.Controls.Label> sont fournis pour identifier chaque colonne dans la table Customers.  
  
#### Pour paramétrer la disposition de la grille  
  
-   Copiez le code XAML suivant dans la déclaration de l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### Pour paramétrer les contrôles Label  
  
-   Copiez le code XAML suivant dans la déclaration de l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## Spécification des liaisons de données  
 La liste principale des clients est affichée dans un contrôle <xref:System.Windows.Controls.ListBox>.  Le `ListItemsTemplate` attaché lie un contrôle <xref:System.Windows.Controls.TextBlock> au champ `ContactName` de la base de données.  
  
 Les détails de chaque enregistrement client sont affichés dans plusieurs contrôles <xref:System.Windows.Controls.TextBox>.  
  
#### Pour spécifier des liaisons de données  
  
-   Copiez le code XAML suivant dans la déclaration de l'élément <xref:System.Windows.Controls.Grid>.  
  
     La classe <xref:System.Windows.Data.Binding> lie les contrôles <xref:System.Windows.Controls.TextBox> aux champs appropriés dans la base de données.  
  
     [!code-xml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## Affichage de données en utilisant l'interopérabilité  
 Les ordres qui correspondent au client sélectionné sont affichés dans un contrôle <xref:System.Windows.Forms.DataGridView?displayProperty=fullName> nommé `dataGridView1`.  Le contrôle `dataGridView1` est lié à la source de données dans le fichier code\-behind.  Un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> est le parent de ce contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
#### Pour afficher des données dans le contrôle DataGridView  
  
-   Copiez le code XAML suivant dans la déclaration de l'élément <xref:System.Windows.Controls.Grid>.  
  
     [!code-xml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## Ajout de la source de données au projet  
 Avec [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], vous pouvez ajouter facilement une source de données à votre projet.  Cette procédure ajoute un groupe de données fortement typé à votre projet.  Plusieurs autres classes de prise en charge, telles que les adaptateurs de table pour chacune des tables choisies, sont également ajoutées.  
  
#### Pour ajouter la source de données  
  
1.  Dans le menu **Données**, sélectionnez **Ajouter une nouvelle source de données**.  
  
2.  Dans l'**Assistant Configuration de source de données**, créez une connexion à la base de données Northwind à l'aide d'un dataset.  Pour plus d'informations, consultez [Comment : établir une connexion à des données d'une base de données](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
3.  Lorsque vous êtes invités par l'**Assistant Configuration de source de données**, enregistrez la chaîne de connexion en tant que `NorthwindConnectionString`.  
  
4.  Lorsque vous êtes invité à choisir vos objets de base de données, sélectionnez les tables `Customers` et `Orders`, puis nommez le groupe de données généré `NorthwindDataSet`.  
  
## Liaison à la source de données  
 Le composant <xref:System.Windows.Forms.BindingSource?displayProperty=fullName> fournit une interface uniforme pour la source de données de l'application.  La liaison à la source de données est implémentée dans le fichier code\-behind.  
  
#### Pour effectuer la liaison à la source de données  
  
1.  Ouvrez le fichier code\-behind, nommé MainWindow.xaml.vb ou MainWindow.xaml.cs.  
  
2.  Copiez le code suivant dans la définition de classe `MainWindow`.  
  
     Ce code déclare le composant <xref:System.Windows.Forms.BindingSource> et les classes d'assistance associées qui se connectent à la base de données.  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  Copiez le code suivant dans le constructeur.  
  
     Ce code crée et initialise le composant <xref:System.Windows.Forms.BindingSource>.  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  Ouvrez MainWindow.xaml.  
  
5.  En mode Design ou XAML, sélectionnez l'élément <xref:System.Windows.Window>.  
  
6.  Dans la fenêtre Propriétés, cliquez sur l'onglet **Événements**.  
  
7.  Double\-cliquez sur l'événement <xref:System.Windows.FrameworkElement.Loaded>.  
  
8.  Copiez le code suivant dans le gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded>.  
  
     Ce code affecte le composant <xref:System.Windows.Forms.BindingSource> en tant que contexte de données et remplit les objets d'adaptateur `Customers` et `Orders`.  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. Copiez le code suivant dans la définition de classe `MainWindow`.  
  
     Cette méthode gère l'événement <xref:System.Windows.Data.CollectionView.CurrentChanged> et met à jour l'élément actuel de la liaison de données.  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. Appuyez sur F5 pour générer et exécuter l'application.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)   
 [Liaison de données dans des applications hybrides, exemple](http://go.microsoft.com/fwlink/?LinkID=159983)   
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)