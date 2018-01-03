---
title: "Exécution d'opérations du catalogue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 841f4e126a475799e7cc66f6f7afbcc9318a1096
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="808fa-102">Exécution d'opérations du catalogue</span><span class="sxs-lookup"><span data-stu-id="808fa-102">Performing Catalog Operations</span></span>
<span data-ttu-id="808fa-103">Pour exécuter une commande pour modifier une base de données ou un catalogue, telles que l’instruction CREATE TABLE ou CREATE PROCEDURE, créez un **commande** de l’objet à l’aide d’instructions SQL appropriées et un **connexion** objet.</span><span class="sxs-lookup"><span data-stu-id="808fa-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="808fa-104">Exécutez la commande avec le **ExecuteNonQuery** méthode de la **commande** objet.</span><span class="sxs-lookup"><span data-stu-id="808fa-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="808fa-105">L'exemple de code suivant crée une procédure stockée dans une base de données Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="808fa-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="808fa-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="808fa-106">See Also</span></span>  
 [<span data-ttu-id="808fa-107">Utilisation des commandes pour modifier les données</span><span class="sxs-lookup"><span data-stu-id="808fa-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="808fa-108">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="808fa-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="808fa-109">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="808fa-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
