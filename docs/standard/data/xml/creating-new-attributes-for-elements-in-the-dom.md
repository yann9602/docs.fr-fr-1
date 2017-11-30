---
title: "Création de nouveaux attributs pour des éléments du DOM"
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
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6970ffc38e900c9b47c58c8ae4b81b9551f5589b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="225bf-102">Création de nouveaux attributs pour des éléments du DOM</span><span class="sxs-lookup"><span data-stu-id="225bf-102">Creating New Attributes for Elements in the DOM</span></span>
<span data-ttu-id="225bf-103">Création de nouveaux attributs diffère de celui de la création d’autres types de nœud car les attributs ne sont pas des nœuds, mais sont des propriétés d’un nœud d’élément et sont contenues dans un **XmlAttributeCollection** associé à l’élément.</span><span class="sxs-lookup"><span data-stu-id="225bf-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="225bf-104">Il existe plusieurs manières de créer un attribut et de le joindre à un élément :</span><span class="sxs-lookup"><span data-stu-id="225bf-104">There are multiple ways to create an attribute and attach it to an element:</span></span>  
  
-   <span data-ttu-id="225bf-105">Obtenir le nœud d’élément et utiliser **SetAttribute** pour ajouter un attribut à la collection d’attributs de cet élément.</span><span class="sxs-lookup"><span data-stu-id="225bf-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>  
  
-   <span data-ttu-id="225bf-106">Créer un **XmlAttribute** nœud à l’aide du **CreateAttribute** (méthode), obtenir le nœud d’élément, puis utilisez **SetAttributeNode** pour ajouter le nœud à la collection d’attributs de ce élément.</span><span class="sxs-lookup"><span data-stu-id="225bf-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>  
  
 <span data-ttu-id="225bf-107">L’exemple suivant montre comment ajouter un attribut à un élément à l’aide de la **SetAttribute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="225bf-107">The following example shows how to add an attribute to an element using the **SetAttribute** method.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
public class Sample  
  
  public shared sub Main()  
  
  Dim doc as XmlDocument = new XmlDocument()  
  doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _  
              "<title>Pride And Prejudice</title>" & _  
              "</book>")  
  Dim root as XmlElement = doc.DocumentElement  
  
  'Add a new attribute.  
  root.SetAttribute("genre", "urn:samples", "novel")  
  
  Console.WriteLine("Display the modified XML...")  
  Console.WriteLine(doc.InnerXml)  
  
  end sub  
end class  
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
    doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +  
                "<title>Pride And Prejudice</title>" +  
                "</book>");  
    XmlElement root = doc.DocumentElement;  
  
    // Add a new attribute.  
    root.SetAttribute("genre", "urn:samples", "novel");  
  
    Console.WriteLine("Display the modified XML...");  
    Console.WriteLine(doc.InnerXml);  
  }  
```  
  
 <span data-ttu-id="225bf-108">L’exemple suivant montre un nouvel attribut à l’aide de la **CreateAttribute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="225bf-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="225bf-109">Il montre ensuite l’attribut ajouté à la collection d’attributs de la **book** à l’aide de l’élément le **SetAttributeNode** (méthode).</span><span class="sxs-lookup"><span data-stu-id="225bf-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>  
  
 <span data-ttu-id="225bf-110">En partant du code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="225bf-110">Given the following XML:</span></span>  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="225bf-111">créez un nouvel attribut et attribuez-lui une valeur :</span><span class="sxs-lookup"><span data-stu-id="225bf-111">create a new attribute and give it a value:</span></span>  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 <span data-ttu-id="225bf-112">Puis, joignez-le à l'élément :</span><span class="sxs-lookup"><span data-stu-id="225bf-112">and attach it to the element:</span></span>  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 <span data-ttu-id="225bf-113">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="225bf-113">**Output**</span></span>  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="225bf-114">L’exemple de code complet, consultez <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="225bf-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>  
  
 <span data-ttu-id="225bf-115">Vous pouvez également créer un **XmlAttribute** nœud et utilisez le **InsertBefore** ou **InsertAfter** pour le placer à la position appropriée dans la collection.</span><span class="sxs-lookup"><span data-stu-id="225bf-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="225bf-116">Si un attribut portant le même nom est déjà présent dans la collection d’attributs existants **XmlAttribute** nœud est supprimé de la collection et la nouvelle **XmlAttribute** nœud est inséré.</span><span class="sxs-lookup"><span data-stu-id="225bf-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="225bf-117">Il effectue la même façon que les **SetAttribute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="225bf-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="225bf-118">Ces méthodes prennent comme paramètre un nœud existant comme point de référence pour effectuer la **InsertBefore** et **InsertAfter**.</span><span class="sxs-lookup"><span data-stu-id="225bf-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="225bf-119">Si vous ne fournissez pas un nœud de référence indiquant la position d’insertion du nouveau nœud, la valeur par défaut pour le **InsertAfter** méthode consiste à insérer le nouveau nœud au début de la collection.</span><span class="sxs-lookup"><span data-stu-id="225bf-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="225bf-120">La position par défaut pour le **InsertBefore**, si aucun nœud de référence n’est fourni, est à la fin de la collection.</span><span class="sxs-lookup"><span data-stu-id="225bf-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>  
  
 <span data-ttu-id="225bf-121">Si vous avez créé un **XmlNamedNodeMap** d’attributs, vous pouvez ajouter un attribut par nom à l’aide du <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="225bf-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span></span> <span data-ttu-id="225bf-122">Pour plus d’informations, consultez [Collections de nœuds dans NamedNodeMap et NodeList](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span><span class="sxs-lookup"><span data-stu-id="225bf-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span></span>  
  
## <a name="default-attributes"></a><span data-ttu-id="225bf-123">Attributs par défaut</span><span class="sxs-lookup"><span data-stu-id="225bf-123">Default Attributes</span></span>  
 <span data-ttu-id="225bf-124">Si vous créez un élément déclaré comme possédant un attribut par défaut, un nouvel attribut par défaut avec sa valeur par défaut est créé par le DOM (Document Object Model) XML et joint à cet élément.</span><span class="sxs-lookup"><span data-stu-id="225bf-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="225bf-125">Les nœuds enfants de l'attribut par défaut sont également créés en même temps.</span><span class="sxs-lookup"><span data-stu-id="225bf-125">The child nodes of the default attribute are also created at this time.</span></span>  
  
## <a name="attribute-child-nodes"></a><span data-ttu-id="225bf-126">Nœuds enfants d'attribut</span><span class="sxs-lookup"><span data-stu-id="225bf-126">Attribute Child Nodes</span></span>  
 <span data-ttu-id="225bf-127">La valeur d'un nœud d'attribut devient ses nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="225bf-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="225bf-128">Il existe seulement deux types de nœuds enfants valides : **XmlText** nœuds, et **XmlEntityReference** nœuds.</span><span class="sxs-lookup"><span data-stu-id="225bf-128">There are only two types of valid child nodes: **XmlText** nodes, and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="225bf-129">Ce sont des nœuds enfants en ce sens que les méthodes telles que **FirstChild** et **LastChild** les traiter comme des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="225bf-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="225bf-130">Cette distinction qui caractérise un attribut possédant des nœuds enfants est importante lorsque vous tentez de supprimer des attributs ou des nœuds enfants d'attribut.</span><span class="sxs-lookup"><span data-stu-id="225bf-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="225bf-131">Pour plus d’informations, consultez [suppression d’attributs d’un nœud d’élément dans le DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="225bf-131">For more information, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="225bf-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="225bf-132">See Also</span></span>  
 [<span data-ttu-id="225bf-133">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="225bf-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
