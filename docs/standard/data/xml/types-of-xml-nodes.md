---
title: "Types de nœuds XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3914a2c5c06a2cc73f14bc473984094b474d537e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-xml-nodes"></a>Types de nœuds XML
Quand un document XML est lu et chargé en mémoire sous la forme d’une arborescence de nœuds, le type de nœud des nœuds est déterminé lors de la création de ces derniers. Le DOM (Document Object Model) XML propose plusieurs catégories de types de nœuds, déterminés par le World Wide Web Consortium (W3C) et répertoriés dans la section 1.1.1 The DOM Structure Model. Le tableau suivant répertorie les types de nœuds et fournit, pour chaque type, l'objet qui lui est assigné ainsi qu'une brève description.  
  
|Type de nœud DOM|Objet|Description|  
|-------------------|------------|-----------------|  
|Document|<xref:System.Xml.XmlDocument>|Conteneur de tous les nœuds de l’arborescence. Également connu comme la racine du document, qui ne correspond pas toujours à l'élément racine.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Sac temporaire contenant un ou plusieurs nœuds sans structure d’arborescence.|  
|DocumentType ;|<xref:System.Xml.XmlDocumentType>|Représente le nœud `<!DOCTYPE…>`.|  
|EntityReference|<xref:System.Xml.XmlEntityReference>|Représente le texte de référence d’entité non développé.|  
|Élément|<xref:System.Xml.XmlElement>|Représente un nœud d'élément.|  
|Attr|<xref:System.Xml.XmlAttribute>|Attribut d'un élément.|  
|ProcessingInstruction ;|<xref:System.Xml.XmlProcessingInstruction>|Nœud d'instruction de traitement.|  
|Commentaire|<xref:System.Xml.XmlComment>|Nœud de commentaire.|  
|Texte|<xref:System.Xml.XmlText>|Texte appartenant à un élément ou attribut.|  
|CDATASection.|<xref:System.Xml.XmlCDataSection>|Représente CDATA.|  
|Entité|<xref:System.Xml.XmlEntity>|Représente les déclarations `<!ENTITY…>` dans un document XML, soit à partir d'un sous-ensemble de définitions de type de document (DTD) internes, soit à partir de DTD externes et d'entités de paramètre.|  
|Notation|<xref:System.Xml.XmlNotation>|Représente une notation déclarée dans la DTD.|  
  
 Bien qu’un attribut (*attr*) est répertorié dans le W3C DOM Level 1 la section 1.2 Fundamental Interfaces en tant que nœud, il n'est pas considéré comme un enfant d’un nœud d’élément.  
  
 Le tableau suivant présente les types de nœuds supplémentaires non définis par le W3C, mais ils ne sont disponibles pour une utilisation dans le modèle objet Microsoft .NET Framework en tant que **XmlNodeType** énumérations. Ce tableau ne comprend donc pas de colonne pour le type de nœud DOM correspondant à ces types de nœuds.  
  
|Type de nœud|Description|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Représente le nœud de déclaration `<?xml version="1.0"…>`.|  
|<xref:System.Xml.XmlSignificantWhitespace>|Représente l'espace blanc significatif, qui est l'espace blanc dans du contenu mixte.|  
|<xref:System.Xml.XmlWhitespace>|Représente l'espace blanc dans le contenu d'un élément.|  
|EndElement|Retourné lorsque **XmlReader** arrive à la fin d’un élément.<br /><br /> Exemple de fichier XML :  **\</Item >**<br /><br /> Pour plus d'informations, consultez <xref:System.Xml.XmlNodeType>.|  
|EndEntity|Retourné lorsque **XmlReader** arrive à la fin du remplacement d’entité à la suite d’un appel à <xref:System.Xml.XmlReader.ResolveEntity%2A>. Pour plus d'informations, consultez <xref:System.Xml.XmlNodeType>.|  
  
 Pour afficher un exemple de code qui lit du XML et utilise une construction case sur les types de nœuds pour imprimer des informations sur le nœud et son contenu, consultez <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.  
  
 Pour plus d’informations sur la hiérarchie d’objets des types de nœud et leurs noms d’objet équivalents, consultez [hiérarchie du modèle DOM (Document objet Model) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md). Pour plus d’informations sur les objets créés dans l’arborescence de nœuds, consultez [mappage de la hiérarchie d’objets à des données XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
