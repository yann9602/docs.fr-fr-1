---
title: "Ajout de contraintes existantes à un DataSet"
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
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fd760cf51aa0f3e89e49831b1aa165e62b321d20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="3f857-102">Ajout de contraintes existantes à un DataSet</span><span class="sxs-lookup"><span data-stu-id="3f857-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="3f857-103">Le **remplir** méthode de la **DataAdapter** remplit un <xref:System.Data.DataSet> uniquement avec les colonnes des tables et des lignes à partir d’une source de données ; bien que les contraintes soient généralement définies par la source de données, le **deremplissage** méthode n’ajoute pas ces informations de schéma pour le **DataSet** par défaut.</span><span class="sxs-lookup"><span data-stu-id="3f857-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="3f857-104">Pour remplir un **DataSet** avec les informations de contrainte de clé primaire existante à partir d’une source de données, vous pouvez appeler la **FillSchema** méthode de la **DataAdapter**, ou définir le **MissingSchemaAction** propriété de la **DataAdapter** à **AddWithKey** avant d’appeler **remplir**.</span><span class="sxs-lookup"><span data-stu-id="3f857-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="3f857-105">Cela permet de garantir cette clé primaire contraintes dans les **DataSet** reflètent celles de la source de données.</span><span class="sxs-lookup"><span data-stu-id="3f857-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="3f857-106">Les informations de contrainte de clé étrangère n’est pas incluses et doivent être créées explicitement, comme indiqué dans [contraintes DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="3f857-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="3f857-107">Ajout d’informations de schéma à un **DataSet** avant de remplir avec les données garantit que les contraintes de clé primaire sont incluses avec le <xref:System.Data.DataTable> des objets dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="3f857-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="3f857-108">Par conséquent, lorsqu’une appels pour remplir le **DataSet** sont effectuées, le serveur principal les informations de colonne clé sont utilisées pour faire correspondre les nouvelles lignes de la source de données avec les lignes actuelles de chaque **DataTable**et les données actuelles dans les tables sont remplacées par les données à partir de la source de données.</span><span class="sxs-lookup"><span data-stu-id="3f857-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="3f857-109">Sans les informations de schéma, les nouvelles lignes à partir de la source de données sont ajoutées à la **DataSet**, se traduisant par des lignes en double.</span><span class="sxs-lookup"><span data-stu-id="3f857-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f857-110">Si une colonne dans une source de données est identifiée en tant que l’incrémentation automatique, le **FillSchema** (méthode), ou le **remplir** méthode avec un **MissingSchemaAction** de  **AddWithKey**, crée un **DataColumn** avec un **AutoIncrement** propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="3f857-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="3f857-111">Toutefois, vous devez définir le **AutoIncrementStep** et **AutoIncrementSeed** vous-même les valeurs.</span><span class="sxs-lookup"><span data-stu-id="3f857-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="3f857-112">Pour plus d’informations sur les colonnes à incrémentation automatique, consultez [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="3f857-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="3f857-113">À l’aide de **FillSchema** ou le **MissingSchemaAction** à **AddWithKey** nécessite un traitement supplémentaire à la source de données pour déterminer les informations de colonne de clé primaire.</span><span class="sxs-lookup"><span data-stu-id="3f857-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="3f857-114">Ce traitement supplémentaire peut gêner la performance.</span><span class="sxs-lookup"><span data-stu-id="3f857-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="3f857-115">Si vous connaissez les informations de clé primaire au moment du design, il est recommandé de spécifier explicitement la ou les colonnes de clé primaire afin d'atteindre une performance optimale.</span><span class="sxs-lookup"><span data-stu-id="3f857-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="3f857-116">Pour plus d’informations sur la définition explicite des informations de clé primaire pour une table, consultez [définition des clés primaires](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="3f857-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="3f857-117">L’exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** à l’aide de **FillSchema**.</span><span class="sxs-lookup"><span data-stu-id="3f857-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 <span data-ttu-id="3f857-118">L’exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** à l’aide de la **MissingSchemaAction.AddWithKey** propriété de la **remplir** (méthode).</span><span class="sxs-lookup"><span data-stu-id="3f857-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="3f857-119">Gestion de jeux de résultats multiples</span><span class="sxs-lookup"><span data-stu-id="3f857-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="3f857-120">Si le **DataAdapter** rencontre plusieurs jeux de résultats retournés à partir de la **SelectCommand**, il créera plusieurs tables dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="3f857-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="3f857-121">Les tables recevront un nom de base zéro incrémentiel par défaut de **Table** *N*, en commençant par **Table** au lieu de « Table0 ».</span><span class="sxs-lookup"><span data-stu-id="3f857-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="3f857-122">Si un nom de table est passé comme argument à la **FillSchema** (méthode), les tables recevront un nom incrémentiel de base zéro de **TableName** *N*, en commençant par **TableName** au lieu de « TableName0 ».</span><span class="sxs-lookup"><span data-stu-id="3f857-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f857-123">Si le **FillSchema** méthode de la **OleDbDataAdapter** objet est appelé pour une commande qui retourne plusieurs jeux de résultats, les informations de schéma du premier jeu de résultats sont retournées.</span><span class="sxs-lookup"><span data-stu-id="3f857-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="3f857-124">Lorsque retournant des informations de schéma pour plusieurs résultats définit à l’aide de la **OleDbDataAdapter**, il est recommandé de spécifier un **MissingSchemaAction** de **AddWithKey** et obtenir les informations de schéma lors de l’appel du **remplir** (méthode).</span><span class="sxs-lookup"><span data-stu-id="3f857-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f857-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f857-125">See Also</span></span>  
 [<span data-ttu-id="3f857-126">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="3f857-126">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="3f857-127">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="3f857-127">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="3f857-128">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3f857-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="3f857-129">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="3f857-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
