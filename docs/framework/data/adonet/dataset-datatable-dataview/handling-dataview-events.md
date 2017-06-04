---
title: "Gestion des &#233;v&#233;nements DataView | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Gestion des &#233;v&#233;nements DataView
Vous pouvez utiliser l'événement <xref:System.Data.DataView.ListChanged> du <xref:System.Data.DataView> pour déterminer si une vue a été mise à jour.  Les mises à jour qui déclenchent l'événement incluent l'ajout, la suppression ou la modification d'une ligne dans la table sous\-jacente, l'ajout ou la suppression d'une colonne dans le schéma de la table sous\-jacente et une modification d'une relation parente ou enfant.  L'événement **ListChanged** vous avertit aussi si la liste des lignes que vous affichez a changé de façon significative suite à l'application d'un nouvel ordre de tri ou d'un filtre.  
  
 L'événement **ListChanged** implémente le délégué **ListChangedEventHandler** de l'espace de noms <xref:System.ComponentModel> et accepte comme entrée un objet <xref:System.ComponentModel.ListChangedEventArgs>.  Vous pouvez déterminer le type de modification qui a été apportée à l'aide de la valeur d'énumération <xref:System.ComponentModel.ListChangedType> figurant dans la propriété **ListChangedType** de l'objet **ListChangedEventArgs**.  Pour les modifications qui impliquent l'ajout, la suppression ou le déplacement de lignes, le nouvel index de la ligne ajoutée ou déplacée et l'index précédent de la ligne supprimée sont accessibles via la propriété **NewIndex** de l'objet **ListChangedEventArgs**.  Dans le cas d'une ligne déplacée, l'index précédent de la ligne déplacée est accessible via la propriété **OldIndex** de l'objet **ListChangedEventArgs**.  
  
 Le **DataViewManager** expose également un événement **ListChanged** pour vous avertir lorsqu'une table a été ajoutée ou supprimée ou lorsqu'une modification a été apportée à la collection **Relations** du **DataSet** sous\-jacent.  
  
 L'exemple de code suivant montre comment ajouter un gestionnaire d'événements **ListChanged**.  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
  
```  
  
```csharp  
custView.ListChanged  += new   
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,   
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## Voir aussi  
 <xref:System.Data.DataView>   
 <xref:System.ComponentModel.ListChangedEventHandler>   
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)