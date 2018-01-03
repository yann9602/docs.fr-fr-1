---
title: "Grands types définis par l'utilisateur"
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
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 876ebeb5568ffff0a10aa5a54ce96c256d237d86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="large-udts"></a><span data-ttu-id="5701b-102">Grands types définis par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5701b-102">Large UDTs</span></span>
<span data-ttu-id="5701b-103">Les types définis par l'utilisateur (UDT, User-Defined Types) permettent à un développeur d'étendre le système de type scalaire du serveur, en stockant des objets CLR (Common Language Runtime) dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5701b-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="5701b-104">Les UDT peuvent contenir plusieurs éléments et, contrairement aux types de données alias traditionnels, avoir des comportements qui consistent en un unique type de données système SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5701b-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5701b-105">Vous devez installer le .NET Framework 3.5 SP1 (ou version ultérieure) pour tirer parti de la prise en charge améliorée de SqlClient pour les UDT volumineux.</span><span class="sxs-lookup"><span data-stu-id="5701b-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="5701b-106">Auparavant, les UDT étaient limités à une taille maximale de 8 Ko.</span><span class="sxs-lookup"><span data-stu-id="5701b-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="5701b-107">Dans SQL Server 2008, cette restriction a été supprimée pour les UDT ayant un format <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="5701b-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="5701b-108">Pour la documentation complète relative aux types définis par l'utilisateur, consultez la version de la documentation en ligne de SQL Server correspondant à la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="5701b-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="5701b-109">**Documentation en ligne de SQL Server**</span><span class="sxs-lookup"><span data-stu-id="5701b-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="5701b-110">Types CLR définis par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="5701b-110">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="5701b-111">Récupération de schémas UDT à l'aide de GetSchema</span><span class="sxs-lookup"><span data-stu-id="5701b-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="5701b-112">La méthode <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> de <xref:System.Data.SqlClient.SqlConnection> retourne les informations de schéma de la base de données dans un objet <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="5701b-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="5701b-113">Pour plus d’informations, consultez [Collections de schémas SQL Server](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="5701b-113">For more information, see [SQL Server Schema Collections](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="5701b-114">Valeurs de colonne GetSchemaTable Column pour les UDT</span><span class="sxs-lookup"><span data-stu-id="5701b-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="5701b-115">La méthode <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> d'un objet <xref:System.Data.SqlClient.SqlDataReader> retourne un objet <xref:System.Data.DataTable> qui décrit les métadonnées des colonnes.</span><span class="sxs-lookup"><span data-stu-id="5701b-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="5701b-116">Le tableau suivant décrit les différences dans les métadonnées des colonnes pour les UDT volumineux entre SQL Server 2005 et SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="5701b-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="5701b-117">Colonne SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="5701b-117">SqlDataReader column</span></span>|<span data-ttu-id="5701b-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="5701b-118">SQL Server 2005</span></span>|<span data-ttu-id="5701b-119">SQL Server 2008 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="5701b-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="5701b-120">Selon le cas</span><span class="sxs-lookup"><span data-stu-id="5701b-120">Varies</span></span>|<span data-ttu-id="5701b-121">Selon le cas</span><span class="sxs-lookup"><span data-stu-id="5701b-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="5701b-122">255</span><span class="sxs-lookup"><span data-stu-id="5701b-122">255</span></span>|<span data-ttu-id="5701b-123">255</span><span class="sxs-lookup"><span data-stu-id="5701b-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="5701b-124">255</span><span class="sxs-lookup"><span data-stu-id="5701b-124">255</span></span>|<span data-ttu-id="5701b-125">255</span><span class="sxs-lookup"><span data-stu-id="5701b-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="5701b-126">Instance UDT</span><span class="sxs-lookup"><span data-stu-id="5701b-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="5701b-127">Instance UDT</span><span class="sxs-lookup"><span data-stu-id="5701b-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="5701b-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="5701b-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="5701b-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="5701b-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="5701b-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="5701b-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="5701b-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="5701b-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="5701b-132">Nom spécifié en tant qu’en trois parties *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="5701b-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="5701b-133">Selon le cas</span><span class="sxs-lookup"><span data-stu-id="5701b-133">Varies</span></span>|<span data-ttu-id="5701b-134">Selon le cas</span><span class="sxs-lookup"><span data-stu-id="5701b-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="5701b-135">Considérations relatives à SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="5701b-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="5701b-136">L'objet <xref:System.Data.SqlClient.SqlDataReader> a été étendu depuis SQL Server 2008 pour prendre en charge la récupération des valeurs UDT volumineuses.</span><span class="sxs-lookup"><span data-stu-id="5701b-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="5701b-137">La manière dont un <xref:System.Data.SqlClient.SqlDataReader> traite les valeurs UDT volumineuses par dépend de la version de SQL Server que vous utilisez, ainsi que du `Type System Version` spécifié dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="5701b-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="5701b-138">Pour plus d'informations, consultez <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="5701b-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="5701b-139">Les méthodes suivantes de <xref:System.Data.SqlClient.SqlDataReader> retournent un <xref:System.Data.SqlTypes.SqlBinary> au lieu d'un type défini par l'utilisateur lorsque `Type System Version` est défini à SQL Server 2005 :</span><span class="sxs-lookup"><span data-stu-id="5701b-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="5701b-140">Les méthodes suivantes retournent un tableau de `Byte[]` au lieu d'un UDT lorsque `Type System Version` est défini à SQL Server 2005 :</span><span class="sxs-lookup"><span data-stu-id="5701b-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="5701b-141">Notez qu'aucune conversion n'est effectuée pour la version actuelle d'ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="5701b-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="5701b-142">Spécification de SqlParameters</span><span class="sxs-lookup"><span data-stu-id="5701b-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="5701b-143">Les propriétés <xref:System.Data.SqlClient.SqlParameter> suivantes ont été étendues pour fonctionner avec des UDT volumineux.</span><span class="sxs-lookup"><span data-stu-id="5701b-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="5701b-144">Propriété SqlParameter</span><span class="sxs-lookup"><span data-stu-id="5701b-144">SqlParameter Property</span></span>|<span data-ttu-id="5701b-145">Description</span><span class="sxs-lookup"><span data-stu-id="5701b-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="5701b-146">Obtient ou définit un objet qui représente la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="5701b-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="5701b-147">La valeur par défaut correspond à la valeur null.</span><span class="sxs-lookup"><span data-stu-id="5701b-147">The default is null.</span></span> <span data-ttu-id="5701b-148">La propriété peut être de type `SqlBinary`, `Byte[]` ou un objet managé.</span><span class="sxs-lookup"><span data-stu-id="5701b-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="5701b-149">Obtient ou définit un objet qui représente la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="5701b-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="5701b-150">La valeur par défaut correspond à la valeur null.</span><span class="sxs-lookup"><span data-stu-id="5701b-150">The default is null.</span></span> <span data-ttu-id="5701b-151">La propriété peut être de type `SqlBinary`, `Byte[]` ou un objet managé.</span><span class="sxs-lookup"><span data-stu-id="5701b-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="5701b-152">Obtient ou définit la taille de la valeur de paramètre à résoudre.</span><span class="sxs-lookup"><span data-stu-id="5701b-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="5701b-153">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="5701b-153">The default value is 0.</span></span> <span data-ttu-id="5701b-154">La propriété peut être un nombre entier qui représente la taille de la valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="5701b-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="5701b-155">Pour les UDT volumineux, il peut s'agir de la taille réelle de l'UDT ou -1 pour inconnu.</span><span class="sxs-lookup"><span data-stu-id="5701b-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="5701b-156">Exemple d'extraction de données</span><span class="sxs-lookup"><span data-stu-id="5701b-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="5701b-157">Le fragment de code suivant montre comment extraire des données UDT volumineuses.</span><span class="sxs-lookup"><span data-stu-id="5701b-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="5701b-158">La variable `connectionString` suppose une connexion valide à une base de données SQL Server, et la variable `commandString` suppose une instruction SELECT valide avec la colonne de clé primaire apparaissant en premier.</span><span class="sxs-lookup"><span data-stu-id="5701b-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
```csharp  
using (SqlConnection connection = new SqlConnection(   
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="5701b-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5701b-159">See Also</span></span>  
 [<span data-ttu-id="5701b-160">Configuration des paramètres et des types de données des paramètres</span><span class="sxs-lookup"><span data-stu-id="5701b-160">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="5701b-161">Récupération des informations de schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="5701b-161">Retrieving Database Schema Information</span></span>](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="5701b-162">Mappages de types de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="5701b-162">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="5701b-163">Données binaires et de valeur élevée SQL Server</span><span class="sxs-lookup"><span data-stu-id="5701b-163">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="5701b-164">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="5701b-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
