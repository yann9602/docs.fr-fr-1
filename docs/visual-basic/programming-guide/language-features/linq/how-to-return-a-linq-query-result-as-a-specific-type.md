---
title: "How to: Return a LINQ Query Result as a Specific Type (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [LINQ in Visual Basic], specific type returned"
  - "projection [LINQ in Visual Basic]"
  - "anonymous types [Visual Basic]"
  - "querying databases [LINQ]"
  - "queries [LINQ in Visual Basic], how-to topics"
  - "query samples [Visual Basic]"
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Return a LINQ Query Result as a Specific Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

LINQ \(Language\-Integrated Query\) facilite l'accès aux informations de la base de données et l'exécution des requêtes.  Par défaut, les requêtes LINQ retournent une liste d'objets sous forme de type anonyme.  Vous pouvez également spécifier qu'une requête retourne une liste d'un type spécifique en utilisant la clause `Select`.  
  
 L'exemple suivant indique comment créer une nouvelle application qui effectue des requêtes sur une base de données SQL Server et projette les résultats sous forme de type nommé spécifique.  Pour plus d'informations, consultez [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) et [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
 Les exemples de cette rubrique utilisent l'exemple de base de données Northwind.  Si vous ne disposez pas de l'exemple de base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger sur le site Web du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=98088).  Pour obtenir des instructions, consultez [Téléchargement d'exemples de bases de données](../Topic/Downloading%20Sample%20Databases.md).  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
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
  
2.  Cliquez sur la table Customers et faites\-la glisser dans le volet gauche du concepteur.  
  
     Le concepteur crée un nouvel objet `Customer` pour votre projet.  Vous pouvez projeter un résultat de requête comme type `Customer` ou comme un type que vous créez.  Cet exemple créera un nouveau type dans une procédure ultérieure et projettera un résultat de requête sous la forme de ce type.  
  
3.  Enregistrez vos modifications et fermez le concepteur.  
  
4.  Enregistrez votre projet.  
  
### Pour ajouter du code en vue d'interroger la base de données et afficher les résultats  
  
1.  À partir de la **Boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.DataGridView> sur le Windows Form par défaut pour votre projet, Form1.  
  
2.  Double\-cliquez sur Form1 pour modifier la classe Form1.  
  
3.  Après l'instruction `End Class` de la classe Form1, ajoutez le code suivant pour créer un type `CustomerInfo` pour stocker les résultats de la requête pour cet exemple.  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  Lorsque vous avez ajouté des tables au Concepteur O\/R, le concepteur a ajouté un objet <xref:System.Data.Linq.DataContext> à votre projet.  Cet objet contient le code indispensable pour accéder à ces tables, ainsi qu'aux collections et objets individuels de chaque table.  L'objet <xref:System.Data.Linq.DataContext> pour votre projet est nommé d'après le nom de votre fichier .dbml.  Pour ce projet, l'objet <xref:System.Data.Linq.DataContext> est nommé `northwindDataContext`.  
  
     Vous pouvez créer une instance du <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O\/R.  
  
     Ajoutez le code suivant à l'événement `Load` de la classe Form1 pour interroger les tables qui sont exposées comme propriétés de votre contexte de données.  La clause `Select` de la requête créera un nouveau type `CustomerInfo` au lieu d'un type anonyme pour chaque élément du résultat de la requête.  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  Appuyez sur F5 pour exécuter votre projet et consulter les résultats.  
  
## Voir aussi  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Méthodes DataContext \(Concepteur O\/R\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)