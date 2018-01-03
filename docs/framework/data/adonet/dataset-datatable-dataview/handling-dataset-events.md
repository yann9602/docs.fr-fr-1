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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a11d80e0aee459b3bbc985f38f482d5b1db61c70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="handling-dataset-events"></a>Gestion des événements de DataSet
L'objet <xref:System.Data.DataSet> fournit trois événements : <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>et <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>Événement MergeFailed  
 L'événement le plus couramment utilisé de l'objet `DataSet` est `MergeFailed`, qui se déclenche en cas de conflit au niveau du schéma des objets `DataSet` en cours de fusion. Cela se produit lorsque des <xref:System.Data.DataRow> cible et source possèdent la même valeur de clé primaire et que la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> a la valeur `true`. Par exemple, si les colonnes de clé primaire d'une table en cours de fusion sont identiques entre les tables des deux objets `DataSet` , une exception est levée et l'événement `MergeFailed` est déclenché. L'objet <xref:System.Data.MergeFailedEventArgs> passé à l'événement `MergeFailed` possède une propriété <xref:System.Data.MergeFailedEventArgs.Conflict%2A> qui identifie le conflit au niveau du schéma entre les deux objets `DataSet` et une propriété <xref:System.Data.MergeFailedEventArgs.Table%2A> qui identifie le nom de la table en conflit.  
  
 Le fragment de code ci-dessous montre comment ajouter un gestionnaire d'événements pour l'événement `MergeFailed`.  
  
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
  
## <a name="the-initialized-event"></a>Événement Initialized  
 L'événement <xref:System.Data.DataSet.Initialized> se produit après que le constructeur `DataSet` a initialisé une nouvelle instance du `DataSet`.  
  
 La propriété <xref:System.Data.DataSet.IsInitialized%2A> retourne `true` si le `DataSet` a terminé l'initialisation ; dans le cas contraire, elle retourne `false`. La méthode <xref:System.Data.DataSet.BeginInit%2A> , qui commence l'initialisation d'un `DataSet`, affecte à la propriété <xref:System.Data.DataSet.IsInitialized%2A> la valeur `false`. La méthode <xref:System.Data.DataSet.EndInit%2A> , qui termine l'initialisation du `DataSet`, lui affecte la valeur `true`. Ces méthodes sont utilisées par l'environnement de conception [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] pour initialiser un `DataSet` utilisé par un autre composant. Vous ne les utiliserez pas couramment dans votre code.  
  
## <a name="the-disposed-event"></a>Événement Disposed  
 `DataSet` est dérivé de la classe <xref:System.ComponentModel.MarshalByValueComponent> , qui expose la méthode <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> et l'événement <xref:System.ComponentModel.MarshalByValueComponent.Disposed> . Le <xref:System.ComponentModel.MarshalByValueComponent.Disposed> événement ajoute un gestionnaire d’événements pour écouter l’événement libéré sur le composant. Vous pouvez utiliser la <xref:System.ComponentModel.MarshalByValueComponent.Disposed> événement d’un `DataSet` si vous souhaitez exécuter code lorsque le <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> méthode est appelée. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>Libère les ressources utilisées par le <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  Le `DataSet` et `DataTable` objets héritent de <xref:System.ComponentModel.MarshalByValueComponent> et prend en charge la <xref:System.Runtime.Serialization.ISerializable> interface pour la communication à distance. Ce sont les seuls objets ADO.NET qui peuvent être exécutés à distance. Pour plus d'informations, consultez [Remote Objects](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58).  
  
 Pour plus d’informations sur les autres événements disponibles lorsque vous travaillez avec un `DataSet`, consultez [gestion des événements de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) et [gestion des événements DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Voir aussi  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [Extraction et modification de données dans ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
