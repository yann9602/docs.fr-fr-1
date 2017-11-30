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
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="33487-102">Accès aux attributs dans le DOM</span><span class="sxs-lookup"><span data-stu-id="33487-102">Accessing Attributes in the DOM</span></span>
<span data-ttu-id="33487-103">Les attributs sont des propriétés de l'élément, pas des enfants de l'élément.</span><span class="sxs-lookup"><span data-stu-id="33487-103">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="33487-104">Cette distinction est importante en raison des méthodes utilisées pour accéder aux nœuds frères, parents et enfants du DOM (Document Object Model) XML.</span><span class="sxs-lookup"><span data-stu-id="33487-104">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="33487-105">Par exemple, le **PreviousSibling** et **NextSibling** méthodes ne sont pas utilisées pour naviguer d’un élément à un attribut ou entre des attributs.</span><span class="sxs-lookup"><span data-stu-id="33487-105">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="33487-106">Au lieu de cela, un attribut est une propriété d’un élément et appartient à un élément, a une **OwnerElement** propriété et non une **parentNode** propriété, et possède des méthodes distinctes de navigation.</span><span class="sxs-lookup"><span data-stu-id="33487-106">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>  
  
 <span data-ttu-id="33487-107">Lorsque le nœud actuel est un élément, utilisez la **HasAttribute** méthode pour voir s’il existe des attributs associés à l’élément.</span><span class="sxs-lookup"><span data-stu-id="33487-107">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="33487-108">Une fois que vous savez qu'un élément possède des attributs, il existe plusieurs méthodes permettant d'accéder à des attributs.</span><span class="sxs-lookup"><span data-stu-id="33487-108">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="33487-109">Pour extraire un seul attribut de l’élément, vous pouvez utiliser la **GetAttribute** et **GetAttributeNode** méthodes de la **XmlElement** ou vous pouvez obtenir tous les attributs dans la collection.</span><span class="sxs-lookup"><span data-stu-id="33487-109">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="33487-110">L’obtention de la collection est utile s’il est nécessaire d’itérer sur la collection.</span><span class="sxs-lookup"><span data-stu-id="33487-110">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="33487-111">Si vous souhaitez que tous les attributs de l’élément, utilisez la **attributs** propriété de l’élément à extraire tous les attributs d’une collection.</span><span class="sxs-lookup"><span data-stu-id="33487-111">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>  
  
## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="33487-112">Extraction de tous les attributs d’une collection</span><span class="sxs-lookup"><span data-stu-id="33487-112">Retrieving All Attributes into a Collection</span></span>  
 <span data-ttu-id="33487-113">Si vous souhaitez que tous les attributs d’un nœud d’élément insérés dans une collection, appelez le **XmlElement.Attributes** propriété.</span><span class="sxs-lookup"><span data-stu-id="33487-113">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="33487-114">Cet exemple obtient le **XmlAttributeCollection** qui contient tous les attributs d’un élément.</span><span class="sxs-lookup"><span data-stu-id="33487-114">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="33487-115">Le **XmlAttributeCollection** classe hérite de la **XmlNamedNode** carte.</span><span class="sxs-lookup"><span data-stu-id="33487-115">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="33487-116">Par conséquent, les méthodes et propriétés disponibles sur la collection comprennent celles qui sont disponibles sur une table de nœud nommée en outre méthodes et propriétés spécifiques à la **XmlAttributeCollection** class, telle que la **ItemOf**  propriété ou le **Append** (méthode).</span><span class="sxs-lookup"><span data-stu-id="33487-116">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="33487-117">Chaque élément de la collection d’attributs représente un **XmlAttribute** nœud.</span><span class="sxs-lookup"><span data-stu-id="33487-117">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="33487-118">Pour rechercher le nombre d’attributs sur un élément, obtenez le **XmlAttributeCollection**et utiliser le **nombre** propriété pour voir combien **XmlAttribute** nœuds se trouvent dans la collection.</span><span class="sxs-lookup"><span data-stu-id="33487-118">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>  
  
 <span data-ttu-id="33487-119">L’exemple de code suivant montre comment récupérer un attribut de collection et, à l’aide de la **nombre** méthode pour l’index de boucle, comment itérer sur cette.</span><span class="sxs-lookup"><span data-stu-id="33487-119">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="33487-120">Le code montre ensuite comment extraire un attribut unique de la collection et afficher sa valeur.</span><span class="sxs-lookup"><span data-stu-id="33487-120">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>  
  
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
  
 <span data-ttu-id="33487-121">Cet exemple affiche la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="33487-121">This example displays the following output:</span></span>  
  
 <span data-ttu-id="33487-122">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="33487-122">**Output**</span></span>  
  
 <span data-ttu-id="33487-123">Afficher tous les attributs dans la collection.</span><span class="sxs-lookup"><span data-stu-id="33487-123">Display all the attributes in the collection.</span></span>  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 <span data-ttu-id="33487-124">Les informations d'une collection d'attributs peuvent être extraites par leur nom ou numéro d'index.</span><span class="sxs-lookup"><span data-stu-id="33487-124">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="33487-125">L'exemple ci-avant montre comment extraire des données par nom.</span><span class="sxs-lookup"><span data-stu-id="33487-125">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="33487-126">L'exemple suivant montre comment extraire des données par numéro d'index.</span><span class="sxs-lookup"><span data-stu-id="33487-126">The next example shows how to retrieve data by index number.</span></span>  
  
 <span data-ttu-id="33487-127">Étant donné que la **XmlAttributeCollection** est une collection et peut être l’objet d’une itération par nom ou index, cet exemple montre le premier attribut dans la collection à l’aide d’un index de base zéro et le fichier suivant, **baseuri.xml**comme entrée.</span><span class="sxs-lookup"><span data-stu-id="33487-127">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>  
  
### <a name="input"></a><span data-ttu-id="33487-128">Entrée</span><span class="sxs-lookup"><span data-stu-id="33487-128">Input</span></span>  
  
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
  
## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="33487-129">Extraction d'un nœud d'attribut individuel</span><span class="sxs-lookup"><span data-stu-id="33487-129">Retrieving an Individual Attribute Node</span></span>  
 <span data-ttu-id="33487-130">Pour extraire un seul nœud d'attribut d'un élément, la méthode <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> est utilisée.</span><span class="sxs-lookup"><span data-stu-id="33487-130">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="33487-131">Elle retourne un objet de type **XmlAttribute**.</span><span class="sxs-lookup"><span data-stu-id="33487-131">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="33487-132">Une fois que vous avez un **XmlAttribute**, toutes les méthodes et propriétés disponibles dans le <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> classe sont disponibles sur cet objet, comme la recherche le **OwnerElement**.</span><span class="sxs-lookup"><span data-stu-id="33487-132">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>  
  
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
  
 <span data-ttu-id="33487-133">Vous pouvez également suivre l’exemple précédent, où un nœud d’attribut unique est extrait de la collection d’attributs.</span><span class="sxs-lookup"><span data-stu-id="33487-133">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="33487-134">L’exemple de code suivant montre comment une ligne de code peut être écrites pour extraire un attribut unique par numéro d’index depuis la racine du document XML arborescence, également connue sous le **DocumentElement** propriété.</span><span class="sxs-lookup"><span data-stu-id="33487-134">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a><span data-ttu-id="33487-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33487-135">See Also</span></span>  
 [<span data-ttu-id="33487-136">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="33487-136">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
