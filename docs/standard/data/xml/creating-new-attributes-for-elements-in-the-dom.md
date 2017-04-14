---
title: "Cr&#233;ation de nouveaux attributs pour des &#233;l&#233;ments du DOM | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Cr&#233;ation de nouveaux attributs pour des &#233;l&#233;ments du DOM
La création de nouveaux attributs diffère de la création d'autres types de nœud car les attributs ne sont pas des nœuds, mais des propriétés d'un nœud d'élément, et appartiennent à un **XmlAttributeCollection** associé à cet élément.  Il existe plusieurs manières de créer un attribut et de le joindre à un élément :  
  
-   Obtenir le nœud d'élément et utiliser **SetAttribute** pour ajouter un attribut à la collection d'attributs de cet élément ;  
  
-   Créer un nœud **XmlAttribute** à l'aide de la méthode **CreateAttribute**, obtenir le nœud d'élément, puis utiliser **SetAttributeNode** pour ajouter le nœud à la collection d'attributs de cet élément.  
  
 L'exemple suivant montre comment ajouter un attribut à un élément au moyen de la méthode **SetAttribute**.  
  
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
  
 L'exemple suivant illustre la création d'un nouvel attribut à l'aide de la méthode **CreateAttribute**.  Il affiche ensuite l'attribut ajouté à la collection d'attributs de l'élément **book** à l'aide de la méthode **SetAttributeNode**.  
  
 En partant du code XML suivant :  
  
```  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 créez un nouvel attribut et attribuez\-lui une valeur :  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 Puis, joignez\-le à l'élément :  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 **Sortie**  
  
```  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Pour examiner l'exemple de code dans son intégralité, voir [Méthode XmlDocument.CreateAttribute](frlrfSystemXmlXmlDocumentClassCreateAttributeTopic).  
  
 Vous pouvez également créer un nœud **XmlAttribute** et utiliser la méthode **InsertBefore** ou **InsertAfter** pour le placer à la position voulue dans la collection.  Si un attribut de même nom figure déjà dans la collection d'attributs, le nœud **XmlAttribute** existant est supprimé de la collection et le nouveau nœud **XmlAttribute** est inséré.  Ce comportement est le même qu'avec la méthode **SetAttribute**.  Ces méthodes prennent comme paramètre un nœud existant comme point de référence pour réaliser les opérations **InsertBefore** et **InsertAfter**.  Si vous ne fournissez pas de nœud de référence indiquant la position d'insertion du nouveau nœud, la méthode **InsertAfter**, par défaut, place ce dernier au début de la collection.  Pour la méthode **InsertBefore**, la position par défaut si aucun nœud de référence n'est fourni est la fin de la collection.  
  
 Si vous avez créé un **XmlNamedNodeMap** d'attributs, vous pouvez ajouter un attribut en vous servant de son nom à l'aide de la [méthode SetNamedItem](frlrfSystemXmlXmlNamedNodeMapClassSetNamedItemTopic).  Pour plus d'informations, voir [Collections de nœuds dans NamedNodeMap et NodeList](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).  
  
## Attributs par défaut  
 Si vous créez un élément déclaré comme possédant un attribut par défaut, un nouvel attribut par défaut avec sa valeur par défaut est créé par le DOM \(Document Object Model\) XML et joint à cet élément.  Les nœuds enfants de l'attribut par défaut sont également créés en même temps.  
  
## Nœuds enfants d'attribut  
 La valeur d'un nœud d'attribut devient ses nœuds enfants.  Il n'y a que deux types de nœuds enfants valides : les nœuds **XmlText** et les nœuds **XmlEntityReference**.  Ces nœuds sont des nœuds enfants, en ce sens que des méthodes telles que **FirstChild** et **LastChild** les traitent comme tels.  Cette distinction qui caractérise un attribut possédant des nœuds enfants est importante lorsque vous tentez de supprimer des attributs ou des nœuds enfants d'attribut.  Pour plus d'informations, voir [Suppression d'attributs d'un nœud d'élément dans le DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## Voir aussi  
 [DOM \(Document Object Model\) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)