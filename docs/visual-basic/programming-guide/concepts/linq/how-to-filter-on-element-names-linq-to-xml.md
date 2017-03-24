---
title: "Comment : filtrer sur des noms d’élément (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 07f7867b0fc5cf79ba5ce06f95b07b5c538e83d3
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a>Comment : filtrer sur des noms d’élément (LINQ to XML) (Visual Basic)
Lorsque vous appelez une des méthodes qui retournent des <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>, vous pouvez filtrer sur le nom de l’élément.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>  
  
## <a name="example"></a>Exemple  
 Cet exemple récupère une collection des descendants filtrée de sorte à contenir uniquement les descendants avec le nom spécifié.  
  
 Cet exemple utilise le document XML suivant : [exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Ce code génère la sortie suivante :  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Les autres méthodes qui retournent <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>collections suivent le même modèle.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Leurs signatures sont semblables aux <xref:System.Xml.Linq.XContainer.Elements%2A>et <xref:System.Xml.Linq.XContainer.Descendants%2A>.</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XContainer.Elements%2A> Voici la liste complète des méthodes qui ont des signatures de méthodes semblables :  
  
-   <xref:System.Xml.Linq.XNode.Ancestors%2A></xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Descendants%2A></xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A></xref:System.Xml.Linq.XContainer.Elements%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms. Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Cet exemple utilise le document XML suivant : [exemple de fichier XML : commande fournisseur typique dans un Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim items As IEnumerable(Of XElement) = _  
            From el In po...<aw:ProductName> _  
            Select el  
        For Each prdName As XElement In items  
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
        Next  
    End Sub  
End Module  
```  
  
 Ce code génère la sortie suivante :  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Axes LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
