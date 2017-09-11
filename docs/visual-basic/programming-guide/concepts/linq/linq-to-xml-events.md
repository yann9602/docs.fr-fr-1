---
title: "Événements LINQ to XML (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e2358808dfeafab1576a686563e6025f90e78954
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="4eb3d-102">Événements LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4eb3d-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="4eb3d-103">les événements permettent d’être averti lorsqu’une arborescence XML est modifiée.</span><span class="sxs-lookup"><span data-stu-id="4eb3d-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="4eb3d-104">Vous pouvez ajouter des événements à une instance de n’importe quel <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="4eb3d-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="4eb3d-105">Le Gestionnaire d’événements doit recevoir ensuite des événements pour la modification apportée à cet <xref:System.Xml.Linq.XObject>et tous ses descendants.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="4eb3d-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="4eb3d-106">Par exemple, vous pouvez ajouter un gestionnaire d'événements à la racine de l'arborescence et gérer toutes les modifications apportées à l'arborescence à partir de ce gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="4eb3d-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="4eb3d-107">Pour obtenir des exemples de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XObject.Changing>et <xref:System.Xml.Linq.XObject.Changed>.</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing> les événements, consultez</span><span class="sxs-lookup"><span data-stu-id="4eb3d-107">For examples of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="4eb3d-108">Types et événements</span><span class="sxs-lookup"><span data-stu-id="4eb3d-108">Types and Events</span></span>  
 <span data-ttu-id="4eb3d-109">Vous utilisez les types suivants lorsque vous travaillez avec des événements :</span><span class="sxs-lookup"><span data-stu-id="4eb3d-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="4eb3d-110">Type</span><span class="sxs-lookup"><span data-stu-id="4eb3d-110">Type</span></span>|<span data-ttu-id="4eb3d-111">Description</span><span class="sxs-lookup"><span data-stu-id="4eb3d-111">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="4eb3d-112"><xref:System.Xml.Linq.XObjectChange></xref:System.Xml.Linq.XObjectChange></span><span class="sxs-lookup"><span data-stu-id="4eb3d-112"><xref:System.Xml.Linq.XObjectChange></span></span>|<span data-ttu-id="4eb3d-113">Spécifie le type d’événement lorsqu’un événement est déclenché pour un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="4eb3d-113">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="4eb3d-114"><xref:System.Xml.Linq.XObjectChangeEventArgs></xref:System.Xml.Linq.XObjectChangeEventArgs></span><span class="sxs-lookup"><span data-stu-id="4eb3d-114"><xref:System.Xml.Linq.XObjectChangeEventArgs></span></span>|<span data-ttu-id="4eb3d-115">Fournit des données pour le <xref:System.Xml.Linq.XObject.Changing>et <xref:System.Xml.Linq.XObject.Changed>événements.</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing></span><span class="sxs-lookup"><span data-stu-id="4eb3d-115">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="4eb3d-116">Les événements suivants sont déclenchés lorsque vous modifiez une arborescence XML :</span><span class="sxs-lookup"><span data-stu-id="4eb3d-116">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="4eb3d-117">Événement</span><span class="sxs-lookup"><span data-stu-id="4eb3d-117">Event</span></span>|<span data-ttu-id="4eb3d-118">Description</span><span class="sxs-lookup"><span data-stu-id="4eb3d-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4eb3d-119"><xref:System.Xml.Linq.XObject.Changing></xref:System.Xml.Linq.XObject.Changing></span><span class="sxs-lookup"><span data-stu-id="4eb3d-119"><xref:System.Xml.Linq.XObject.Changing></span></span>|<span data-ttu-id="4eb3d-120">Se produit juste avant que cet <xref:System.Xml.Linq.XObject>ou un de ses descendants ne change.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="4eb3d-120">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<span data-ttu-id="4eb3d-121"><xref:System.Xml.Linq.XObject.Changed></xref:System.Xml.Linq.XObject.Changed></span><span class="sxs-lookup"><span data-stu-id="4eb3d-121"><xref:System.Xml.Linq.XObject.Changed></span></span>|<span data-ttu-id="4eb3d-122">Se produit lorsqu’un <xref:System.Xml.Linq.XObject>a été modifié ou un des ses descendants a changé.</xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="4eb3d-122">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4eb3d-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="4eb3d-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4eb3d-124">Description</span><span class="sxs-lookup"><span data-stu-id="4eb3d-124">Description</span></span>  
 <span data-ttu-id="4eb3d-125">Les événements sont utiles lorsque vous souhaitez conserver certaines informations d'agrégation dans une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="4eb3d-125">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="4eb3d-126">Par exemple, vous pourriez souhaiter conserver le montant total d'une facture qui est la somme des éléments de la facture.</span><span class="sxs-lookup"><span data-stu-id="4eb3d-126">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="4eb3d-127">Cet exemple utilise des événements pour conserver le total de tous les éléments enfants sous l'élément complexe `Items`.</span><span class="sxs-lookup"><span data-stu-id="4eb3d-127">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4eb3d-128">Code</span><span class="sxs-lookup"><span data-stu-id="4eb3d-128">Code</span></span>  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="4eb3d-129">Commentaires</span><span class="sxs-lookup"><span data-stu-id="4eb3d-129">Comments</span></span>  
 <span data-ttu-id="4eb3d-130">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4eb3d-130">This code produces the following output:</span></span>  
  
```  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4eb3d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4eb3d-131">See Also</span></span>  
 [<span data-ttu-id="4eb3d-132">LINQ to XML (Visual Basic) de la programmation avancée</span><span class="sxs-lookup"><span data-stu-id="4eb3d-132">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
