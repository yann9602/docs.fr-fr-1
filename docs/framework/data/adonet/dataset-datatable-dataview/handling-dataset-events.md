---
title: "Gestion des &#233;v&#233;nements de DataSet  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Gestion des &#233;v&#233;nements de DataSet 
L'objet <xref:System.Data.DataSet> fournit trois événements : <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized> et <xref:System.Data.DataSet.MergeFailed>.  
  
## Événement MergeFailed  
 L'événement le plus couramment utilisé de l'objet `DataSet` est `MergeFailed`, qui se déclenche en cas de conflit au niveau du schéma des objets `DataSet` en cours de fusion. Cela se produit lorsque des <xref:System.Data.DataRow> cible et source possèdent la même valeur de clé primaire et que la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> a la valeur `true`. Par exemple, si les colonnes de clé primaire d'une table en cours de fusion sont identiques entre les tables des deux objets `DataSet`, une exception est levée et l'événement `MergeFailed` est déclenché. L'objet <xref:System.Data.MergeFailedEventArgs> passé à l'événement `MergeFailed` possède une propriété <xref:System.Data.MergeFailedEventArgs.Conflict%2A> qui identifie le conflit au niveau du schéma entre les deux objets `DataSet` et une propriété <xref:System.Data.MergeFailedEventArgs.Table%2A> qui identifie le nom de la table en conflit.  
  
 Le fragment de code ci\-dessous montre comment ajouter un gestionnaire d'événements pour l'événement `MergeFailed`.  
  
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
  
## Événement Initialized  
 L'événement <xref:System.Data.DataSet.Initialized> se produit après que le constructeur `DataSet` a initialisé une nouvelle instance du `DataSet`.  
  
 La propriété <xref:System.Data.DataSet.IsInitialized%2A> retourne `true` si le `DataSet` a terminé l'initialisation ; dans le cas contraire, elle retourne `false`. La méthode <xref:System.Data.DataSet.BeginInit%2A>, qui commence l'initialisation d'un `DataSet`, affecte à la propriété <xref:System.Data.DataSet.IsInitialized%2A> la valeur `false`. La méthode <xref:System.Data.DataSet.EndInit%2A>, qui termine l'initialisation du `DataSet`, lui affecte la valeur `true`. Ces méthodes sont utilisées par l'environnement de conception [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] pour initialiser un `DataSet` utilisé par un autre composant. Vous ne les utiliserez pas couramment dans votre code.  
  
## Événement Disposed  
 `DataSet` est dérivé de la classe <xref:System.ComponentModel.MarshalByValueComponent>, qui expose la méthode <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> et l'événement <xref:System.ComponentModel.MarshalByValueComponent.Disposed>. L’événement <xref:System.ComponentModel.MarshalByValueComponent.Disposed>ajoute un gestionnaire d’événements pour écouter l’événement libéré sur le composant. Vous pouvez utiliser l’événement <xref:System.ComponentModel.MarshalByValueComponent.Disposed>d’un `DataSet` si vous voulez exécuter du code quand la méthode <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>est appelée.<xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>libère les ressources utilisées par le <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  Les objets `DataSet` et `DataTable` héritent de <xref:System.ComponentModel.MarshalByValueComponent>et prennent en charge l’interface <xref:System.Runtime.Serialization.ISerializable> pour la communication à distance. Ce sont les seuls objets ADO.NET qui peuvent être exécutés à distance. Pour plus d'informations, consultez [Remote Objects](http://msdn.microsoft.com/fr-fr/515686e6-0a8d-42f7-8188-73abede57c58).  
  
 Pour plus d’informations sur les autres événements disponibles lors de l’utilisation d’un `DataSet`, consultez [Gestion des événements DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) et [Gestion des événements DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## Voir aussi  
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Extraction et modification de données dans ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)