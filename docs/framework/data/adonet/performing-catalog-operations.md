---
title: "Ex&#233;cution d&#39;op&#233;rations de catalogue | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Ex&#233;cution d&#39;op&#233;rations de catalogue
Pour exécuter une commande permettant de modifier une base de données ou un catalogue, comme l'instruction CREATE TABLE ou CREATE PROCEDURE, créez un objet **Command** à l'aide des instructions SQL appropriées et d'un objet **Connection**.  Exécutez la commande avec la méthode **ExecuteNonQuery** de l'objet **Command**.  
  
 L'exemple de code suivant crée une procédure stockée dans une base de données Microsoft SQL Server.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +   
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +   
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +   
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## Voir aussi  
 [Utilisation de commandes pour modifier des données](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)   
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)