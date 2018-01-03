---
title: REF CURSOR Oracle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 27351c1d47d4ad40940e5b64f257e6a59fc7403a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="b3a83-102">REF CURSOR Oracle</span><span class="sxs-lookup"><span data-stu-id="b3a83-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="b3a83-103">Le fournisseur de données .NET Framework pour Oracle prend en charge Oracle **REF CURSOR** type de données.</span><span class="sxs-lookup"><span data-stu-id="b3a83-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="b3a83-104">Lorsque vous utilisez le fournisseur de données pour travailler avec des REF CURSOR Oracle, vous devez tenir compte des comportements suivants.</span><span class="sxs-lookup"><span data-stu-id="b3a83-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3a83-105">Certains comportements diffèrent de ceux du fournisseur Microsoft OLE DB pour Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="b3a83-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
-   <span data-ttu-id="b3a83-106">Pour des raisons de performances, le fournisseur de données pour Oracle ne lie pas automatiquement **REF CURSOR** types de données, comme le fait MSDAORA, sauf si vous les spécifiez explicitement.</span><span class="sxs-lookup"><span data-stu-id="b3a83-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
-   <span data-ttu-id="b3a83-107">Le fournisseur de données ne prend pas en charge les séquences d'échappement ODBC, notamment l'échappement {resultset} utilisé pour spécifier les paramètres REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="b3a83-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="b3a83-108">Pour exécuter une procédure stockée qui retourne les REF CURSOR, vous devez définir les paramètres dans le <xref:System.Data.OracleClient.OracleParameterCollection> avec un <xref:System.Data.OracleClient.OracleType> de **curseur** et un <xref:System.Data.OracleClient.OracleParameter.Direction%2A> de **sortie**.</span><span class="sxs-lookup"><span data-stu-id="b3a83-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="b3a83-109">Le fournisseur de données prend en charge la liaison des REF CURSOR en tant que paramètres de sortie seulement.</span><span class="sxs-lookup"><span data-stu-id="b3a83-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="b3a83-110">Le fournisseur ne prend pas en charge les REF CURSOR en tant que paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="b3a83-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
-   <span data-ttu-id="b3a83-111">L'obtention d'un <xref:System.Data.OracleClient.OracleDataReader> à partir de la valeur de paramètre n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="b3a83-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="b3a83-112">Les valeurs sont de type <xref:System.DBNull> après l'exécution d'une commande.</span><span class="sxs-lookup"><span data-stu-id="b3a83-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
-   <span data-ttu-id="b3a83-113">La seule **CommandBehavior** valeur d’énumération qui fonctionne avec des REF CURSOR (par exemple, lors de l’appel <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) est **CloseConnection**; tous les autres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="b3a83-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
-   <span data-ttu-id="b3a83-114">L’ordre des REF CURSOR dans le **OracleDataReader** dépend de l’ordre des paramètres dans le **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="b3a83-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="b3a83-115">La propriété <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> est ignorée.</span><span class="sxs-lookup"><span data-stu-id="b3a83-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
-   <span data-ttu-id="b3a83-116">PL/SQL **TABLE** type de données n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b3a83-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="b3a83-117">Toutefois, les REF CURSOR sont plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="b3a83-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="b3a83-118">Si vous devez utiliser un **TABLE** type de données, utilisez le fournisseur de données OLE DB .NET avec MSDAORA.</span><span class="sxs-lookup"><span data-stu-id="b3a83-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3a83-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b3a83-119">In This Section</span></span>  
 [<span data-ttu-id="b3a83-120">Exemples REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="b3a83-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="b3a83-121">Contient trois exemples qui illustrent l'utilisation des REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="b3a83-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="b3a83-122">Paramètres REF CURSOR dans un OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="b3a83-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="b3a83-123">Montre comment exécuter une procédure stockée PL/SQL qui retourne un paramètre REF CURSOR et lit la valeur comme un **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="b3a83-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="b3a83-124">Récupération de données à partir de plusieurs REF CURSOR à l’aide d’un OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="b3a83-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="b3a83-125">Montre comment exécuter une procédure stockée PL/SQL qui retourne deux paramètres REF CURSOR et lit les valeurs en utilisant un **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="b3a83-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="b3a83-126">Remplissage d’un DataSet à l’aide d’un ou de plusieurs REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="b3a83-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="b3a83-127">Montre comment exécuter une procédure stockée PL/SQL qui retourne deux paramètres REF CURSOR et remplit un <xref:System.Data.DataSet> avec les lignes qui sont retournées.</span><span class="sxs-lookup"><span data-stu-id="b3a83-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a83-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3a83-128">See Also</span></span>  
 [<span data-ttu-id="b3a83-129">Oracle et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b3a83-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="b3a83-130">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="b3a83-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
