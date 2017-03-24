---
title: "Comment : récupérer un seul élément enfant (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9e96e2e2270f16364b0a26a0b4f17c0d96d7c38b
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a>Comment : récupérer un seul élément enfant (LINQ to XML) (Visual Basic)
Cette rubrique explique comment récupérer un seul élément enfant, étant donné le nom de l'élément enfant. Lorsque vous connaissez le nom de l’élément enfant et qu’il n’y a qu’un seul élément qui possède ce nom, il peut être plus commode de récupérer un seul élément plutôt qu’une collection.  
  
 La <xref:System.Xml.Linq.XContainer.Element%2A>méthode retourne le premier enfant <xref:System.Xml.Linq.XElement>avec le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer.Element%2A>  
  
 Si vous souhaitez récupérer un seul élément enfant en Visual Basic, une approche courante consiste à utiliser la propriété XML, puis à récupérer le premier élément à l'aide de la notation d'indexeur de tableau.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la <xref:System.Xml.Linq.XContainer.Element%2A>méthode.</xref:System.Xml.Linq.XContainer.Element%2A> Cet exemple prend l'arborescence XML nommée `po` et recherche le premier élément nommé `Comment`.  
  
 L'exemple Visual Basic illustre l'utilisation de la notation d'indexeur de tableau pour récupérer un seul élément.  
  
 Cet exemple utilise le document XML suivant : [exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre le même code pour du XML qui est dans un espace de noms. Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Cet exemple utilise le document XML suivant : [exemple de fichier XML : commande fournisseur typique dans un Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Axes LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
