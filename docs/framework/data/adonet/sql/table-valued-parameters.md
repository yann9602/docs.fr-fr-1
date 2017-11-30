---
title: "Paramètres table"
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
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47956848079e6094dc000d95ec4066f814a70e35
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="table-valued-parameters"></a><span data-ttu-id="ddde2-102">Paramètres table</span><span class="sxs-lookup"><span data-stu-id="ddde2-102">Table-Valued Parameters</span></span>
<span data-ttu-id="ddde2-103">Les paramètres table fournissent un moyen simple de marshaler plusieurs lignes de données d'une application cliente vers [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] sans avoir recours à plusieurs allers-retours ou à une logique côté serveur spéciale pour le traitement des données.</span><span class="sxs-lookup"><span data-stu-id="ddde2-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="ddde2-104">Les paramètres table vous permettent d'encapsuler des lignes de données dans une application cliente et d'envoyer les données au serveur dans une commande paramétrée unique.</span><span class="sxs-lookup"><span data-stu-id="ddde2-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="ddde2-105">Les lignes de données entrantes sont stockées dans une variable de table qui peut ensuite être traitée en utilisant [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ddde2-105">The incoming data rows are stored in a table variable that can then be operated on by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ddde2-106">Les valeurs de colonne dans les paramètres table sont accessibles à l'aide d'instructions [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT standard.</span><span class="sxs-lookup"><span data-stu-id="ddde2-106">Column values in table-valued parameters can be accessed using standard [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT statements.</span></span> <span data-ttu-id="ddde2-107">Les paramètres table sont fortement typés et leur structure est automatiquement validée.</span><span class="sxs-lookup"><span data-stu-id="ddde2-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="ddde2-108">La taille des paramètres table est uniquement limitée par la mémoire du serveur.</span><span class="sxs-lookup"><span data-stu-id="ddde2-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddde2-109">Vous ne pouvez pas retourner de données dans un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="ddde2-110">Les paramètres table sont des paramètres d'entrée uniquement ; le mot clé OUTPUT n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ddde2-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="ddde2-111">Pour plus d'informations sur l'utilisation des paramètres table, consultez les ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="ddde2-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="ddde2-112">Ressource</span><span class="sxs-lookup"><span data-stu-id="ddde2-112">Resource</span></span>|<span data-ttu-id="ddde2-113">Description</span><span class="sxs-lookup"><span data-stu-id="ddde2-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ddde2-114">[Paramètres table (moteur de base de données)](http://go.microsoft.com/fwlink/?LinkId=98363) dans [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] la documentation en ligne</span><span class="sxs-lookup"><span data-stu-id="ddde2-114">[Table-Valued Parameters (Database Engine)](http://go.microsoft.com/fwlink/?LinkId=98363) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="ddde2-115">Décrit comment créer et utiliser des paramètres table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="ddde2-116">[Types de tables définis par l’utilisateur](http://go.microsoft.com/fwlink/?LinkId=98364) dans [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] la documentation en ligne</span><span class="sxs-lookup"><span data-stu-id="ddde2-116">[User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkId=98364) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="ddde2-117">Décrit les types de tables définis par l'utilisateur qui permettent de déclarer des paramètres table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="ddde2-118">Passage de plusieurs lignes dans les versions précédentes de SQL Server</span><span class="sxs-lookup"><span data-stu-id="ddde2-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="ddde2-119">Avant l'introduction des paramètres table dans [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008, les options permettant de passer plusieurs lignes de données à une procédure stockée ou à une commande SQL paramétrée étaient limitées.</span><span class="sxs-lookup"><span data-stu-id="ddde2-119">Before table-valued parameters were introduced to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="ddde2-120">Un développeur pouvait choisir parmi les options suivantes pour passer plusieurs lignes au serveur :</span><span class="sxs-lookup"><span data-stu-id="ddde2-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
-   <span data-ttu-id="ddde2-121">Utiliser une série de paramètres individuels pour représenter les valeurs dans plusieurs colonnes et lignes de données.</span><span class="sxs-lookup"><span data-stu-id="ddde2-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="ddde2-122">La quantité des données qui peuvent être passées à l'aide de cette méthode est limitée par le nombre de paramètres autorisés.</span><span class="sxs-lookup"><span data-stu-id="ddde2-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="ddde2-123">Les procédures [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] peuvent contenir jusqu'à 2 100 paramètres.</span><span class="sxs-lookup"><span data-stu-id="ddde2-123">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="ddde2-124">La logique côté serveur est requise pour assembler ces valeurs individuelles dans une variable de table ou dans une table temporaire à des fins de traitement.</span><span class="sxs-lookup"><span data-stu-id="ddde2-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
-   <span data-ttu-id="ddde2-125">Regrouper plusieurs valeurs de données dans des chaînes délimitées ou des documents XML, puis passer ces valeurs texte à une procédure ou à une instruction.</span><span class="sxs-lookup"><span data-stu-id="ddde2-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="ddde2-126">Cela implique pour la procédure ou l'instruction d'inclure la logique nécessaire permettant de valider les structures de données et de dégrouper les valeurs.</span><span class="sxs-lookup"><span data-stu-id="ddde2-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
-   <span data-ttu-id="ddde2-127">Créer une série d'instructions SQL individuelles pour les modifications de données qui affectent plusieurs lignes, telles que celles créées en appelant la méthode `Update` d'un objet <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="ddde2-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="ddde2-128">Les modifications peuvent être soumises au serveur individuellement ou être traitées par lot dans des groupes.</span><span class="sxs-lookup"><span data-stu-id="ddde2-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="ddde2-129">Cependant, même lorsqu'elles sont soumises dans des lots qui contiennent plusieurs instructions, chaque instruction est exécutée séparément sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="ddde2-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
-   <span data-ttu-id="ddde2-130">Utiliser l'utilitaire `bcp` ou l'objet <xref:System.Data.SqlClient.SqlBulkCopy> pour charger plusieurs lignes de données dans une table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="ddde2-131">Même si cette technique est très efficace, elle ne prend pas en charge le traitement côté serveur sauf si les données sont chargées dans une table temporaire ou dans une variable de table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="ddde2-132">Création de types de paramètre table</span><span class="sxs-lookup"><span data-stu-id="ddde2-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="ddde2-133">Les paramètres table sont basés sur des structures de table fortement typées qui sont définies à l'aide des instructions  [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE.</span><span class="sxs-lookup"><span data-stu-id="ddde2-133">Table-valued parameters are based on strongly-typed table structures that are defined by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE statements.</span></span> <span data-ttu-id="ddde2-134">Vous devez créer un type de table et définir la structure dans [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] avant de pouvoir utiliser les paramètres table dans vos applications clientes.</span><span class="sxs-lookup"><span data-stu-id="ddde2-134">You have to create a table type and define the structure in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="ddde2-135">Pour plus d’informations sur la création des types de tables, consultez [les Types de tables définis par l’utilisateur](http://go.microsoft.com/fwlink/?LinkID=98364) dans [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] la documentation en ligne.</span><span class="sxs-lookup"><span data-stu-id="ddde2-135">For more information about creating table types, see [User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkID=98364) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="ddde2-136">L'instruction suivante crée un type de table nommé CategoryTableType qui se compose des colonnes CategoryID et CategoryName :</span><span class="sxs-lookup"><span data-stu-id="ddde2-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="ddde2-137">Après avoir créé un type de table, vous pouvez déclarer des paramètres table basés sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="ddde2-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="ddde2-138">Le fragment [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] suivant montre comment déclarer un paramètre table dans une définition de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="ddde2-138">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="ddde2-139">Notez que le mot clé READONLY est obligatoire pour déclarer un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="ddde2-140">Modification des données à l'aide des paramètres table (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ddde2-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="ddde2-141">Des paramètres table peuvent être utilisés dans des modifications de données basées sur des jeux qui affectent plusieurs lignes en exécutant une instruction unique.</span><span class="sxs-lookup"><span data-stu-id="ddde2-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="ddde2-142">Par exemple, vous pouvez sélectionner toutes les lignes d'un paramètre table et les insérer dans une table de base de données, ou créer une instruction de mise à jour en joignant un paramètre table à la table à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="ddde2-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="ddde2-143">L'instruction  [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE suivante montre comment utiliser un paramètre table en le joignant à la table Categories.</span><span class="sxs-lookup"><span data-stu-id="ddde2-143">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="ddde2-144">Lorsque vous utilisez un paramètre table avec une condition JOIN dans une clause FROM, vous devez également créer des alias pour celui-ci, comme ci-après, où le paramètre table se voit attribuer l'alias "ec" :</span><span class="sxs-lookup"><span data-stu-id="ddde2-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="ddde2-145">Cet exemple [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] montre comment sélectionner des lignes d'un paramètre table pour effectuer une insertion (INSERT) dans une opération basée sur un jeu unique.</span><span class="sxs-lookup"><span data-stu-id="ddde2-145">This [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="ddde2-146">Limites des paramètres table</span><span class="sxs-lookup"><span data-stu-id="ddde2-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="ddde2-147">Les paramètres table présentent plusieurs limites :</span><span class="sxs-lookup"><span data-stu-id="ddde2-147">There are several limitations to table-valued parameters:</span></span>  
  
-   <span data-ttu-id="ddde2-148">Vous ne pouvez pas passer des paramètres table à [fonctions CLR définies par l’utilisateur](http://msdn.microsoft.com/library/ms131077.aspx).</span><span class="sxs-lookup"><span data-stu-id="ddde2-148">You cannot pass table-valued parameters to [CLR user-defined functions](http://msdn.microsoft.com/library/ms131077.aspx).</span></span>  
  
-   <span data-ttu-id="ddde2-149">Les paramètres table peuvent uniquement être indexés pour prendre en charge les contraintes UNIQUE ou PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="ddde2-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="ddde2-150"> ne gère pas les statistiques sur les paramètres table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-150"> does not maintain statistics on table-valued parameters.</span></span>  
  
-   <span data-ttu-id="ddde2-151">Les paramètres table sont en lecture seule dans le code [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ddde2-151">Table-valued parameters are read-only in [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="ddde2-152">Vous ne pouvez pas mettre les valeurs de colonne à jour dans les lignes d'un paramètre table et vous ne pouvez pas insérer ni supprimer de ligne.</span><span class="sxs-lookup"><span data-stu-id="ddde2-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="ddde2-153">Pour modifier les données qui sont passées à une procédure stockée ou à une instruction paramétrée dans un paramètre table, vous devez insérer les données dans une table temporaire ou dans une variable de table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
-   <span data-ttu-id="ddde2-154">Vous ne pouvez pas utiliser d'instruction ALTER TABLE pour modifier la conception des paramètres table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="ddde2-155">Exemple : configuration d'un SqlParameter</span><span class="sxs-lookup"><span data-stu-id="ddde2-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="ddde2-156"><xref:System.Data.SqlClient>prend en charge le remplissage des paramètres table à partir de <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> ou <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> objets.</span><span class="sxs-lookup"><span data-stu-id="ddde2-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="ddde2-157">Vous devez spécifier un nom de type pour le paramètre table à l'aide de la propriété <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> d'un objet <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="ddde2-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="ddde2-158">Le `TypeName` doit correspondre au nom d'un type compatible précédemment créé sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="ddde2-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="ddde2-159">Le fragment de code suivant montre comment configurer l'objet <xref:System.Data.SqlClient.SqlParameter> pour insérer des données.</span><span class="sxs-lookup"><span data-stu-id="ddde2-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
  
```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 <span data-ttu-id="ddde2-160">Vous pouvez également utiliser n'importe quel objet dérivé de l'objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table, tel qu'indiqué dans ce fragment :</span><span class="sxs-lookup"><span data-stu-id="ddde2-160">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><span data-ttu-id="ddde2-161">Passage d'un paramètre table à une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ddde2-161">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="ddde2-162">Cet exemple montre comment passer des données de paramètre table à une procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="ddde2-162">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="ddde2-163">Le code extrait les lignes ajoutées dans un nouvel objet <xref:System.Data.DataTable> à l'aide de la méthode <xref:System.Data.DataTable.GetChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="ddde2-163">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="ddde2-164">Le code définit ensuite un objet <xref:System.Data.SqlClient.SqlCommand>, en affectant <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> à la propriété <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="ddde2-164">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="ddde2-165"><xref:System.Data.SqlClient.SqlParameter> est rempli à l'aide de la méthode <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> et <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> a la valeur `Structured`.</span><span class="sxs-lookup"><span data-stu-id="ddde2-165">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="ddde2-166"><xref:System.Data.SqlClient.SqlCommand> est ensuite exécuté à l'aide de la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.</span><span class="sxs-lookup"><span data-stu-id="ddde2-166">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="ddde2-167">Passage d'un paramètre table à une instruction SQL paramétrée</span><span class="sxs-lookup"><span data-stu-id="ddde2-167">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="ddde2-168">L'exemple suivant montre comment insérer des données dans la table dbo.Categories à l'aide de l'instruction INSERT avec une sous-requête SELECT qui a un paramètre table comme source de données.</span><span class="sxs-lookup"><span data-stu-id="ddde2-168">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="ddde2-169">Lors du passage d'un paramètre table a une instruction SQL paramétrée, vous devez spécifier un nom de type pour le paramètre table à l'aide de la nouvelle propriété <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> d'un objet <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="ddde2-169">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="ddde2-170">Ce `TypeName` doit correspondre au nom d'un type compatible précédemment créé sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="ddde2-170">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="ddde2-171">Dans cet exemple, le code utilise la propriété `TypeName` pour référencer la structure de type définie dans dbo.CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="ddde2-171">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddde2-172">Si vous indiquez une valeur pour une colonne d'identité d'un paramètre table, vous devez émettre l'instruction SET IDENTITY_INSERT pour la session.</span><span class="sxs-lookup"><span data-stu-id="ddde2-172">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="ddde2-173">Diffusion en continu des lignes à l'aide d'un objet DataReader</span><span class="sxs-lookup"><span data-stu-id="ddde2-173">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="ddde2-174">Vous pouvez également utiliser n'importe quel objet dérivé de l'objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-174">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="ddde2-175">Le fragment de code suivant montre comment extraire des données d'une base de données Oracle à l'aide d'un objet <xref:System.Data.OracleClient.OracleCommand> et d'un objet <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="ddde2-175">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="ddde2-176">Le code configure ensuite un objet <xref:System.Data.SqlClient.SqlCommand> pour appeler une procédure stockée avec un paramètre d'entrée unique.</span><span class="sxs-lookup"><span data-stu-id="ddde2-176">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="ddde2-177">La propriété <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> de l'objet <xref:System.Data.SqlClient.SqlParameter> a la valeur `Structured`.</span><span class="sxs-lookup"><span data-stu-id="ddde2-177">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="ddde2-178"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passe le jeu de résultats `OracleDataReader` à la procédure stockée sous la forme d'un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="ddde2-178">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddde2-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddde2-179">See Also</span></span>  
 [<span data-ttu-id="ddde2-180">Configuration des paramètres et des Types de données de paramètre</span><span class="sxs-lookup"><span data-stu-id="ddde2-180">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="ddde2-181">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="ddde2-181">Commands and Parameters</span></span>](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="ddde2-182">Paramètres DataAdapter</span><span class="sxs-lookup"><span data-stu-id="ddde2-182">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [<span data-ttu-id="ddde2-183">Opérations sur les données SQL Server dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ddde2-183">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="ddde2-184">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="ddde2-184">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
