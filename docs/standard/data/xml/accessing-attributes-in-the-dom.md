---
title: "Accès aux attributs dans le DOM"
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
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a433ec5f83a50aa4fe4b2017a0dac3d2a5e5710c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-attributes-in-the-dom"></a>Accès aux attributs dans le DOM
Les attributs sont des propriétés de l'élément, pas des enfants de l'élément. Cette distinction est importante en raison des méthodes utilisées pour accéder aux nœuds frères, parents et enfants du DOM (Document Object Model) XML. Par exemple, le **PreviousSibling** et **NextSibling** méthodes ne sont pas utilisées pour naviguer d’un élément à un attribut ou entre des attributs. Au lieu de cela, un attribut est une propriété d’un élément et appartient à un élément, a une **OwnerElement** propriété et non une **parentNode** propriété, et possède des méthodes distinctes de navigation.  
  
 Lorsque le nœud actuel est un élément, utilisez la **HasAttribute** méthode pour voir s’il existe des attributs associés à l’élément. Une fois que vous savez qu'un élément possède des attributs, il existe plusieurs méthodes permettant d'accéder à des attributs. Pour extraire un seul attribut de l’élément, vous pouvez utiliser la **GetAttribute** et **GetAttributeNode** méthodes de la **XmlElement** ou vous pouvez obtenir tous les attributs dans la collection. L’obtention de la collection est utile s’il est nécessaire d’itérer sur la collection. Si vous souhaitez que tous les attributs de l’élément, utilisez la **attributs** propriété de l’élément à extraire tous les attributs d’une collection.  
  
## <a name="retrieving-all-attributes-into-a-collection"></a>Extraction de tous les attributs d’une collection  
 Si vous souhaitez que tous les attributs d’un nœud d’élément insérés dans une collection, appelez le **XmlElement.Attributes** propriété. Cet exemple obtient le **XmlAttributeCollection** qui contient tous les attributs d’un élément. Le **XmlAttributeCollection** classe hérite de la **XmlNamedNode** carte. Par conséquent, les méthodes et propriétés disponibles sur la collection comprennent celles qui sont disponibles sur une table de nœud nommée en outre méthodes et propriétés spécifiques à la **XmlAttributeCollection** class, telle que la **ItemOf**  propriété ou le **Append** (méthode). Chaque élément de la collection d’attributs représente un **XmlAttribute** nœud. Pour rechercher le nombre d’attributs sur un élément, obtenez le **XmlAttributeCollection**et utiliser le **nombre** propriété pour voir combien **XmlAttribute** nœuds se trouvent dans la collection.  
  
 L’exemple de code suivant montre comment récupérer un attribut de collection et, à l’aide de la **nombre** méthode pour l’index de boucle, comment itérer sur cette. Le code montre ensuite comment extraire un attribut unique de la collection et afficher sa valeur.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.   
        Dim myElement As XmlElement = doc.DocumentElement  
  
        ' Create an attribute collection from the element.  
        Dim attrColl As XmlAttributeCollection = myElement.Attributes  
  
        ' Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...")  
        Dim i As Integer  
        For i = 0 To attrColl.Count - 1  
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)  
            Console.Write("{0}", attrColl.ItemOf(i).Value)  
            Console.WriteLine()  
        Next  
  
        ' Retrieve a single attribute from the collection; specifically, the  
        ' attribute with the name "misc".  
        Dim attr As XmlAttribute = attrColl("misc")  
  
        ' Retrieve the value from that attribute.  
        Dim miscValue As String = attr.InnerXml  
  
        Console.WriteLine("Display the attribute information.")  
        Console.WriteLine(miscValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  
    public static void Main()  
    {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +  
                      "<title>The Handmaid's Tale</title>" +  
                      "<price>14.95</price>" +  
                      "</book>");  
  
        // Move to an element.  
        XmlElement myElement = doc.DocumentElement;  
  
        // Create an attribute collection from the element.  
        XmlAttributeCollection attrColl = myElement.Attributes;  
  
        // Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...");  
        for (int i = 0; i < attrColl.Count; i++)  
        {  
            Console.Write("{0} = ", attrColl[i].Name);  
            Console.Write("{0}", attrColl[i].Value);  
            Console.WriteLine();  
        }  
  
        // Retrieve a single attribute from the collection; specifically, the  
        // attribute with the name "misc".  
        XmlAttribute attr = attrColl["misc"];  
  
        // Retrieve the value from that attribute.  
        String miscValue = attr.InnerXml;  
  
        Console.WriteLine("Display the attribute information.");  
        Console.WriteLine(miscValue);  
  
    }  
}  
```  
  
 Cet exemple affiche la sortie suivante :  
  
 **Sortie**  
  
 Afficher tous les attributs dans la collection.  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 Les informations d'une collection d'attributs peuvent être extraites par leur nom ou numéro d'index. L'exemple ci-avant montre comment extraire des données par nom. L'exemple suivant montre comment extraire des données par numéro d'index.  
  
 Étant donné que la **XmlAttributeCollection** est une collection et peut être l’objet d’une itération par nom ou index, cet exemple montre le premier attribut dans la collection à l’aide d’un index de base zéro et le fichier suivant, **baseuri.xml**comme entrée.  
  
### <a name="input"></a>Entrée  
  
```xml  
<!-- XML fragment -->  
<book genre="novel">  
  <title>Pride And Prejudice</title>  
</book>  
```  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.Load("http://localhost/baseuri.xml")  
  
        ' Display information on the attribute node. The value  
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.  
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)  
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)  
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)  
        Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText)  
    End Sub 'Main   
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    // Create the XmlDocument.  
    XmlDocument doc = new XmlDocument();  
  
    doc.Load("http://localhost/baseuri.xml");  
  
    // Display information on the attribute node. The value  
    // returned for BaseURI is 'http://localhost/baseuri.xml'.  
    XmlAttribute attr = doc.DocumentElement.Attributes[0];  
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);  
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);  
    Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText);  
  }  
}  
```  
  
## <a name="retrieving-an-individual-attribute-node"></a>Extraction d'un nœud d'attribut individuel  
 Pour extraire un seul nœud d'attribut d'un élément, la méthode <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> est utilisée. Elle retourne un objet de type **XmlAttribute**. Une fois que vous avez un **XmlAttribute**, toutes les méthodes et propriétés disponibles dans le <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> classe sont disponibles sur cet objet, comme la recherche le **OwnerElement**.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.  
        Dim root As XmlElement  
        root = doc.DocumentElement  
  
        ' Get an attribute.  
        Dim attr As XmlAttribute  
        attr = root.GetAttributeNode("ISBN")  
  
        ' Display the value of the attribute.  
        Dim attrValue As String  
        attrValue = attr.InnerXml  
        Console.WriteLine(attrValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
 public class Sample  
 {  
      public static void Main()  
      {  
    XmlDocument doc = new XmlDocument();  
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +  
                   "<title>The Handmaid's Tale</title>" +  
                   "<price>14.95</price>" +  
                   "</book>");   
  
    // Move to an element.  
     XmlElement root = doc.DocumentElement;  
  
    // Get an attribute.  
     XmlAttribute attr = root.GetAttributeNode("ISBN");  
  
    // Display the value of the attribute.  
     String attrValue = attr.InnerXml;  
     Console.WriteLine(attrValue);  
  
    }  
}  
```  
  
 Vous pouvez également suivre l’exemple précédent, où un nœud d’attribut unique est extrait de la collection d’attributs. L’exemple de code suivant montre comment une ligne de code peut être écrites pour extraire un attribut unique par numéro d’index depuis la racine du document XML arborescence, également connue sous le **DocumentElement** propriété.  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
