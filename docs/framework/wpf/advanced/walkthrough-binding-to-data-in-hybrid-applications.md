---
title: "Procédure pas à pas : liaison de données dans des applications hybrides"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3afc0d2eabb7554d64a40863b182a6edefe169f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Procédure pas à pas : liaison de données dans des applications hybrides
Liaison d’une source de données à un contrôle est essentielle pour fournir aux utilisateurs d’accéder aux données sous-jacentes, que vous utilisiez [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette procédure pas à pas montre comment vous pouvez utiliser la liaison de données dans les applications hybrides qui incluent les deux [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôles.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création du projet  
  
-   Définition du modèle de données.  
  
-   Spécification de la disposition du formulaire.  
  
-   Spécification des liaisons de données.  
  
-   Affichage des données à l’aide de l’interopérabilité.  
  
-   Ajout de la source de données au projet.  
  
-   Liaison à la source de données.  
  
 Pour l’intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [une liaison de données dans des Applications hybrides, exemple](http://go.microsoft.com/fwlink/?LinkID=159983).  
  
 À l’issue de cette procédure, vous aurez une meilleure compréhension des fonctionnalités de liaison de données dans les applications hybrides.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Accès à la base de données Northwind en cours d’exécution sur Microsoft SQL Server.  
  
## <a name="creating-the-project"></a>Création du projet  
  
#### <a name="to-create-and-set-up-the-project"></a>Pour créer et configurer le projet  
  
1.  Créez un projet d’Application WPF nommé `WPFWithWFAndDatabinding`.  
  
2.  Dans l’Explorateur de solutions, ajoutez des références aux assemblys suivants.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Ouvrez MainWindow.xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  Dans le <xref:System.Windows.Window> élément, ajoutez le code suivant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mappage des espaces de noms.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Nom de la valeur par défaut <xref:System.Windows.Controls.Grid> élément `mainGrid` en assignant le <xref:System.Windows.FrameworkElement.Name%2A> propriété.  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a>Définition du modèle de données  
 La liste principale des clients est affichée dans un <xref:System.Windows.Controls.ListBox> contrôle. L’exemple de code suivant définit un <xref:System.Windows.DataTemplate> objet nommé `ListItemsTemplate` qui contrôle l’arborescence d’éléments visuels de la <xref:System.Windows.Controls.ListBox> contrôle. Cela <xref:System.Windows.DataTemplate> est affectée à la <xref:System.Windows.Controls.ListBox> du contrôle <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété.  
  
#### <a name="to-define-the-data-template"></a>Pour définir le modèle de données  
  
-   Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> déclaration de l’élément.  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a>Spécification de la disposition du formulaire  
 La disposition du formulaire est définie par une grille de trois lignes et trois colonnes. <xref:System.Windows.Controls.Label>les contrôles sont fournis pour identifier chaque colonne dans la table Customers.  
  
#### <a name="to-set-up-the-grid-layout"></a>Pour configurer la disposition de la grille  
  
-   Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> déclaration de l’élément.  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a>Pour configurer les contrôles Label  
  
-   Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> déclaration de l’élément.  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a>Spécification des liaisons de données  
 La liste principale des clients est affichée dans un <xref:System.Windows.Controls.ListBox> contrôle. Le fichier joint `ListItemsTemplate` lie un <xref:System.Windows.Controls.TextBlock> le contrôle à la `ContactName` champ à partir de la base de données.  
  
 Les détails de chaque enregistrement client sont affichés dans plusieurs <xref:System.Windows.Controls.TextBox> contrôles.  
  
#### <a name="to-specify-data-bindings"></a>Pour spécifier des liaisons de données  
  
-   Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> déclaration de l’élément.  
  
     Le <xref:System.Windows.Data.Binding> classe lie le <xref:System.Windows.Controls.TextBox> contrôles aux champs appropriés dans la base de données.  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a>Affichage des données à l’aide de l’interopérabilité  
 Les commandes correspondant au client sélectionné sont affichées dans un <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> contrôle nommé `dataGridView1`. Le `dataGridView1` contrôle est lié à la source de données dans le fichier code-behind. A <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle est le parent de ce [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle.  
  
#### <a name="to-display-data-in-the-datagridview-control"></a>Pour afficher des données dans le contrôle DataGridView  
  
-   Copiez le code XAML suivant dans la <xref:System.Windows.Controls.Grid> déclaration de l’élément.  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a>Ajout de la source de données au projet  
 Avec [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], vous pouvez facilement ajouter une source de données à votre projet. Cette procédure ajoute un jeu de données fortement typé à votre projet. Plusieurs autres classes de prise en charge, comme les adaptateurs de table pour chacune des tables choisies, sont également ajoutées.  
  
#### <a name="to-add-the-data-source"></a>Pour ajouter la source de données  
  
1.  À partir de la **données** menu, sélectionnez **ajouter une nouvelle Source de données**.  
  
2.  Dans le **Assistant de Configuration de Source de données**, créez une connexion à la base de données Northwind à l’aide d’un jeu de données. Pour plus d’informations, consultez [Comment : se connecter à des données dans une base de données](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).  
  
3.  Lorsque vous êtes invité par le **Assistant de Configuration de Source de données**, enregistrer la chaîne de connexion en tant que `NorthwindConnectionString`.  
  
4.  Lorsque vous êtes invité à choisir vos objets de base de données, sélectionnez le `Customers` et `Orders` tables et le nom du jeu de données généré `NorthwindDataSet`.  
  
## <a name="binding-to-the-data-source"></a>Liaison à la source de données  
 Le <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> composant fournit une interface uniforme pour la source de données de l’application. La liaison à la source de données est implémentée dans le fichier code-behind.  
  
#### <a name="to-bind-to-the-data-source"></a>Pour effectuer la liaison à la source de données  
  
1.  Ouvrez le fichier code-behind nommé MainWindow.xaml.vb ou MainWindow.xaml.cs.  
  
2.  Copiez le code suivant dans le `MainWindow` définition de classe.  
  
     Ce code déclare le <xref:System.Windows.Forms.BindingSource> composant et les classes d’assistance associées qui se connectent à la base de données.  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  Copiez le code suivant dans le constructeur.  
  
     Ce code crée et initialise le <xref:System.Windows.Forms.BindingSource> composant.  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  Ouvrez MainWindow.xaml.  
  
5.  En mode Création ou la vue XAML, sélectionnez le <xref:System.Windows.Window> élément.  
  
6.  Dans la fenêtre Propriétés, cliquez sur le **événements** onglet.  
  
7.  Double-cliquez sur le <xref:System.Windows.FrameworkElement.Loaded> événement.  
  
8.  Copiez le code suivant dans le <xref:System.Windows.FrameworkElement.Loaded> Gestionnaire d’événements.  
  
     Ce code affecte la <xref:System.Windows.Forms.BindingSource> composant en tant que le contexte de données et remplit la `Customers` et `Orders` objets de carte.  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. Copiez le code suivant dans le `MainWindow` définition de classe.  
  
     Cette méthode gère le <xref:System.Windows.Data.CollectionView.CurrentChanged> événements et met à jour l’élément actuel de la liaison de données.  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. Appuyez sur F5 pour générer et exécuter l'application.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Concepteur WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Liaison de données dans des Applications hybrides, exemple](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
