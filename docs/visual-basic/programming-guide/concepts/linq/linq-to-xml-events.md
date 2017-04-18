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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2b7756845f155c4683015d54b41f2ecc09b29333
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-events-visual-basic"></a>Événements LINQ to XML (Visual Basic)
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]les événements permettent d’être averti lorsqu’une arborescence XML est modifiée.  
  
 Vous pouvez ajouter des événements à une instance de n’importe quel <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject> Le Gestionnaire d’événements doit recevoir ensuite des événements pour la modification apportée à cet <xref:System.Xml.Linq.XObject>et tous ses descendants.</xref:System.Xml.Linq.XObject> Par exemple, vous pouvez ajouter un gestionnaire d'événements à la racine de l'arborescence et gérer toutes les modifications apportées à l'arborescence à partir de ce gestionnaire d'événements.  
  
 Pour obtenir des exemples de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XObject.Changing>et <xref:System.Xml.Linq.XObject.Changed>.</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing> les événements, consultez  
  
## <a name="types-and-events"></a>Types et événements  
 Vous utilisez les types suivants lorsque vous travaillez avec des événements :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange></xref:System.Xml.Linq.XObjectChange>|Spécifie le type d’événement lorsqu’un événement est déclenché pour un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs></xref:System.Xml.Linq.XObjectChangeEventArgs>|Fournit des données pour le <xref:System.Xml.Linq.XObject.Changing>et <xref:System.Xml.Linq.XObject.Changed>événements.</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing>|  
  
 Les événements suivants sont déclenchés lorsque vous modifiez une arborescence XML :  
  
|Événement|Description|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing></xref:System.Xml.Linq.XObject.Changing>|Se produit juste avant que cet <xref:System.Xml.Linq.XObject>ou un de ses descendants ne change.</xref:System.Xml.Linq.XObject>|  
|<xref:System.Xml.Linq.XObject.Changed></xref:System.Xml.Linq.XObject.Changed>|Se produit lorsqu’un <xref:System.Xml.Linq.XObject>a été modifié ou un des ses descendants a changé.</xref:System.Xml.Linq.XObject>|  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Les événements sont utiles lorsque vous souhaitez conserver certaines informations d'agrégation dans une arborescence XML. Par exemple, vous pourriez souhaiter conserver le montant total d'une facture qui est la somme des éléments de la facture. Cet exemple utilise des événements pour conserver le total de tous les éléments enfants sous l'élément complexe `Items`.  
  
### <a name="code"></a>Code  
  
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
  
### <a name="comments"></a>Commentaires  
 Ce code génère la sortie suivante :  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML (Visual Basic) de la programmation avancée](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
