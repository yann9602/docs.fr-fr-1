---
title: "Récupération de données à l'aide d'un DataReader"
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
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0b66ca2fbcc760598b771b4c02a46acc3c9c1d4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-data-using-a-datareader"></a><span data-ttu-id="48078-102">Récupération de données à l'aide d'un DataReader</span><span class="sxs-lookup"><span data-stu-id="48078-102">Retrieving Data Using a DataReader</span></span>
<span data-ttu-id="48078-103">La récupération de données à l’aide un **DataReader** implique la création d’une instance de la **commande** objet, puis en créant un **DataReader** en appelant  **Command.ExecuteReader** pour extraire des lignes à partir d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="48078-103">Retrieving data using a **DataReader** involves creating an instance of the **Command** object and then creating a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="48078-104">L’exemple suivant montre comment utiliser un **DataReader** où `reader` représente un DataReader valide et `command` représente un objet Command valide.</span><span class="sxs-lookup"><span data-stu-id="48078-104">The following example illustrates using a **DataReader** where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  
  
```  
reader = command.ExecuteReader();  
```  
  
 <span data-ttu-id="48078-105">Vous utilisez la **en lecture** méthode de la **DataReader** objet pour obtenir une ligne à partir des résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="48078-105">You use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span> <span data-ttu-id="48078-106">Vous pouvez accéder à chaque colonne de la ligne retournée en passant le nom ou la référence ordinale de la colonne à la **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="48078-106">You can access each column of the returned row by passing the name or ordinal reference of the column to the **DataReader**.</span></span> <span data-ttu-id="48078-107">Toutefois, pour de meilleures performances, le **DataReader** fournit une série de méthodes qui vous permettent d’accéder aux valeurs de colonne dans leurs types de données natifs (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, et ainsi de suite).</span><span class="sxs-lookup"><span data-stu-id="48078-107">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="48078-108">Pour obtenir la liste des méthodes d’accesseur typées pour les données spécifiques au fournisseur **DataReaders**, consultez <xref:System.Data.OleDb.OleDbDataReader> et <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="48078-108">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="48078-109">L’utilisation des méthodes d’accesseur typées, lorsque le type de données sous-jacent est connu, réduit le volume de conversion de types requis lors de l’extraction de la valeur de colonne.</span><span class="sxs-lookup"><span data-stu-id="48078-109">Using the typed accessor methods, assuming the underlying data type is known, reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48078-110">La version de Windows Server 2003 du .NET Framework inclut une propriété supplémentaire pour le **DataReader**, **HasRows**, ce qui vous permet de déterminer si le **DataReader**a retourné des résultats avant la lecture à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="48078-110">The Windows Server 2003 release of the .NET Framework includes an additional property for the **DataReader**, **HasRows**, which enables you to determine if the **DataReader** has returned any results before reading from it.</span></span>  
  
 <span data-ttu-id="48078-111">L’exemple de code suivant itère un **DataReader** objet et retourne deux colonnes à partir de chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="48078-111">The following code example iterates through a **DataReader** object, and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 <span data-ttu-id="48078-112">Le **DataReader** fournit un flux non mis en tampon de données qui permet à la logique procédurale de traiter efficacement les résultats à partir d’une source de données de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="48078-112">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="48078-113">Le **DataReader** est un bon choix lors de la récupération de grandes quantités de données, car les données ne sont pas mis en cache en mémoire.</span><span class="sxs-lookup"><span data-stu-id="48078-113">The **DataReader** is a good choice when retrieving large amounts of data because the data is not cached in memory.</span></span>  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="48078-114">Fermeture du DataReader</span><span class="sxs-lookup"><span data-stu-id="48078-114">Closing the DataReader</span></span>  
 <span data-ttu-id="48078-115">Vous devez toujours appeler la **fermer** méthode lorsque vous avez fini d’utiliser le **DataReader** objet.</span><span class="sxs-lookup"><span data-stu-id="48078-115">You should always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="48078-116">Si votre **commande** sortie contient des paramètres ou valeurs de retour, ils ne seront pas disponibles tant que le **DataReader** est fermé.</span><span class="sxs-lookup"><span data-stu-id="48078-116">If your **Command** contains output parameters or return values, they will not be available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="48078-117">Notez que pendant un **DataReader** est ouvert, le **connexion** est utilisé exclusivement par qui **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="48078-117">Note that while a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="48078-118">Vous ne pouvez pas exécuter de commandes pour le **connexion**, y compris la création d’un autre **DataReader**, jusqu'à ce que l’original **DataReader** est fermé.</span><span class="sxs-lookup"><span data-stu-id="48078-118">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48078-119">N’appelez pas **fermer** ou **Dispose** sur un **connexion**, un **DataReader**, ou tout autre objet managé dans le **Finalize**  méthode de votre classe.</span><span class="sxs-lookup"><span data-stu-id="48078-119">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="48078-120">Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement.</span><span class="sxs-lookup"><span data-stu-id="48078-120">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="48078-121">Si votre classe ne possède pas les ressources non managées, n’incluez pas une **Finalize** méthode dans votre définition de classe.</span><span class="sxs-lookup"><span data-stu-id="48078-121">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="48078-122">Pour plus d’informations, consultez [le Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="48078-122">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="48078-123">Extraction de plusieurs jeux de résultats à l'aide de NextResult</span><span class="sxs-lookup"><span data-stu-id="48078-123">Retrieving Multiple Result Sets using NextResult</span></span>  
 <span data-ttu-id="48078-124">Si plusieurs jeux de résultats est retournés, le **DataReader** fournit le **NextResult** définit de méthode pour itérer au sein du résultat dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="48078-124">If multiple result sets are returned, the **DataReader** provides the **NextResult** method to iterate through the result sets in order.</span></span> <span data-ttu-id="48078-125">L'exemple suivant montre l'objet <xref:System.Data.SqlClient.SqlDataReader> traitant les résultats de deux instructions SELECT utilisant la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="48078-125">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="48078-126">Obtention d'informations de schéma à partir du DataReader</span><span class="sxs-lookup"><span data-stu-id="48078-126">Getting Schema Information from the DataReader</span></span>  
 <span data-ttu-id="48078-127">Pendant un **DataReader** est ouvert, vous pouvez extraire les informations de schéma sur le résultat actuel à l’aide de la **GetSchemaTable** (méthode).</span><span class="sxs-lookup"><span data-stu-id="48078-127">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="48078-128">**GetSchemaTable** retourne un <xref:System.Data.DataTable> objet rempli avec des lignes et colonnes qui contiennent des informations de schéma pour le jeu de résultats actuel.</span><span class="sxs-lookup"><span data-stu-id="48078-128">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="48078-129">Le **DataTable** contient une ligne pour chaque colonne du jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="48078-129">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="48078-130">Chaque colonne de la ligne de table de schéma mappe à une propriété de la colonne retournée dans le jeu de résultats, où le **ColumnName** est le nom de la propriété et la valeur de la colonne est la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="48078-130">Each column of the schema table row maps to a property of the column returned in the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="48078-131">L’exemple de code suivant écrit les informations de schéma **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="48078-131">The following code example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="48078-132">Utilisation de chapitres OLE DB</span><span class="sxs-lookup"><span data-stu-id="48078-132">Working with OLE DB Chapters</span></span>  
 <span data-ttu-id="48078-133">Ensembles de lignes hiérarchiques ou chapitres (type OLE DB **DBTYPE_HCHAPTER**, type ADO **adChapter**) peuvent être récupérés à l’aide de la <xref:System.Data.OleDb.OleDbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="48078-133">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**) can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="48078-134">Lorsqu’une requête comprenant un chapitre est retournée comme un **DataReader**, le chapitre est retourné comme colonne dans ce **DataReader** et est exposé comme un **DataReader** objet.</span><span class="sxs-lookup"><span data-stu-id="48078-134">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="48078-135">ADO.NET **DataSet** peut également être utilisé pour représenter des jeux de lignes hiérarchiques à l’aide de relations parent-enfant entre les tables.</span><span class="sxs-lookup"><span data-stu-id="48078-135">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets using parent-child relationships between tables.</span></span> <span data-ttu-id="48078-136">Pour plus d’informations, consultez [DataSets, DataTables et DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="48078-136">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="48078-137">L'exemple de code suivant utilise le fournisseur MSDataShape pour générer une colonne chapitre de commandes pour chaque client d'une liste de clients.</span><span class="sxs-lookup"><span data-stu-id="48078-137">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="48078-138">Retour de résultats avec des REF CURSOR Oracle</span><span class="sxs-lookup"><span data-stu-id="48078-138">Returning Results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="48078-139">Le fournisseur de données .NET Framework pour Oracle prend en charge l'utilisation des REF CURSOR Oracle pour retourner le résultat d'une requête.</span><span class="sxs-lookup"><span data-stu-id="48078-139">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="48078-140">Un REF CURSOR Oracle est retourné en tant qu'objet <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="48078-140">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="48078-141">Vous pouvez récupérer un **OracleDataReader** objet qui représente un REF CURSOR Oracle à l’aide de la <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> (méthode) et vous pouvez également spécifier un <xref:System.Data.OracleClient.OracleCommand> qui retourne un ou plusieurs REF CURSOR Oracle en tant que le  **SelectCommand** pour un <xref:System.Data.OracleClient.OracleDataAdapter> utilisé pour remplir un <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="48078-141">You can retrieve an **OracleDataReader** object, that represents an Oracle REF CURSOR using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method, and you can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="48078-142">Pour accéder à un REF CURSOR retourné à partir d’une source de données Oracle, créez un **OracleCommand** pour votre requête et ajoutez un paramètre de sortie qui référence le REF CURSOR à la **paramètres** collection de votre  **OracleCommand**.</span><span class="sxs-lookup"><span data-stu-id="48078-142">To access a REF CURSOR returned from an Oracle data source, create an **OracleCommand** for your query and add an output parameter that references the REF CURSOR to the **Parameters** collection of your **OracleCommand**.</span></span> <span data-ttu-id="48078-143">Le nom du paramètre doit correspondre à celui du paramètre REF CURSOR de votre requête.</span><span class="sxs-lookup"><span data-stu-id="48078-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="48078-144">Définir le type du paramètre à **OracleType.Cursor**.</span><span class="sxs-lookup"><span data-stu-id="48078-144">Set the type of the parameter to **OracleType.Cursor**.</span></span> <span data-ttu-id="48078-145">Le **ExecuteReader** méthode de votre **OracleCommand** retournera un **OracleDataReader** pour REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="48078-145">The **ExecuteReader** method of your **OracleCommand** will return an **OracleDataReader** for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="48078-146">Si votre **OracleCommand** retourne plusieurs REF CURSOR, ajoutez plusieurs paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="48078-146">If your **OracleCommand** returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="48078-147">Vous pouvez accéder aux différents REF CURSOR en appelant le **OracleCommand.ExecuteReader** (méthode).</span><span class="sxs-lookup"><span data-stu-id="48078-147">You can access the different REF CURSORs by calling the **OracleCommand.ExecuteReader** method.</span></span> <span data-ttu-id="48078-148">L’appel à **ExecuteReader** retourne un **OracleDataReader** qui référence le premier REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="48078-148">The call to **ExecuteReader** returns an **OracleDataReader** referencing the first REF CURSOR.</span></span> <span data-ttu-id="48078-149">Vous pouvez ensuite appeler la **OracleDataReader.NextResult** méthode pour accéder aux REF CURSOR suivants.</span><span class="sxs-lookup"><span data-stu-id="48078-149">You can then call the **OracleDataReader.NextResult** method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="48078-150">Bien que les paramètres de votre **OracleCommand.Parameters** collection le REF CURSOR paramètres de sortie par son nom, le **OracleDataReader** y accède selon l’ordre qu’ils ont été ajoutés à la  **Paramètres** collection.</span><span class="sxs-lookup"><span data-stu-id="48078-150">Although the parameters in your **OracleCommand.Parameters** collection match the REF CURSOR output parameters by name, the **OracleDataReader** accesses them in the order that they were added to the **Parameters** collection.</span></span>  
  
 <span data-ttu-id="48078-151">Considérez, par exemple, le package et le corps de package Oracle suivants.</span><span class="sxs-lookup"><span data-stu-id="48078-151">For example, consider the following Oracle package and package body.</span></span>  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 <span data-ttu-id="48078-152">Le code suivant crée un **OracleCommand** qui retourne les REF CURSOR d’un précédent package Oracle en ajoutant deux paramètres de type **OracleType.Cursor** à le **paramètres** collection.</span><span class="sxs-lookup"><span data-stu-id="48078-152">The following code creates an **OracleCommand** that returns the REF CURSORs from the previous Oracle package by adding two parameters of type **OracleType.Cursor** to the **Parameters** collection.</span></span>  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 <span data-ttu-id="48078-153">Le code suivant retourne les résultats de la commande précédente à l’aide du **en lecture** et **NextResult** méthodes de la **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="48078-153">The following code returns the results of the previous command using the **Read** and **NextResult** methods of the **OracleDataReader**.</span></span> <span data-ttu-id="48078-154">Les paramètres REF CURSOR sont retournés dans l'ordre.</span><span class="sxs-lookup"><span data-stu-id="48078-154">The REF CURSOR parameters are returned in order.</span></span>  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 <span data-ttu-id="48078-155">L’exemple suivant utilise la commande précédente pour remplir un **DataSet** avec les résultats du package Oracle.</span><span class="sxs-lookup"><span data-stu-id="48078-155">The following example uses the previous command to populate a **DataSet** with the results of the Oracle package.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48078-156">Pour éviter un **OverflowException**, nous vous recommandons d’également gérer toute conversion à partir du type Oracle NUMBER en un type .NET Framework valide avant de stocker la valeur dans un **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="48078-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a **DataRow**.</span></span> <span data-ttu-id="48078-157">Vous pouvez utiliser la **FillError** événement pour déterminer si une **OverflowException** s’est produite.</span><span class="sxs-lookup"><span data-stu-id="48078-157">You can use the **FillError** event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="48078-158">Pour plus d’informations sur la **FillError** événements, consultez [gestion des événements DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="48078-158">For more information on the **FillError** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## <a name="see-also"></a><span data-ttu-id="48078-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48078-159">See Also</span></span>  
 [<span data-ttu-id="48078-160">Utilisation de DataReaders</span><span class="sxs-lookup"><span data-stu-id="48078-160">Working with DataReaders</span></span>](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="48078-161">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="48078-161">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="48078-162">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="48078-162">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="48078-163">La récupération des informations de schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="48078-163">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="48078-164">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="48078-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
