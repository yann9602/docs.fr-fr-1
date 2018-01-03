---
title: "Ajout de colonnes à un DataTable"
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
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 423b9ed389a5a3750c8e9b0339e0887d6b650741
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="436b9-102">Ajout de colonnes à un DataTable</span><span class="sxs-lookup"><span data-stu-id="436b9-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="436b9-103">A <xref:System.Data.DataTable> contient une collection de <xref:System.Data.DataColumn> objets référencés par le **colonnes** propriété de la table.</span><span class="sxs-lookup"><span data-stu-id="436b9-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="436b9-104">Cette collection de colonnes, ainsi que toute contrainte, définit le schéma, ou structure, de la table.</span><span class="sxs-lookup"><span data-stu-id="436b9-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="436b9-105">Vous créez **DataColumn** objets au sein d’une table à l’aide de la **DataColumn** constructeur, ou en appelant le **ajouter** méthode de la **colonnes**propriété de la table, qui est un <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="436b9-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="436b9-106">Le **ajouter** méthode accepte facultatif **ColumnName**, **DataType**, et **Expression** arguments et crée un nouveau  **DataColumn** en tant que membre de la collection.</span><span class="sxs-lookup"><span data-stu-id="436b9-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="436b9-107">Elle accepte également un existant **DataColumn** de l’objet et l’ajoute à la collection et retourne une référence à l’ajout **DataColumn** si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="436b9-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="436b9-108">Étant donné que **DataTable** objets ne sont pas spécifiques à n’importe quelle source de données, les types .NET Framework sont utilisées lorsque vous spécifiez le type de données d’une **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="436b9-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="436b9-109">L’exemple suivant ajoute quatre colonnes à un **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="436b9-109">The following example adds four columns to a **DataTable**.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 <span data-ttu-id="436b9-110">Dans l’exemple, notez que les propriétés de la **CustID** colonne sont définies pour ne pas autoriser **DBNull** valeurs et à limiter les valeurs soient uniques.</span><span class="sxs-lookup"><span data-stu-id="436b9-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="436b9-111">Toutefois, si vous définissez la **CustID** colonne en tant que la colonne de clé primaire de la table, la **AllowDBNull** propriété sera automatiquement la valeur **false** et le **Unique** propriété sera automatiquement la valeur **true**.</span><span class="sxs-lookup"><span data-stu-id="436b9-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="436b9-112">Pour plus d’informations, consultez [définition des clés primaires](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="436b9-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="436b9-113">Si un nom de colonne n’est pas fourni pour une colonne, la colonne reçoit un nom incrémentiel par défaut de la colonne*N,* commençant par « Column1 », lorsqu’il est ajouté à la **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="436b9-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="436b9-114">Nous vous recommandons d’éviter la convention d’affectation de noms de « colonne*N*» lorsque vous fournissez un nom de colonne, car le nom fourni peut entrer en conflit avec un nom de colonne par défaut existant dans le **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="436b9-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="436b9-115">Si le nom fourni existe déjà, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="436b9-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="436b9-116">Si vous utilisez <xref:System.Xml.Linq.XElement> en tant que <xref:System.Data.DataColumn.DataType%2A> d'un <xref:System.Data.DataColumn> dans <xref:System.Data.DataTable>, la sérialisation XML ne fonctionnera pas lors de la lecture dans les données.</span><span class="sxs-lookup"><span data-stu-id="436b9-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="436b9-117">Par exemple, si vous écrivez un <xref:System.Xml.XmlDocument> à l'aide de la méthode `DataTable.WriteXml`, lors de la sérialisation vers XML, un nœud parent supplémentaire est ajouté dans le <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="436b9-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="436b9-118">Pour contourner ce problème, utilisez le type <xref:System.Data.SqlTypes.SqlXml> à la place de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="436b9-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="436b9-119">`ReadXml` et `WriteXml` fonctionnent correctement avec <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="436b9-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="436b9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="436b9-120">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="436b9-121">Définition de schéma de DataTable</span><span class="sxs-lookup"><span data-stu-id="436b9-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="436b9-122">DataTables</span><span class="sxs-lookup"><span data-stu-id="436b9-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="436b9-123">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="436b9-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
