---
title: "Comment : appeler une procédure stockée à l'aide de LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 943bf4c80d88633cad857896381efcbef69683cc
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Comment : appeler une procédure stockée à l'aide de LINQ (Visual Basic)
Language-Integrated Query (LINQ) permet de facilement accéder aux informations de base de données, y compris les procédures stockées comme des objets de base de données.  
  
 L’exemple suivant montre comment créer une application qui appelle une procédure stockée dans une base de données SQL Server. L’exemple montre comment appeler deux procédures stockées différentes dans la base de données. Chaque procédure retourne les résultats d’une requête. Une procédure accepte des paramètres d’entrée, et l’autre procédure n’accepte pas de paramètres.  
  
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
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Pour ajouter des procédures stockées au Concepteur O/R  
  
1.  Dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, développez la connexion à la base de données Northwind. Développez le **de procédures stockées** dossier.  
  
     Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier northwind.dbml que vous avez ajoutée précédemment.  
  
2.  Cliquez sur le **ventes par année** procédure stockée et faites-le glisser vers le volet droit du concepteur. Cliquez sur le **dix produits les plus chers** procédure stockée faites-le glisser vers le volet droit du concepteur.  
  
3.  Enregistrez vos modifications et fermez le concepteur.  
  
4.  Enregistrez votre projet.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Pour ajouter du code pour afficher les résultats des procédures stockées  
  
1.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le formulaire Windows par défaut pour votre projet, Form1.  
  
2.  Double-cliquez sur Form1 pour ajouter du code à ses `Load` événement.  
  
3.  Lorsque vous avez ajouté des procédures stockées au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet pour votre projet. Cet objet contient le code que vous devez disposer pour accéder à ces procédures. Le <xref:System.Data.Linq.DataContext> objet pour le projet est nommé d’après le nom du fichier .dbml. Pour ce projet, le <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext`.  
  
     Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext> dans votre code et appeler les méthodes de la procédure stockée spécifiée par le Concepteur O/R. Pour lier à la <xref:System.Windows.Forms.DataGridView> de l’objet, vous devrez peut-être forcer la requête à exécuter immédiatement en appelant le <xref:System.Linq.Enumerable.ToList%2A> méthode sur les résultats de la procédure stockée.  
  
     Ajoutez le code suivant à la `Load` événements d’appeler une des procédures stockées exposées comme méthodes pour votre contexte de données.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  Appuyez sur F5 pour exécuter votre projet et afficher les résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Requêtes](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [Méthodes DataContext (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
