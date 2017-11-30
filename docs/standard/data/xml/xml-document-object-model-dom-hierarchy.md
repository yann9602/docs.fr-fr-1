---
title: "Hiérarchie du DOM XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6dec61860fba5815b1dae802d280e8df6628ab91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hiérarchie du DOM XML
L’illustration suivante montre la hiérarchie de classes du DOM (Document Object Model) XML et fournit le nom World Wide Web Consortium (W3C) entre parenthèses en même temps que le nom de la classe lorsque cela est pertinent.  
  
 ![Modèle objet de Document XML &#40; DOM &#41; hiérarchie](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hiérarchie du modèle DOM (Document Object Model) XML  
  
 Les classes suivantes n’héritent pas de la **XmlNode**:  
  
-   **XmlImplementation**  
  
-   **XmlNamedNodeMap**  
  
-   **XmlNodeList**  
  
-   **XmlNodeChangedEventArgs**  
  
 Le **XmlImplementation** classe est utilisée pour créer un document XML. Pour plus d’informations, consultez [création d’un Document XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 Le **XmlNamedNodeMap** classe gère un ensemble non trié de nœuds. Pour plus d’informations, consultez [extraction de nœuds non triée par nom ou Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 Le **XmlNodeList** classe gère une liste triée de nœuds. Pour plus d’informations, consultez [extraction de nœuds triés par l’Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 Le **XmlNodeChangedEventArgs** classe gère des gestionnaires d’événements inscrits sur le **XmlDocument**. Pour plus d’informations, consultez [gestion des événements dans un Document XML à l’aide de XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 Le **XmlLinkedNode** hérite de la classe **XmlNode**. Son objectif consiste à substituer deux méthodes de **XmlNode**: le **PreviousSibling** et **NextSibling** méthodes. Les méthodes substituées sont ensuite héritées et utilisées par **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, et **XmlProcessingInstruction**, qui sont des classes dotées de frères précédents et suivants.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
