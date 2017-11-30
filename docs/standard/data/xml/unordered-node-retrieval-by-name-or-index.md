---
title: "Extraction de nœuds non triés par leur nom ou par l'index"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8bea8f373dced08fd7a2a828255a593533df9d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="unordered-node-retrieval-by-name-or-index"></a>Extraction de nœuds non triés par leur nom ou par l'index
Le **XmlNamedNodeMap** est décrite dans la spécification du World Wide Web Consortium (W3C) en tant que NamedNodeMap et est requis pour gérer un ensemble non trié de nœuds avec la possibilité de référencer les nœuds par leur nom ou l’index. La seule façon de que vous avez accès à un **XmlNamedNodeMap** est quand une **XmlNamedNodeMap** est retournée via une méthode ou propriété. Il existe trois méthodes ou propriétés retournent un **XmlNamedNodeMap**:  
  
-   XmlElement.Attributes ;  
  
-   XmlDocumentType.Entities ;  
  
-   XmlDocumentType.Notations.  
  
 Par exemple, le **XmlDocumentType.Entities** propriété obtient la collection de **XmlEntity** nœuds déclarés dans la déclaration de type de document. Cette collection est retournée en tant qu’un **XmlNamedNodeMap**, et vous pouvez itérer dans la collection à l’aide de la **nombre** informations propriété et l’affichage de l’entité. Pour obtenir un exemple d’itération sur une **XmlNamedNodeMap**, consultez <xref:System.Xml.XmlDocumentType.Entities%2A>.  
  
 Le **XmlAttributeCollection** est dérivée de **XmlNamedNodeMap** et seuls les attributs sont modifiables, alors que les notations et entités sont en lecture seule. À l’aide de la **XmlNamedNodeMap** pour les attributs, vous pouvez obtenir des nœuds pour ces attributs en fonction de leurs noms XML. Il s’agit d’une méthode facile pour manipuler la collection d’attributs d’un nœud d’élément. Cela peut être opposer directement **XmlNodeList**, qui implémente également la **IEnumerable** interface, mais avec un accesseur d’index plutôt qu’une chaîne. Le **RemoveNamedItem** et **SetNamedItem** méthodes sont utilisées uniquement par rapport à un **XmlAttributeCollection**. Ajout ou suppression d’une collection d’attributs, que vous utilisiez le **AttributeCollection** ou **XmlNamedNodeMap** implémentation, modifie la collection d’attributs sur l’élément. L'exemple de code suivant montre comment déplacer un attribut et créer un nouvel attribut.  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );           
  
    }  
}  
```  
  
 Pour voir un exemple de code supplémentaire qui illustre un attribut en cours de suppression une **AttributeCollection**, consultez [méthode XmlNamedNodeMap.RemoveNamedItem](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem). Pour plus d’informations sur les méthodes et propriétés, consultez [membres XmlNamedNodeMap](AllMembers.T:System.Xml.XmlNamedNodeMap).  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
