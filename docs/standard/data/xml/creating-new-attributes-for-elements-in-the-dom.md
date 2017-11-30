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
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>Création de nouveaux attributs pour des éléments du DOM
Création de nouveaux attributs diffère de celui de la création d’autres types de nœud car les attributs ne sont pas des nœuds, mais sont des propriétés d’un nœud d’élément et sont contenues dans un **XmlAttributeCollection** associé à l’élément. Il existe plusieurs manières de créer un attribut et de le joindre à un élément :  
  
-   Obtenir le nœud d’élément et utiliser **SetAttribute** pour ajouter un attribut à la collection d’attributs de cet élément.  
  
-   Créer un **XmlAttribute** nœud à l’aide du **CreateAttribute** (méthode), obtenir le nœud d’élément, puis utilisez **SetAttributeNode** pour ajouter le nœud à la collection d’attributs de ce élément.  
  
 L’exemple suivant montre comment ajouter un attribut à un élément à l’aide de la **SetAttribute** (méthode).  
  
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
  
 L’exemple suivant montre un nouvel attribut à l’aide de la **CreateAttribute** (méthode). Il montre ensuite l’attribut ajouté à la collection d’attributs de la **book** à l’aide de l’élément le **SetAttributeNode** (méthode).  
  
 En partant du code XML suivant :  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 créez un nouvel attribut et attribuez-lui une valeur :  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 Puis, joignez-le à l'élément :  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 **Sortie**  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 L’exemple de code complet, consultez <xref:System.Xml.XmlDocument.CreateAttribute%2A>.  
  
 Vous pouvez également créer un **XmlAttribute** nœud et utilisez le **InsertBefore** ou **InsertAfter** pour le placer à la position appropriée dans la collection. Si un attribut portant le même nom est déjà présent dans la collection d’attributs existants **XmlAttribute** nœud est supprimé de la collection et la nouvelle **XmlAttribute** nœud est inséré. Il effectue la même façon que les **SetAttribute** (méthode). Ces méthodes prennent comme paramètre un nœud existant comme point de référence pour effectuer la **InsertBefore** et **InsertAfter**. Si vous ne fournissez pas un nœud de référence indiquant la position d’insertion du nouveau nœud, la valeur par défaut pour le **InsertAfter** méthode consiste à insérer le nouveau nœud au début de la collection. La position par défaut pour le **InsertBefore**, si aucun nœud de référence n’est fourni, est à la fin de la collection.  
  
 Si vous avez créé un **XmlNamedNodeMap** d’attributs, vous pouvez ajouter un attribut par nom à l’aide du <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>. Pour plus d’informations, consultez [Collections de nœuds dans NamedNodeMap et NodeList](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).  
  
## <a name="default-attributes"></a>Attributs par défaut  
 Si vous créez un élément déclaré comme possédant un attribut par défaut, un nouvel attribut par défaut avec sa valeur par défaut est créé par le DOM (Document Object Model) XML et joint à cet élément. Les nœuds enfants de l'attribut par défaut sont également créés en même temps.  
  
## <a name="attribute-child-nodes"></a>Nœuds enfants d'attribut  
 La valeur d'un nœud d'attribut devient ses nœuds enfants. Il existe seulement deux types de nœuds enfants valides : **XmlText** nœuds, et **XmlEntityReference** nœuds. Ce sont des nœuds enfants en ce sens que les méthodes telles que **FirstChild** et **LastChild** les traiter comme des nœuds enfants. Cette distinction qui caractérise un attribut possédant des nœuds enfants est importante lorsque vous tentez de supprimer des attributs ou des nœuds enfants d'attribut. Pour plus d’informations, consultez [suppression d’attributs d’un nœud d’élément dans le DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
