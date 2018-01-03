---
title: "Mise à jour des données dans une source de données"
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
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c83b137f0de5ee165d110706dc286d13a084427c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="f71c4-102">Mise à jour des données dans une source de données</span><span class="sxs-lookup"><span data-stu-id="f71c4-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="f71c4-103">Les instructions SQL qui modifient les données (comme INSERT, UPDATE ou DELETE) ne retournent pas de ligne.</span><span class="sxs-lookup"><span data-stu-id="f71c4-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="f71c4-104">De même, de nombreuses procédures stockées effectuent une action mais ne retournent pas de ligne.</span><span class="sxs-lookup"><span data-stu-id="f71c4-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="f71c4-105">Pour exécuter des commandes qui ne retournent pas de lignes, créez un **commande** objet avec la commande SQL appropriée et un **connexion**, y compris tout **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="f71c4-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="f71c4-106">Exécutez la commande avec le **ExecuteNonQuery** méthode de la **commande** objet.</span><span class="sxs-lookup"><span data-stu-id="f71c4-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="f71c4-107">Le **ExecuteNonQuery** méthode retourne un entier qui représente le nombre de lignes affectées par l’instruction ou la procédure stockée qui a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="f71c4-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="f71c4-108">Si plusieurs instructions sont exécutées, la valeur retournée est la somme des enregistrements affectés par toutes ces instructions.</span><span class="sxs-lookup"><span data-stu-id="f71c4-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f71c4-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="f71c4-109">Example</span></span>  
 <span data-ttu-id="f71c4-110">L’exemple de code suivant exécute une instruction INSERT pour insérer un enregistrement dans une base de données à l’aide **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="f71c4-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="f71c4-111">L’exemple de code suivant exécute la procédure stockée créée par l’exemple de code dans [exécution d’opérations de catalogue](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f71c4-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span></span> <span data-ttu-id="f71c4-112">Aucuns lignes ne sont retournées par la procédure stockée, donc la **ExecuteNonQuery** méthode est utilisée, mais la procédure stockée reçoit un paramètre d’entrée et retourne un paramètre de sortie et une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="f71c4-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="f71c4-113">Pour le <xref:System.Data.OleDb.OleDbCommand> objet, le **ReturnValue** paramètre doit être ajouté à la **paramètres** collection premier.</span><span class="sxs-lookup"><span data-stu-id="f71c4-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f71c4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f71c4-114">See Also</span></span>  
 [<span data-ttu-id="f71c4-115">Utilisation des commandes pour modifier les données</span><span class="sxs-lookup"><span data-stu-id="f71c4-115">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="f71c4-116">Mise à jour de sources de données avec des DataAdapters</span><span class="sxs-lookup"><span data-stu-id="f71c4-116">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="f71c4-117">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="f71c4-117">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="f71c4-118">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="f71c4-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
