---
title: "Entrée XmlDataDocument dans XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 813c240ca0115015158988e1226d25890cde6939
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xmldatadocument-input-to-xsltransform"></a>Entrée XmlDataDocument dans XslTransform
> [!NOTE]
>  La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Consultez [à l’aide de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) pour plus d’informations.  
  
 Microsoft [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implémente le DOM (Document Object Model) XML pour fournir l'accès aux données des documents XML et des classes supplémentaires pour lire et écrire des documents XML, ainsi que pour naviguer dans ceux-ci. Le <xref:System.Xml.XmlDataDocument>, située dans le <xref:System.Xml> espace de noms fournit un accès relationnel aux données grâce à sa capacité à synchroniser avec les données relationnelles dans le <xref:System.Data.DataSet>. Vous pouvez afficher et manipuler simultanément un document XML structuré par l'intermédiaire de la représentation relationnelle de l'objet <xref:System.Data.DataSet> ou manipuler le document XML semi-structuré par l'intermédiaire de la représentation DOM de l'objet <xref:System.Xml.XmlDataDocument>. C'est pourquoi l'objet <xref:System.Xml.XmlDataDocument> dépasse les limites des mondes XML et relationnels.  
  
 Si les données sont stockées dans une structure relationnelle et que vous souhaitez qu'elles soient une entrée dans une transformation XSLT, vous pouvez charger les données relationnelles dans un objet <xref:System.Data.DataSet> et les associer à l'objet <xref:System.Xml.XmlDataDocument>. L'objet <xref:System.Xml.XPath.XPathNavigator>, l'entrée dans l'objet <xref:System.Xml.Xsl.XslTransform>, est implémenté sur l'objet <xref:System.Xml.XmlDataDocument> à l'aide de l'interface <xref:System.Xml.XPath.IXPathNavigable>. En prenant des données relationnelles, en les chargeant dans un objet <xref:System.Data.DataSet> et en utilisant la synchronisation dans l'objet <xref:System.Xml.XmlDataDocument>, il est à présent possible d'effectuer des transformations XSLT sur des données relationnelles.  
  
 Pour plus d’informations sur l’application d’une transformation aux données relationnelles, consultez [appliquer une transformation XSLT à un DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.XmlDataDocument>  
 [Synchronisation DataSet et XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [Transformations XSLT avec la classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XslTransform Class Implements the XSLT Processor](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [XPathNavigator dans les Transformations](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator dans les Transformations](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Entrée XPathDocument dans XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Entrée XmlDocument dans XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
