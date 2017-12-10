---
title: "Comment : rechercher la valeur minimale ou maximale dans un résultat de requête à l'aide de LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74a8148ad9572ee217921697e620791c85ff93f7
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Comment : rechercher la valeur minimale ou maximale dans un résultat de requête à l'aide de LINQ (Visual Basic)
Language-Integrated Query (LINQ) facilite l’accès aux informations de base de données et exécuter des requêtes.  
  
 L’exemple suivant montre comment créer une application qui effectue des requêtes sur une base de données SQL Server. L’exemple détermine les valeurs minimales et maximales pour les résultats à l’aide de la `Aggregate` et `Group By` clauses. Pour plus d’informations, consultez [Aggregate, Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) et [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Les exemples de cette rubrique utilisent la base de données Northwind. Si vous n’avez pas de la base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site Web. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
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
  
2.  Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur. Cliquez sur la table Orders et faites-le glisser vers le volet gauche du concepteur.  
  
     Le concepteur crée de nouveaux `Customer` et `Order` objets de votre projet. Notez que le concepteur détecte des relations entre les tables automatiquement et crée des propriétés pour les objets enfants. Par exemple, IntelliSense indiquera que la `Customer` objet a un `Orders` propriété pour toutes les commandes associées à ce client.  
  
3.  Enregistrez vos modifications et fermez le concepteur.  
  
4.  Enregistrez votre projet.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Pour ajouter du code pour interroger la base de données et afficher les résultats  
  
1.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le formulaire Windows par défaut pour votre projet, Form1.  
  
2.  Double-cliquez sur Form1 pour ajouter du code pour le `Load` événement du formulaire.  
  
3.  Lorsque vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet pour votre projet. Cet objet contient le code que vous devez disposer pour accéder à ces tables, en plus des collections et des objets individuels de chaque table. Le <xref:System.Data.Linq.DataContext> objet pour votre projet est nommé en fonction du nom de votre fichier .dbml. Pour ce projet, le <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext`.  
  
     Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O/R.  
  
     Ajoutez le code suivant à la `Load` événement. Ce code interroge les tables qui sont exposées comme propriétés de votre contexte de données et détermine les valeurs minimales et maximales pour les résultats. L’exemple utilise `Aggregate` clause pour interroger un résultat unique et le `Group By` clause pour afficher une moyenne pour les résultats groupés.  
  
     [!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]  
  
4.  Appuyez sur F5 pour exécuter votre projet et afficher les résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Requêtes](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [Méthodes DataContext (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
