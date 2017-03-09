---
title: "How to: Filter Query Results by Using LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "filtering [Visual Basic]"
  - "filtering data [LINQ in Visual Basic]"
  - "filtering [LINQ in Visual Basic]"
  - "queries [LINQ in Visual Basic], filtering results"
  - "querying databases [LINQ]"
  - "queries [LINQ in Visual Basic], how-to topics"
  - "query samples [Visual Basic]"
  - "filtering data [Visual Basic]"
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# How to: Filter Query Results by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

LINQ \(Language\-Integrated Query\) facilite l'accès aux informations de la base de données et l'exécution des requêtes.  
  
 L'exemple suivant indique comment créer une nouvelle application qui effectue des requêtes contre une base de données SQL Server et filtre les résultats par valeur particulière, en utilisant la clause `Where`.  Pour plus d'informations, consultez [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
 Les exemples de cette rubrique utilisent l'exemple de base de données Northwind.  Si vous ne disposez pas de l'exemple de base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger sur le site Web du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=98088).  Pour obtenir des instructions, consultez [Téléchargement d'exemples de bases de données](../Topic/Downloading%20Sample%20Databases.md).  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour créer une connexion à une base de données  
  
1.  Dans Visual Studio, ouvrez l'**Explorateur de serveurs**\/**Explorateur de bases de données** en cliquant sur **Explorateur de serveurs** ou **Explorateur de bases de données** dans le menu **Affichage**.  
  
2.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, cliquez avec le bouton droit sur **Connexions de données**, puis sur **Ajouter une connexion**.  
  
3.  Spécifiez une connexion valide à l'exemple de base de données Northwind.  
  
### Pour ajouter un projet contenant un fichier LINQ to SQL  
  
1.  Dans le menu **Fichier** de Visual Studio, pointez sur **Nouveau**, puis cliquez sur **Projet**.  Sélectionnez **Application Windows Forms** Visual Basic comme type de projet.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  Sélectionnez le modèle d'élément **Classes LINQ to SQL**.  
  
3.  Nommez le fichier `northwind.dbml`.  Cliquez sur **Ajouter**.  Le fichier northwind.dbml s'ouvre dans le Concepteur Objet\/Relationnel \(Concepteur O\/R\).  
  
### Pour ajouter des tables à interroger au Concepteur O\/R  
  
1.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, développez la connexion à la base de données Northwind.  Développez le dossier **Tables**.  
  
     Si vous avez fermé le Concepteur O\/R, vous pouvez le rouvrir en double\-cliquant sur le fichier northwind.dbml que vous avez ajouté précédemment.  
  
2.  Cliquez sur la table Customers et faites\-la glisser dans le volet gauche du concepteur.  Cliquez sur la table Orders et faites\-la glisser dans le volet gauche du concepteur.  
  
     Le concepteur crée de nouveaux objets `Customer` et `Order` pour votre projet.  Notez que le concepteur détecte automatiquement les relations entre les tables et crée des propriétés enfants pour les objets connexes.  Par exemple, IntelliSense indiquera que l'objet `Customer` a une propriété `Orders` pour tous les commandes associées à ce client.  
  
3.  Enregistrez vos modifications et fermez le concepteur.  
  
4.  Enregistrez votre projet.  
  
### Pour ajouter du code en vue d'interroger la base de données et afficher les résultats  
  
1.  À partir de la **Boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.DataGridView> sur le Windows Form par défaut pour votre projet, Form1.  
  
2.  Double\-cliquez sur Form1 pour ajouter le code à l'événement `Load` du formulaire.  
  
3.  Lorsque vous avez ajouté des tables au Concepteur O\/R, le concepteur a ajouté un objet <xref:System.Data.Linq.DataContext> à votre projet.  Cet objet contient le code indispensable pour accéder à ces tables, ainsi qu'aux collections et objets individuels de chaque table.  L'objet <xref:System.Data.Linq.DataContext> pour votre projet est nommé d'après le nom de votre fichier .dbml.  Pour ce projet, l'objet <xref:System.Data.Linq.DataContext> est nommé `northwindDataContext`.  
  
     Vous pouvez créer une instance du <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O\/R.  
  
     Ajoutez le code suivant à l'événement `Load`,  pour interroger les tables exposées en tant que propriétés de votre contexte de données.  La requête filtre les résultats et ne retourne que les clients situés à `London`.  
  
     [!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/StoredProcedureHowTo/Form5.vb#11)]  
  
4.  Appuyez sur F5 pour exécuter votre projet et consulter les résultats.  
  
5.  Vous trouverez plus bas d'autres filtres que vous pouvez essayer.  
  
     [!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/StoredProcedureHowTo/Form5.vb#12)]  
  
## Voir aussi  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Méthodes DataContext \(Concepteur O\/R\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)