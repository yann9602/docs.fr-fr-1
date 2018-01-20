---
title: "Gestion des événements de DataSet"
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
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 820d93529fc12f3eeacd730cc66ec85ffd560ff9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="handling-dataset-events"></a><span data-ttu-id="f4863-102">Gestion des événements de DataSet</span><span class="sxs-lookup"><span data-stu-id="f4863-102">Handling DataSet Events</span></span>
<span data-ttu-id="f4863-103">L'objet <xref:System.Data.DataSet> fournit trois événements : <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>et <xref:System.Data.DataSet.MergeFailed>.</span><span class="sxs-lookup"><span data-stu-id="f4863-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="f4863-104">Événement MergeFailed</span><span class="sxs-lookup"><span data-stu-id="f4863-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="f4863-105">L'événement le plus couramment utilisé de l'objet `DataSet` est `MergeFailed`, qui se déclenche en cas de conflit au niveau du schéma des objets `DataSet` en cours de fusion.</span><span class="sxs-lookup"><span data-stu-id="f4863-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="f4863-106">Cela se produit lorsque des <xref:System.Data.DataRow> cible et source possèdent la même valeur de clé primaire et que la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="f4863-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="f4863-107">Par exemple, si les colonnes de clé primaire d'une table en cours de fusion sont identiques entre les tables des deux objets `DataSet` , une exception est levée et l'événement `MergeFailed` est déclenché.</span><span class="sxs-lookup"><span data-stu-id="f4863-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="f4863-108">L'objet <xref:System.Data.MergeFailedEventArgs> passé à l'événement `MergeFailed` possède une propriété <xref:System.Data.MergeFailedEventArgs.Conflict%2A> qui identifie le conflit au niveau du schéma entre les deux objets `DataSet` et une propriété <xref:System.Data.MergeFailedEventArgs.Table%2A> qui identifie le nom de la table en conflit.</span><span class="sxs-lookup"><span data-stu-id="f4863-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="f4863-109">Le fragment de code ci-dessous montre comment ajouter un gestionnaire d'événements pour l'événement `MergeFailed`.</span><span class="sxs-lookup"><span data-stu-id="f4863-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a><span data-ttu-id="f4863-110">Événement Initialized</span><span class="sxs-lookup"><span data-stu-id="f4863-110">The Initialized Event</span></span>  
 <span data-ttu-id="f4863-111">L'événement <xref:System.Data.DataSet.Initialized> se produit après que le constructeur `DataSet` a initialisé une nouvelle instance du `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f4863-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="f4863-112">La propriété <xref:System.Data.DataSet.IsInitialized%2A> retourne `true` si le `DataSet` a terminé l'initialisation ; dans le cas contraire, elle retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="f4863-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="f4863-113">La méthode <xref:System.Data.DataSet.BeginInit%2A> , qui commence l'initialisation d'un `DataSet`, affecte à la propriété <xref:System.Data.DataSet.IsInitialized%2A> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="f4863-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="f4863-114">La méthode <xref:System.Data.DataSet.EndInit%2A> , qui termine l'initialisation du `DataSet`, lui affecte la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="f4863-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="f4863-115">Ces méthodes sont utilisées par l'environnement de conception [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] pour initialiser un `DataSet` utilisé par un autre composant.</span><span class="sxs-lookup"><span data-stu-id="f4863-115">These methods are used by the [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="f4863-116">Vous ne les utiliserez pas couramment dans votre code.</span><span class="sxs-lookup"><span data-stu-id="f4863-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="f4863-117">Événement Disposed</span><span class="sxs-lookup"><span data-stu-id="f4863-117">The Disposed Event</span></span>  
 <span data-ttu-id="f4863-118">`DataSet` est dérivé de la classe <xref:System.ComponentModel.MarshalByValueComponent> , qui expose la méthode <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> et l'événement <xref:System.ComponentModel.MarshalByValueComponent.Disposed> .</span><span class="sxs-lookup"><span data-stu-id="f4863-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="f4863-119">Le <xref:System.ComponentModel.MarshalByValueComponent.Disposed> événement ajoute un gestionnaire d’événements pour écouter l’événement libéré sur le composant.</span><span class="sxs-lookup"><span data-stu-id="f4863-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="f4863-120">Vous pouvez utiliser la <xref:System.ComponentModel.MarshalByValueComponent.Disposed> événement d’un `DataSet` si vous souhaitez exécuter code lorsque le <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="f4863-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="f4863-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>Libère les ressources utilisées par le <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="f4863-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4863-122">Le `DataSet` et `DataTable` objets héritent de <xref:System.ComponentModel.MarshalByValueComponent> et prend en charge la <xref:System.Runtime.Serialization.ISerializable> interface pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="f4863-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="f4863-123">Ce sont les seuls objets ADO.NET qui peuvent être exécutés à distance.</span><span class="sxs-lookup"><span data-stu-id="f4863-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="f4863-124">Pour plus d’informations, consultez [des objets distants](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span><span class="sxs-lookup"><span data-stu-id="f4863-124">For more information, see [Remote Objects](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span></span>  
  
 <span data-ttu-id="f4863-125">Pour plus d’informations sur les autres événements disponibles lorsque vous travaillez avec un `DataSet`, consultez [gestion des événements de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) et [gestion des événements DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="f4863-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) and [Handling DataAdapter Events](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4863-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4863-126">See Also</span></span>  
 [<span data-ttu-id="f4863-127">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="f4863-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="f4863-128">Validation des données</span><span class="sxs-lookup"><span data-stu-id="f4863-128">Validating Data</span></span>](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [<span data-ttu-id="f4863-129">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f4863-129">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="f4863-130">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="f4863-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
