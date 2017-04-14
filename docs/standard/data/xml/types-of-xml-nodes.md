---
title: "Types de nœuds XML | Microsoft Docs"
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
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Types de nœuds XML
Quand un document XML est lu et chargé en mémoire sous la forme d'une arborescence de nœuds, le type de nœud des nœuds est déterminé lors de la création de ces derniers.  Le DOM \(Document Object Model\) XML propose plusieurs catégories de types de nœuds, déterminés par le World Wide Web Consortium \(W3C\) et répertoriés dans la section 1.1.1 The DOM Structure Model.  Le tableau suivant répertorie les types de nœuds et fournit, pour chaque type, l'objet qui lui est assigné ainsi qu'une brève description.  
  
|Type de nœud DOM|Objet|Description|  
|----------------------|-----------|-----------------|  
|Document|[Classe XmlDocument](frlrfSystemXmlXmlDocumentClassTopic)|Conteneur de tous les nœuds de l'arborescence.  Également connu comme la racine du document, qui ne correspond pas toujours à l'élément racine.|  
|DocumentFragment|[Classe XmlDocumentFragment](frlrfSystemXmlXmlDocumentFragmentClassTopic)|Sac temporaire contenant un ou plusieurs nœuds sans structure d'arborescence.|  
|DocumentType ;|[Classe XmlDocumentType](frlrfSystemXmlXmlDocumentTypeClassTopic)|Représente le nœud `<!DOCTYPE…>`.|  
|EntityReference|[Classe XmlEntityReference](frlrfSystemXmlXmlEntityReferenceClassTopic)|Représente le texte de référence d'entité non développé.|  
|Élément|[Classe XmlElement](frlrfSystemXmlXmlElementClassTopic)|Représente un nœud d'élément.|  
|Attr|[Classe XmlAttribute](frlrfSystemXmlXmlAttributeClassTopic)|Attribut d'un élément.|  
|ProcessingInstruction ;|[Classe XmlProcessingInstruction](frlrfSystemXmlXmlProcessingInstructionClassTopic)|Nœud d'instruction de traitement.|  
|Commentaire|[Classe XmlComment](frlrfSystemXmlXmlCommentClassTopic)|Nœud de commentaire.|  
|Texte|[Classe XmlText](frlrfSystemXmlXmlTextClassTopic)|Texte appartenant à un élément ou attribut.|  
|CDATASection.|[Classe XmlCDataSection](frlrfSystemXmlXmlCDataSectionClassTopic)|Représente CDATA.|  
|Entité|[Classe XmlEntity](frlrfSystemXmlXmlEntityClassTopic)|Représente les déclarations `<!ENTITY…>` dans un document XML, soit à partir d'un sous\-ensemble de définitions de type de document \(DTD\) internes, soit à partir de DTD externes et d'entités de paramètre.|  
|Notation|[Classe XmlNotation](frlrfSystemXmlXmlNotationClassTopic)|Représente une notation déclarée dans la DTD.|  
  
 Bien que dans la spécification W3C DOM Level 1, et plus particulièrement dans la section 1.2, Fundamental Interfaces, un attribut \(*attr*\) soit répertorié en tant que nœud, il n'est pas considéré comme un enfant d'un nœud d'élément.  
  
 Le tableau suivant indique des types de nœuds supplémentaires non définis par le W3C, mais pouvant être utilisés dans le modèle objet Microsoft .NET Framework en tant qu'énumérations **XmlNodeType**.  Ce tableau ne comprend donc pas de colonne pour le type de nœud DOM correspondant à ces types de nœuds.  
  
|Type de nœud|Description|  
|------------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Représente le nœud de déclaration `<?xml version="1.0"…>`.|  
|<xref:System.Xml.XmlSignificantWhitespace>|Représente l'espace blanc significatif, qui est l'espace blanc dans du contenu mixte.|  
|<xref:System.Xml.XmlWhitespace>|Représente l'espace blanc dans le contenu d'un élément.|  
|EndElement|Est retourné lorsque **XmlReader** arrive à la fin d'un élément.<br /><br /> Exemple XML : **\<\/item\>**<br /><br /> Pour plus d'informations, voir [Énumération XmlNodeType](frlrfSystemXmlXmlNodeTypeClassTopic).|  
|EndEntity|Est retourné quand **XmlReader** arrive à la fin d'un remplacement d'entité à la suite d'un appel à <xref:System.Xml.XmlReader.ResolveEntity%2A>.  Pour plus d'informations, voir [Énumération XmlNodeType](frlrfSystemXmlXmlNodeTypeClassTopic).|  
  
 Pour afficher un exemple de code qui lit du code XML et utilise une construction Case sur les types de nœuds afin d'imprimer des informations sur le nœud et son contenu, voir [Propriété XmlSignificantWhitespace.NodeType](frlrfSystemXmlXmlSignificantWhitespaceClassNodeTypeTopic).  
  
 Pour plus d'informations sur la hiérarchie d'objets des types de nœuds et sur leurs noms d'objet équivalents, voir [Hiérarchie du DOM XML](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md).  Pour plus informations sur les objets créés dans l'arborescence de nœuds, voir [Mappage de la hiérarchie d'objets à des données XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
## Voir aussi  
 [DOM \(Document Object Model\) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)