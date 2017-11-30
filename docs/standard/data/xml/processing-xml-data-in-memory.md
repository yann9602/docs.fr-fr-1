---
title: "Traitement de données XML en mémoire"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ec4ccbff095071b279e07cee6a1aab3ca830423f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="processing-xml-data-in-memory"></a>Traitement de données XML en mémoire
Microsoft .NET Framework comprend trois modèles pour le traitement des données XML : le <xref:System.Xml.XmlDocument> (classe), le <xref:System.Xml.XPath.XPathDocument> (classe), et [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 La classe <xref:System.Xml.XmlDocument> implémente les recommandations du W3C relatives aux modèles objet de document (DOM), niveaux 1 et 2 (noyau). Le DOM est une représentation sous la forme d'une arborescence (cache) en mémoire d'un document XML. L'objet <xref:System.Xml.XmlDocument> et les classes y afférentes permettent de construire des documents XML, de charger et d'accéder à des données, de modifier des données et d'enregistrer des modifications.  
  
 La classe <xref:System.Xml.XPath.XPathDocument> est un magasin de données en mémoire en lecture seule basé sur le modèle de données XPath. La classe <xref:System.Xml.XPath.XPathNavigator> propose plusieurs options de modification et fonctionnalités de navigation à l'aide d'un modèle de curseur entre des documents XML contenus dans la classe <xref:System.Xml.XPath.XPathDocument> en lecture seule ainsi que dans la classe <xref:System.Xml.XmlDocument>.  
  
 [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) est le nouveau modèle dans le .NET Framework version 3.5 pour le traitement des données XML. Il s’agit d’un modèle en mémoire qui exploite [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). LINQ étend la syntaxe des langages C# et Visual Basic pour fournir de nouvelles capacités de requête.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Traitement des données XML à l’aide du modèle DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 Explique l'utilisation de l'objet <xref:System.Xml.XmlDocument> et des classes y afférentes pour le traitement de données XML.  
  
 [Traitement des données XML à l’aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 Explique l'utilisation des classes <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument> et <xref:System.Xml.XPath.XPathNavigator> pour le traitement de données XML.  
  
 [Traitement des données XML à l’aide de LINQ to XML](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 Fournit une brève vue d'ensemble de LINQ to XML et indique des liens vers la documentation LINQ to XML.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Documents et données XML](../../../../docs/standard/data/xml/index.md)
