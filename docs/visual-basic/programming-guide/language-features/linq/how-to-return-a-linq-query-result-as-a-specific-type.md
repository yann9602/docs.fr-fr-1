---
title: "Comment : retourner un résultat de requête LINQ en tant que type spécifique (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b79a00533e4ad8960c7f3cb512aafbe36e50b0
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Comment : retourner un résultat de requête LINQ en tant que type spécifique (Visual Basic)
Language-Integrated Query (LINQ) facilite l’accès aux informations de base de données et exécuter des requêtes. Par défaut, les requêtes LINQ retournent une liste d’objets comme un type anonyme. Vous pouvez également spécifier qu’une requête retourne une liste d’un type spécifique à l’aide de la `Select` clause.  
  
 L’exemple suivant montre comment créer une application qui effectue des requêtes sur une base de données SQL Server et projette les résultats comme un type nommé spécifique. Pour plus d’informations, consultez [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) et [Clause Select](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
 Les exemples de cette rubrique utilisent la base de données Northwind. Si vous n’avez pas de la base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site Web. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Pour créer une connexion à une base de données  
  
1.  Dans Visual Studio, ouvrez **l’Explorateur de serveurs**/**l’Explorateur de base de données** en cliquant sur **l’Explorateur de serveurs**/**base de données Explorer** sur la **vue** menu.  
  
2.  Avec le bouton droit **des connexions de données** dans **l’Explorateur de serveurs**/**l’Explorateur de base de données** puis cliquez sur **ajouter une connexion**.  
  
3.  Spécifiez une connexion valide à la base de données Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Pour ajouter un projet qui contient un fichier LINQ to SQL  
  
1.  Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**. Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**. Sélectionnez le **Classes LINQ to SQL** modèle d’élément.  
  
3.  Nommez le fichier `northwind.dbml`. Cliquez sur **Ajouter**. Le Concepteur Objet/Relationnel (Concepteur O/R) est ouvert pour le fichier northwind.dbml.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Pour ajouter des tables à interroger au Concepteur O/R  
  
1.  Dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, développez la connexion à la base de données Northwind. Développez le **Tables** dossier.  
  
     Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier northwind.dbml que vous avez ajoutée précédemment.  
  
2.  Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.  
  
     Le concepteur crée un nouveau `Customer` objet pour votre projet. Vous pouvez projeter un résultat de requête du `Customer` type ou en tant que type que vous créez. Cet exemple crée un nouveau type dans une procédure ultérieure et un résultat de requête en tant que type de projet.  
  
3.  Enregistrez vos modifications et fermez le concepteur.  
  
4.  Enregistrez votre projet.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Pour ajouter du code pour interroger la base de données et afficher les résultats  
  
1.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le formulaire Windows par défaut pour votre projet, Form1.  
  
2.  Double-cliquez sur Form1 pour modifier la classe Form1.  
  
3.  Après le `End Class` instruction de la classe Form1, ajoutez le code suivant pour créer un `CustomerInfo` type pour contenir les résultats de requête pour cet exemple.  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  Lorsque vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet à votre projet. Cet objet contient le code que vous devez disposer pour accéder à ces tables et pour accéder à des objets et collections pour chaque table. Le <xref:System.Data.Linq.DataContext> objet pour votre projet est nommé en fonction du nom de votre fichier .dbml. Pour ce projet, le <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext`.  
  
     Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O/R.  
  
     Dans le `Load` les événements de la classe Form1, ajoutez le code suivant pour interroger les tables qui sont exposées comme propriétés de votre contexte de données. Le `Select` clause de la requête créera un nouveau `CustomerInfo` type au lieu d’un type anonyme pour chaque élément du résultat de requête.  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  Appuyez sur F5 pour exécuter votre projet et afficher les résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Requêtes](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Méthodes DataContext (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
