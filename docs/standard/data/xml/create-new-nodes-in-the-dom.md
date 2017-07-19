---
title: "Cr&#233;ation de nouveaux nœuds dans le DOM | Microsoft Docs"
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
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 4
---
# Cr&#233;ation de nouveaux nœuds dans le DOM
Le <xref:System.Xml.XmlDocument> possède une méthode create pour tous les types de nœuds. À l'invite, donnez un nom à la méthode, au contenu ou autres paramètres pour les nœuds dotés de contenu (par exemple, un nœud de texte) et le nœud est créé. Les méthodes suivantes sont celles qui nécessitent un nom ainsi que quelques autres paramètres pour créer un nœud correct.  
  
-   <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 La création des autres types de nœuds exige d’autres opérations : il ne suffit pas de fournir des données à des paramètres.  
  
 Pour plus d’informations sur les attributs, consultez [création de nouveaux attributs pour les éléments dans le DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md). Pour plus d’informations sur la validation de nom d’élément et d’attribut, consultez [(élément XML) et vérification de nom d’attribut lors de la création de nouveaux nœuds](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md). Pour la création de références d’entité, consultez [création de nouvelles références d’entité](../../../../docs/standard/data/xml/creating-new-entity-references.md). Pour plus d’informations sur l’incidence des espaces de noms sur le développement des références d’entité, consultez [effet Namespace sur le développement de références d’entité pour les nouveaux nœuds contenant des éléments et attributs](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).  
  
 Une fois de nouveaux nœuds créés, plusieurs méthodes sont disponibles pour insérer ces nœuds dans l’arborescence. Ce tableau répertorie ces méthodes et décrit la position qu'occupe le nouveau nœud dans le DOM (Document Object Model) XML.  
  
|Méthode|Position du nœud|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|Inséré avant le nœud de référence. Par exemple, pour insérer le nouveau nœud en position 5 :<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> Pour plus d’informations, consultez la <xref:System.Xml.XmlNode.InsertBefore%2A> méthode.|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|Inséré après le nœud de référence. Exemple :<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> Pour plus d’informations, consultez la <xref:System.Xml.XmlNode.InsertAfter%2A> méthode.|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|Ajoute le nœud à la fin de la liste des nœuds enfants du nœud donné. Si le nœud ajouté est un <xref:System.Xml.XmlDocumentFragment>, tout le contenu du fragment de document est déplacé dans la liste des enfants de ce nœud. Pour plus d’informations, consultez la <xref:System.Xml.XmlNode.AppendChild%2A> méthode.|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|Ajoute le nœud au début de la liste des nœuds enfants du nœud donné. Si le nœud ajouté est un <xref:System.Xml.XmlDocumentFragment>, tout le contenu du fragment de document est déplacé dans la liste des enfants de ce nœud. Pour plus d’informations, consultez la <xref:System.Xml.XmlNode.PrependChild%2A> (méthode).|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|Ajoute un <xref:System.Xml.XmlAttribute> nœud à la fin de la collection d’attributs associée à un élément. Pour plus d’informations, consultez la <xref:System.Xml.XmlAttributeCollection.Append%2A> méthode.|  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)