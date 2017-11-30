---
title: "Gestion des événements de DataView"
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
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2abade8bbbf5ab8a9d2cf146271e89703ec34cb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="handling-dataview-events"></a><span data-ttu-id="e0d30-102">Gestion des événements de DataView</span><span class="sxs-lookup"><span data-stu-id="e0d30-102">Handling DataView Events</span></span>
<span data-ttu-id="e0d30-103">Vous pouvez utiliser l'événement <xref:System.Data.DataView.ListChanged> du <xref:System.Data.DataView> pour déterminer si une vue a été mise à jour.</span><span class="sxs-lookup"><span data-stu-id="e0d30-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="e0d30-104">Les mises à jour qui déclenchent l'événement incluent l'ajout, la suppression ou la modification d'une ligne dans la table sous-jacente, l'ajout ou la suppression d'une colonne dans le schéma de la table sous-jacente et une modification d'une relation parente ou enfant.</span><span class="sxs-lookup"><span data-stu-id="e0d30-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="e0d30-105">Le **ListChanged** événement vous avertit aussi si la liste des lignes que vous affichez a changé de manière significative en raison de l’application d’un nouvel ordre de tri ou un filtre.</span><span class="sxs-lookup"><span data-stu-id="e0d30-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="e0d30-106">Le **ListChanged** événement implémente la **ListChangedEventHandler** délégué de la <xref:System.ComponentModel> espace de noms et accepte comme entrée un <xref:System.ComponentModel.ListChangedEventArgs> objet.</span><span class="sxs-lookup"><span data-stu-id="e0d30-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="e0d30-107">Vous pouvez déterminer quel type de modification s’est produite à l’aide de la <xref:System.ComponentModel.ListChangedType> valeur d’énumération dans le **ListChangedType** propriété de la **ListChangedEventArgs** objet.</span><span class="sxs-lookup"><span data-stu-id="e0d30-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="e0d30-108">Pour les modifications qui impliquent l’ajout, suppression ou déplacement de lignes, le nouvel index de la ligne ajoutée ou déplacée et l’index précédent de la ligne supprimée sont accessibles à l’aide de la **NewIndex** propriété de la **ListChangedEventArgs** objet.</span><span class="sxs-lookup"><span data-stu-id="e0d30-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="e0d30-109">Dans le cas d’une ligne déplacée, l’index précédent de la ligne déplacée est accessible à l’aide de la **OldIndex** propriété de la **ListChangedEventArgs** objet.</span><span class="sxs-lookup"><span data-stu-id="e0d30-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="e0d30-110">Le **DataViewManager** expose également un **ListChanged** événements pour vous avertir lorsqu’une table a été ajoutée ou supprimée, ou si une modification a été apportée à la **Relations** collection de la sous-jacent **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="e0d30-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="e0d30-111">L’exemple de code suivant montre comment ajouter un **ListChanged** Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="e0d30-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0d30-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0d30-112">See Also</span></span>  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [<span data-ttu-id="e0d30-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="e0d30-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="e0d30-114">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="e0d30-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
