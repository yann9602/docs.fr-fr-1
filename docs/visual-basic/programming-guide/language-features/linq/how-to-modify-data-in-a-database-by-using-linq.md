---
title: "How to: Modify Data in a Database by Using LINQ (Visual Basic) | Microsoft Docs"
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
  - "inserting rows [LINQ to SQL]"
  - "deleting rows [LINQ to SQL]"
  - "updating rows [LINQ to SQL]"
  - "inserting data [Visual Basic]"
  - "deleting data"
  - "data [Visual Basic], updating"
  - "updating data [LINQ]"
  - "queries [LINQ in Visual Basic], data changes in database"
  - "queries [LINQ in Visual Basic], how-to topics"
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Modify Data in a Database by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les requêtes LINQ \(Language\-Integrated Query\) facilitent l'accès aux informations d'une base de données et la modification des valeurs dans la base.  
  
 L'exemple suivant indique comment créer une nouvelle application qui récupère et met à jour les informations d'une base de données SQL Server.  
  
 Les exemples de cette rubrique utilisent l'exemple de base de données Northwind.  Si vous ne disposez pas de l'exemple de base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger sur le site Web du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=98088).  Pour obtenir des instructions, consultez [Téléchargement d'exemples de bases de données](../Topic/Downloading%20Sample%20Databases.md).  
  
### Pour créer une connexion à une base de données  
  
1.  Dans Visual Studio, ouvrez l'**Explorateur de serveurs**\/**Explorateur de bases de données** en cliquant sur **Explorateur de serveurs** ou **Explorateur de bases de données** dans le menu **Affichage**.  
  
2.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, cliquez avec le bouton droit sur **Connexions de données** et cliquez sur **Ajouter une connexion**.  
  
3.  Spécifiez une connexion valide à l'exemple de base de données Northwind.  
  
### Pour ajouter un projet à l'aide d'un fichier LINQ to SQL  
  
1.  Dans le menu **Fichier** de Visual Studio, pointez sur **Nouveau**, puis cliquez sur **Projet**.  Sélectionnez **Application Windows Forms** Visual Basic comme type de projet.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  Sélectionnez le modèle d'élément **Classes LINQ to SQL**.  
  
3.  Nommez le fichier `northwind.dbml`.  Cliquez sur **Ajouter**.  Le fichier `northwind.dbml` s'ouvre dans le Concepteur Objet\/Relationnel \(Concepteur O\/R\).  
  
### Pour ajouter des tables à interroger et modifier au Concepteur O\/R  
  
1.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, développez la connexion à la base de données Northwind.  Développez le dossier **Tables**.  
  
     Si vous avez fermé le Concepteur O\/R, vous pouvez le rouvrir en double\-cliquant sur le fichier `northwind.dbml` que vous avez ajouté précédemment.  
  
2.  Cliquez sur la table Customers et faites\-la glisser dans le volet gauche du concepteur.  
  
     Le concepteur crée un nouvel objet Customer pour votre projet.  
  
3.  Enregistrez vos modifications et fermez le concepteur.  
  
4.  Enregistrez votre projet.  
  
### Pour ajouter du code en vue de modifier la base de données et afficher les résultats  
  
1.  À partir de la **Boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.DataGridView> sur le Windows Form par défaut pour votre projet, Form1.  
  
2.  Lorsque vous avez ajouté des tables au Concepteur O\/R, le concepteur a ajouté un objet <xref:System.Data.Linq.DataContext> à votre projet.  Cet objet contient du code que vous pouvez utiliser pour accéder à la table Customers.  Il contient également du code qui définit un objet Customer local et une collection Customers pour la table.  L'objet <xref:System.Data.Linq.DataContext> pour votre projet est nommé d'après le nom de votre fichier .dbml.  Pour ce projet, l'objet <xref:System.Data.Linq.DataContext> est nommé `northwindDataContext`.  
  
     Vous pouvez créer une instance de l'objet <xref:System.Data.Linq.DataContext> dans votre code et interroger et modifier la collection Customers spécifiée par le Concepteur O\/R.  Les modifications que vous apportez à la collection Customers ne se sont pas répercutées dans la base de données, tant que vous ne les soumettez pas en appelant la méthode <xref:System.Data.Linq.DataContext.SubmitChanges%2A> de l'objet <xref:System.Data.Linq.DataContext>.  
  
     Double\-cliquez sur le Windows Form, Form1, pour ajouter le code à l'événement <xref:System.Windows.Forms.Form.Load> et interroger la table Customers exposée comme une propriété de votre <xref:System.Data.Linq.DataContext>.  Ajoutez le code ci\-dessous :  
  
    ```vb#  
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
  
3.  À partir de la **Boîte à outils**, faites glisser trois contrôles <xref:System.Windows.Forms.Button> vers le formulaire.  Sélectionnez le premier contrôle `Button`.  Dans la fenêtre **Propriétés**, donnez au `Name` du contrôle `Button` la valeur `AddButton` et au `Text` la valeur `Ajouter`.  Sélectionnez le deuxième bouton et affectez à la propriété `Name` la valeur `UpdateButton` et à la propriété `Text` la valeur `Mise à jour`.  Sélectionnez le troisième bouton et affectez à la propriété `Name` la valeur `DeleteButton` et à la propriété `Text` la valeur `Supprimer`.  
  
4.  Double\-cliquez sur le bouton **Ajouter** pour ajouter le code à son événement `Click`.  Ajoutez le code ci\-dessous :  
  
    ```vb#  
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
  
5.  Double\-cliquez sur le bouton **Mise à jour** pour ajouter le code à son événement `Click`.  Ajoutez le code ci\-dessous :  
  
    ```vb#  
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
  
6.  Double\-cliquez sur le bouton **Supprimer** pour ajouter le code à son événement `Click`.  Ajoutez le code ci\-dessous :  
  
    ```vb#  
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
  
7.  Appuyez sur F5 pour exécuter votre projet.  Cliquez sur **Ajouter** pour ajouter un nouvel enregistrement.  Cliquez sur **Mise à jour** pour modifier le nouvel enregistrement.  Cliquez sur **Supprimer** pour supprimer le nouvel enregistrement.  
  
## Voir aussi  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Méthodes DataContext \(Concepteur O\/R\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [Procédure : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions \(Concepteur O\/R\)](../Topic/How%20to:%20Assign%20stored%20procedures%20to%20perform%20updates,%20inserts,%20and%20deletes%20\(O-R%20Designer\).md)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)