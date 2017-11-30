---
title: Options de traitement XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 18f8f9c76a1842517340eaa3f74b4778f869403e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-processing-options"></a>Options de traitement XML
Reportez-vous aux tableaux suivants pour obtenir une liste des technologies Microsoft que vous pouvez utiliser pour traiter des données XML.  
  
## <a name="net-framework-options"></a>Options du .NET Framework  
  
|**Option**|**Type de traitement**|**Description**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(espace de noms <xref:System.Xml.Linq>)|En mémoire|-Basée sur la technologie Integrated Query (LINQ).<br />: Fournit l’expérience de requête semblable à SQL des objets, les données relationnelles et les données XML.<br />-Fournit des fonctionnalités de création et de transformation de documents intuitives.<br />-Utilisez cette option si vous écrivez un nouveau code.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Basé sur les flux|: Fournit un moyen rapide, non mis en cache et avant uniquement pour accéder aux données XML.<br />-Vous pouvez créer des objets à l’aide de la <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> (méthode) et spécifier l’ensemble de fonctionnalités à activer sur l’objet à l’aide de la <xref:System.Xml.XmlReaderSettings> classe.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Basé sur les flux|: Fournit un moyen rapide, non mis en cache et avant uniquement de générer des données XML.<br />-Vous pouvez créer des objets à l’aide de la <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> (méthode) et spécifier l’ensemble de fonctionnalités à activer sur l’objet à l’aide de la <xref:System.Xml.XmlWriterSettings> classe.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|En mémoire|-Implémente la [W3C Document objet Model (DOM) Level 1 Core](http://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) et [DOM Level 2 Core](http://www.w3.org/TR/DOM-Level-2-Core/) recommandations.<br />-Vous pouvez créer, insérer, supprimer et modifier des nœuds à l’aide des méthodes et propriétés basées sur le modèle DOM habituel.<br />-Utilisez cette option si vous modifiez du code existant qui utilise le modèle DOM W3C.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|En mémoire|-Offre plusieurs options d’édition et les fonctionnalités de navigation à l’aide d’un modèle de curseur.<br />-Documents XML peuvent être contenus dans un <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> objet.<br />-Procure d’excellentes performances pour le traitement des données XML en lecture seule.<br />-Utilisez cette option si vous modifiez du code existant avec les requêtes XPath ou des transformations XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|En mémoire|: Fournit des options pour la transformation des données XML à l’aide de transformations XSL.<br />-La [compilateur XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) vous permet de vous faire référence précompilé transformations dans votre application.|  
  
## <a name="win32-and-com-based-options"></a>Options Win32 et COM  
  
|**Option**|**Description**|  
|----------------|---------------------|  
|[XmlLite](http://go.microsoft.com/fwlink/?LinkId=93723)|-Un rapide et sécurisée, non mise en cache, avant uniquement analyseur XML qui vous permet de générer hautes performances des applications XML.<br />-Fonctionne avec n’importe quel langage qui peut utiliser des bibliothèques de liens dynamiques (DLL). Nous vous recommandons d’utiliser C++.|  
|[MSXML](http://go.microsoft.com/fwlink/?LinkId=93722)|Technologie compatible COM pour le traitement XML qui est inclus avec le système d’exploitation Windows.<br />-Fournit une implémentation native du modèle DOM avec prise en charge de XPath et XSLT.<br />-Contient l’analyseur basé sur des événements SAX2.|  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des données XML à l’aide du modèle DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [Traitement des données XML à l’aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Compilateur XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
