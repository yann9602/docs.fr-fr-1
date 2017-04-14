---
title: "Mise &#224; jour des donn&#233;es dans une source de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Mise &#224; jour des donn&#233;es dans une source de donn&#233;es
Les instructions SQL qui modifient les données \(comme INSERT, UPDATE ou DELETE\) ne retournent pas de ligne.  De même, de nombreuses procédures stockées effectuent une action mais ne retournent pas de ligne.  Pour exécuter des commandes qui ne retournent pas de ligne, créez un objet **Command** avec la commande SQL appropriée et un objet **Connection** incluant tous les **Parameters** requis.  Exécutez la commande avec la méthode **ExecuteNonQuery** de l'objet **Command**.  
  
 La méthode **ExecuteNonQuery** retourne un entier qui représente le nombre de lignes affectées par l'instruction ou la procédure stockée exécutée.  Si plusieurs instructions sont exécutées, la valeur retournée est la somme des enregistrements affectés par toutes ces instructions.  
  
## Exemple  
 L'exemple de code suivant exécute une instruction INSERT pour insérer un enregistrement dans une base de données à l'aide de **ExecuteNonQuery**.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 L'exemple de code suivant exécute la procédure stockée créée par l'exemple de code dans [Exécution d'opérations de catalogue](../../../../docs/framework/data/adonet/performing-catalog-operations.md).  Aucune ligne n'est retournée par la procédure stockée, la méthode **ExecuteNonQuery** est donc utilisée mais la procédure stockée reçoit un paramètre d'entrée et retourne un paramètre de sortie et une valeur de retour.  
  
 Pour l'objet <xref:System.Data.OleDb.OleDbCommand>, le paramètre **ReturnValue** doit être d'abord ajouté à la collection **Parameters**.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)   
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## Voir aussi  
 [Utilisation de commandes pour modifier des données](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)   
 [Mise à jour de sources de données avec des DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)   
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)