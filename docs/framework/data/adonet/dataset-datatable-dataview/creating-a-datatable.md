---
title: "Création d'un DataTable"
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
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 68f8272aa0f525c04120f129057e6151e42ffee1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-datatable"></a><span data-ttu-id="dac0f-102">Création d'un DataTable</span><span class="sxs-lookup"><span data-stu-id="dac0f-102">Creating a DataTable</span></span>
<span data-ttu-id="dac0f-103">Un objet <xref:System.Data.DataTable>, qui représente une table de données relationnelles en mémoire, peut être créé et utilisé de façon indépendante. Il peut également être utilisé par d'autres objets .NET Framework, la plupart du temps comme membre d'un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="dac0f-103">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="dac0f-104">Vous pouvez créer un **DataTable** objet en respectant **DataTable** constructeur.</span><span class="sxs-lookup"><span data-stu-id="dac0f-104">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="dac0f-105">Vous pouvez l’ajouter à la **DataSet** à l’aide de la **ajouter** méthode à ajouter à la **DataTable** l’objet **Tables** collection.</span><span class="sxs-lookup"><span data-stu-id="dac0f-105">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="dac0f-106">Vous pouvez également créer **DataTable** objets au sein d’un **DataSet** à l’aide de la **remplir** ou **FillSchema** méthodes de la  **DataAdapter** objet, ou à partir d’un prédéfini ou déduit XML schema à l’aide de la **ReadXml**, **ReadXmlSchema**, ou **InferXmlSchema** méthodes de la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="dac0f-106">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="dac0f-107">Notez que, après avoir ajouté un **DataTable** en tant que membre de la **Tables** collection d’un **DataSet**, vous ne pouvez l’ajouter à la collection de tables de toutes les autres **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="dac0f-107">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="dac0f-108">Lorsque vous créez un **DataTable**, il ne possède pas de schéma (autrement dit, une structure).</span><span class="sxs-lookup"><span data-stu-id="dac0f-108">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="dac0f-109">Pour définir le schéma de la table, vous devez créer et ajouter <xref:System.Data.DataColumn> des objets sur le **colonnes** collection de la table.</span><span class="sxs-lookup"><span data-stu-id="dac0f-109">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="dac0f-110">Vous pouvez également définir une colonne de clé primaire pour la table et créer et ajouter **contrainte** des objets sur le **contraintes** collection de la table.</span><span class="sxs-lookup"><span data-stu-id="dac0f-110">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="dac0f-111">Après avoir défini le schéma pour un **DataTable**, vous pouvez ajouter des lignes de données à la table en ajoutant **DataRow** des objets sur le **lignes** collection de la table.</span><span class="sxs-lookup"><span data-stu-id="dac0f-111">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="dac0f-112">Vous n’êtes pas obligé de fournir une valeur pour le <xref:System.Data.DataTable.TableName%2A> propriété lorsque vous créez un **DataTable**; vous pouvez spécifier la propriété à un autre moment, ou vous pouvez la laisser vide.</span><span class="sxs-lookup"><span data-stu-id="dac0f-112">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="dac0f-113">Toutefois, lorsque vous ajoutez une table sans un **TableName** valeur un **DataSet**, la table a un nom incrémentiel par défaut de la Table*N*, en commençant par « Table » pour Table0.</span><span class="sxs-lookup"><span data-stu-id="dac0f-113">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dac0f-114">Nous vous recommandons d’éviter le « Table*N*« convention d’affectation de noms lorsque vous fournissez un **TableName** valeur, car le nom fourni peut entrer en conflit avec un nom de table par défaut existant dans le **jeu de données** .</span><span class="sxs-lookup"><span data-stu-id="dac0f-114">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="dac0f-115">Si le nom fourni existe déjà, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="dac0f-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="dac0f-116">L’exemple suivant crée une instance d’un **DataTable** de l’objet et lui attribue le nom « Customers ».</span><span class="sxs-lookup"><span data-stu-id="dac0f-116">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="dac0f-117">L’exemple suivant crée une instance d’un **DataTable** en l’ajoutant à la **Tables** collection d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="dac0f-117">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="dac0f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dac0f-118">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [<span data-ttu-id="dac0f-119">DataTables</span><span class="sxs-lookup"><span data-stu-id="dac0f-119">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="dac0f-120">Remplissage d’un DataSet à partir d’un DataAdapter</span><span class="sxs-lookup"><span data-stu-id="dac0f-120">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="dac0f-121">Chargement d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="dac0f-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="dac0f-122">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="dac0f-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="dac0f-123">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="dac0f-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
