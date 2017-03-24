---
title: "Comment : modifier des données dans une base de données à l’aide de LINQ (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 44ca3e44d8411a6329d176eb778677bfab2b365c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Comment : modifier des données dans une base de données à l'aide de LINQ (Visual Basic)
Intégrés au langage de requêtes de requête (LINQ) facilitent l’accès aux informations de base de données et modifier les valeurs dans la base de données.  
  
 L’exemple suivant montre comment créer une nouvelle application qui Récupère et les informations mises à jour dans une base de données SQL Server.  
  
 Les exemples de cette rubrique utilisent la base de données Northwind. Si vous n’avez pas la base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site Web. Pour obtenir des instructions, consultez la page [téléchargement d’exemples de bases de données](https://msdn.microsoft.com/library/bb399411).  
  
### <a name="to-create-a-connection-to-a-database"></a>Pour créer une connexion à une base de données  
  
1.  Dans Visual Studio, ouvrez **Explorateur de serveurs**/**Database Explorer** en cliquant sur les **affichage** menu, puis sélectionnez **Explorateur de serveurs**/**Explorateur de base de données**.  
  
2.  Avec le bouton droit **des connexions de données** dans **Explorateur de serveurs**/**Database Explorer**, puis cliquez sur **ajouter une connexion**.  
  
3.  Spécifiez une connexion valide à la base de données Northwind.  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Pour ajouter un projet avec LINQ au fichier SQL  
  
1.  Dans Visual Studio, sur le **fichier** menu, pointez sur **nouveau** , puis **projet**. Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**. Sélectionnez le **Classes LINQ to SQL** modèle d’élément.  
  
3.  Nommez le fichier `northwind.dbml`. Cliquez sur **Ajouter**. Le Concepteur Objet/Relationnel (Concepteur O/R) est ouvert pour la `northwind.dbml` fichier.  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Pour ajouter des tables à interroger et modifier au concepteur  
  
1.  Dans **Explorateur de serveurs**/**Database Explorer**, développez la connexion à la base de données Northwind. Développez le **Tables** dossier.  
  
     Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le `northwind.dbml` fichier que vous avez ajouté précédemment.  
  
2.  Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.  
  
     Le concepteur crée un nouvel objet Customer pour votre projet.  
  
3.  Enregistrez vos modifications et fermez le concepteur.  
  
4.  Enregistrez votre projet.  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Pour ajouter du code pour modifier la base de données et afficher les résultats  
  
1.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView>contrôle sur le formulaire Windows par défaut pour votre projet, Form1.</xref:System.Windows.Forms.DataGridView>  
  
2.  Lorsque vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext>objet à votre projet.</xref:System.Data.Linq.DataContext> Cet objet contient le code que vous pouvez utiliser pour accéder à la table Customers. Il contient également le code qui définit un objet Customer local et une collection de clients pour la table. Le <xref:System.Data.Linq.DataContext>objet pour votre projet est nommé d’après le nom de votre fichier .dbml.</xref:System.Data.Linq.DataContext> Pour ce projet, le <xref:System.Data.Linq.DataContext>est nommé `northwindDataContext`.</xref:System.Data.Linq.DataContext>  
  
     Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext>de l’objet dans votre code et interroger et modifier la collection Customers spécifiée par le Concepteur O/R.</xref:System.Data.Linq.DataContext> Les modifications que vous apportez à la collection de clients ne sont pas répercutées dans la base de données jusqu'à ce que vous les envoyez en appelant le <xref:System.Data.Linq.DataContext.SubmitChanges%2A>Procédé de la <xref:System.Data.Linq.DataContext>objet.</xref:System.Data.Linq.DataContext> </xref:System.Data.Linq.DataContext.SubmitChanges%2A>  
  
     Double-cliquez sur le Windows Form, Form1, pour ajouter du code à l' <xref:System.Windows.Forms.Form.Load>événement pour interroger la table Customers exposée comme une propriété de votre <xref:System.Data.Linq.DataContext>.</xref:System.Data.Linq.DataContext> </xref:System.Windows.Forms.Form.Load> Ajoutez le code suivant :  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  À partir de la **boîte à outils**, faites glisser trois <xref:System.Windows.Forms.Button>contrôles vers le formulaire.</xref:System.Windows.Forms.Button> Sélectionnez le premier `Button` contrôle. Dans le **propriétés** , configurez la `Name` de la `Button` le contrôle à `AddButton` et `Text` à `Add`. Sélectionnez le deuxième bouton et définissez la `Name` propriété `UpdateButton` et `Text` propriété `Update`. Sélectionnez le troisième bouton et définissez la `Name` propriété `DeleteButton` et `Text` propriété `Delete`.  
  
4.  Double-cliquez sur le **ajouter** bouton pour ajouter du code à son `Click` événement. Ajoutez le code suivant :  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  Double-cliquez sur le **mise à jour** bouton pour ajouter du code à son `Click` événement. Ajoutez le code suivant :  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  Double-cliquez sur le **supprimer** bouton pour ajouter du code à son `Click` événement. Ajoutez le code suivant :  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  Appuyez sur F5 pour exécuter votre projet. Cliquez sur **Add** pour ajouter un nouvel enregistrement. Cliquez sur **mise à jour** pour modifier le nouvel enregistrement. Cliquez sur **supprimer** pour supprimer l’enregistrement.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Requêtes](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)   
 [Méthodes DataContext (Concepteur O/R)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)   
 [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
