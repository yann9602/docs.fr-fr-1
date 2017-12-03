---
title: "Procédure : lier des données à l'aide d'une source de données projet (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ee72f1c3eaf2c78a7cdff9b2a4db81ef0b767a2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Procédure : lier des données à l'aide d'une source de données projet (WCF Data Services)
Vous pouvez créer des sources de données basées sur les objets de données générés dans une application cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Lorsque vous ajoutez une référence à un service de données à l’aide de la **ajouter une référence de Service** boîte de dialogue, une source de données de projet est créée en même temps que les classes de données clientes générées. Une source de données est créée pour chaque jeu d'entités exposé par le service de données. Vous pouvez créer des formulaires qui affichent des données à partir du service en faisant glisser ces éléments de source de données à partir de la **des Sources de données** fenêtre sur le concepteur. Ces éléments deviennent des contrôles liés à la source de données. Pendant l’exécution, cette source de données est liée à une instance de la <xref:System.Data.Services.Client.DataServiceCollection%601> (classe), qui est remplie avec les objets retournés par une requête au service de données. Pour plus d’informations, consultez [liaison de données aux contrôles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 Les exemples dans cette rubrique utilisent l'exemple de service de données Northwind et des classes de service de données client générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-use-a-project-data-source-in-a-wpf-window"></a>Pour utiliser une source de données projet dans une fenêtre WPF  
  
1.  Dans un projet WPF, ajoutez une référence au service de données Northwind. Pour plus d’informations, consultez [Comment : ajouter une référence de Service de données](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
2.  Dans le **des Sources de données** fenêtre, développez le `Customers` nœud dans le **NorthwindEntities** source de données de projet.  
  
3.  Cliquez sur le **CustomerID** élément, sélectionnez **ComboBox** à partir de la liste, puis faites glisser le **CustomerID** d’élément à partir de la **clients** nœud à la concepteur.  
  
     Cela crée les éléments objet suivants dans le fichier XAML pour la fenêtre :  
  
    -   Un élément <xref:System.Windows.Data.CollectionViewSource> nommé `customersViewSource`. La propriété <xref:System.Windows.FrameworkElement.DataContext%2A> de l'élément objet <xref:System.Windows.Controls.Grid> de niveau supérieur est définie sur cette nouvelle <xref:System.Windows.Data.CollectionViewSource>.  
  
    -   Un <xref:System.Windows.Controls.ComboBox> lié aux données nommé  `CustomerID`.  
  
    -   <xref:System.Windows.Controls.Label>  
  
4.  Faites glisser le **commandes** propriété de navigation vers le concepteur.  
  
     Cela crée les éléments objet supplémentaires suivants dans le fichier XAML pour la fenêtre :  
  
    -   Un deuxième élément <xref:System.Windows.Data.CollectionViewSource> nommé `customersOrdersViewSource`, dont la source est `customerViewSource`.  
  
    -   Un contrôle <xref:System.Windows.Controls.DataGrid> lié aux données nommé  `ordersDataGrid`.  
  
5.  (Facultatif) Faites glisser des éléments supplémentaires à partir de la **clients** nœud vers le concepteur.  
  
6.  Ouvrez la page de codes du formulaire et ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]  
  
7.  Dans la classe partielle qui définit le formulaire, ajoutez le code suivant, qui crée une instance d'<xref:System.Data.Objects.ObjectContext> et définit la constante `customerID`.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]  
  
8.  Dans le concepteur, sélectionnez la fenêtre.  
  
    > [!NOTE]
    >  Assurez-vous que vous sélectionnez la fenêtre elle-même, plutôt que de sélectionner le contenu qui est dans la fenêtre. Si la fenêtre est activée, le **nom** zone de texte vers le haut de la **propriétés** fenêtre doit contenir le nom de la fenêtre.  
  
9. Dans le **propriétés** fenêtre, sélectionnez le **événements** bouton.  
  
10. Rechercher les **Loaded** événement, puis double-cliquez sur la liste déroulante liste en regard de cet événement.  
  
     Visual Studio ouvre le fichier code-behind pour la fenêtre et génère un gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded>.  
  
11. Dans la méthode de gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded> récemment créé, copiez et collez le code suivant.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]  
  
12. Ce code crée une instance de <xref:System.Data.Services.Client.DataServiceCollection%601> pour le type `Customers` basé sur l'exécution d'une requête LINQ qui retourne un <xref:System.Collections.Generic.IEnumerable%601> de `Customers` avec des objets `Orders` connexes du service de données Northwind et le lie à `customersViewSource`.  
  
### <a name="to-use-a-project-data-source-in-a-windows-form"></a>Pour utiliser une source de données projet dans un formulaire Windows  
  
1.  Dans le **des Sources de données** fenêtre, développez le **clients** nœud dans le **NorthwindEntities** source de données de projet.  
  
2.  Cliquez sur le **CustomerID** élément, sélectionnez **ComboBox** à partir de la liste, puis faites glisser le **CustomerID** d’élément à partir de la **clients** nœud à la concepteur.  
  
     Cette opération crée les contrôles suivants dans le formulaire :  
  
    -   Instance de <xref:System.Windows.Forms.BindingSource> nommée `customersBindingSource`.  
  
    -   Instance de <xref:System.Windows.Forms.BindingNavigator> nommée `customersBindingNavigator`. Vous pouvez supprimer ce contrôle qui ne sera pas nécessaire.  
  
    -   Un <xref:System.Windows.Forms.ComboBox> lié aux données nommé  `CustomerID`.  
  
    -   <xref:System.Windows.Forms.Label>  
  
3.  Faites glisser le **commandes** propriété de navigation vers le formulaire.  
  
4.  Cette opération crée le contrôle `ordersBindingSource` dont la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> a la valeur `customersBindingSource` et la propriété <xref:System.Windows.Forms.BindingSource.DataMember%2A> la valeur `Customers`. Elle crée également dans le formulaire le contrôle lié aux données `ordersDataGridView` et son contrôle label avec le titre approprié.  
  
5.  (Facultatif) Faites glisser des éléments supplémentaires à partir de la **clients** nœud vers le concepteur.  
  
6.  Ouvrez la page de codes du formulaire et ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersusing)]  
  
7.  Dans la classe partielle qui définit le formulaire, ajoutez le code suivant, qui crée une instance d'<xref:System.Data.Objects.ObjectContext> et définit la constante `customerID`.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdefinition)]  
  
8.  Dans le concepteur de formulaires, double-cliquez sur le formulaire.  
  
     La page de codes du formulaire s'ouvre et la méthode qui gère l'événement `Load` du formulaire est créée.  
  
9. Dans la méthode de gestionnaire d'événements `Load`, copiez et collez le code suivant.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabinding)]  
  
10. Ce code crée une instance de <xref:System.Data.Services.Client.DataServiceCollection%601> pour le type `Customers` basé sur l'exécution d'un <xref:System.Data.Services.Client.DataServiceQuery%601> qui retourne un <xref:System.Collections.Generic.IEnumerable%601> de `Customers` du service de données Northwind et le lie à `customersBindingSource`.  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Comment : lier les données aux éléments Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)
