---
title: "Hi&#233;rarchie du DOM XML | Microsoft Docs"
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
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Hi&#233;rarchie du DOM XML
L'illustration suivante montre la hiérarchie de classes du DOM \(Document Object Model\) XML et fournit le nom World Wide Web Consortium \(W3C\) entre parenthèses en même temps que le nom de la classe lorsque cela est pertinent.  
  
 ![Hiérarchie du modèle DOM &#40;Document Object Model&#41; XML](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom\_class\_hierarchy")  
Hiérarchie du modèle DOM \(Document Object Model\) XML  
  
 Les classes suivantes n'héritent pas de **XmlNode** :  
  
-   **XmlImplementation ;**  
  
-   **XmlNamedNodeMap ;**  
  
-   **XmlNodeList ;**  
  
-   **XmlNodeChangedEventArgs.**  
  
 La classe **XmlImplementation** est utilisée pour créer un document XML.  Pour plus d'informations, voir [Création d'un document XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 La classe **XmlNamedNodeMap** gère une collection de nœuds non triée.  Pour plus d'informations, voir [Extraction de nœuds non triés par leur nom ou par l'index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 La classe **XmlNodeList** gère une liste triée de nœuds.  Pour plus d'informations, voir [Extraction de nœuds triés par l'index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 La classe **XmlNodeChangedEventArgs** gère des gestionnaires d'événements inscrits dans **XmlDocument**.  Pour plus d'informations, voir [Gestion d'événements dans un document XML à l'aide de XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 La classe **XmlLinkedNode** hérite de **XmlNode**.  Sa fonction consiste à substituer deux méthodes de **XmlNode** : les méthodes **PreviousSibling** et **NextSibling**.  Les méthodes substituées sont ensuite héritées et utilisées par **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference** et **XmlProcessingInstruction**, qui sont des classes dotées de frères précédents et suivants.  
  
## Voir aussi  
 [DOM \(Document Object Model\) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)