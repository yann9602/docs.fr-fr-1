---
title: Prise en charge du type dans les classes System.Xml
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 14821ef78f20d1ff303afacb42415e4017a92742
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="type-support-in-the-systemxml-classes"></a>Prise en charge du type dans les classes System.Xml
Dans .NET Framework version 2.0, les classes XML noyau ont été améliorées pour inclure des fonctionnalités de prise en charge du type. Les classes <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.XPath.XPathNavigator> comprennent des fonctions de prise en charge du type, notamment la possibilité de conversion entre des types de schémas XML et des types CLR (Common Language Runtime).  
  
 Dans .NET Framework version 2.0, les classes <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.XPath.XPathNavigator> ont été améliorées pour inclure des fonctions de prise en charge du type.  
  
-   Le <xref:System.Xml.XmlReader> et <xref:System.Xml.XPath.XPathNavigator> classes chaque incluent un **SchemaInfo** propriété qui retourne les informations de schéma sur un nœud.  
  
-   Le **ReadContentAs** et **ReadElementContentAs** et les méthodes sur la <xref:System.Xml.XmlReader> classe lire une valeur de texte et la convertissent en valeur CLR en un seul appel de méthode.  
  
-   La méthode <xref:System.Xml.XmlWriter.WriteValue%2A> de la classe <xref:System.Xml.XmlWriter> convertit un type CLR en type de schéma XML lors de l'écriture de XML.  
  
-   Le **ValueAs** et <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> propriétés sur la <xref:System.Xml.XPath.XPathNavigator> classe retournent une valeur de nœud et la convertir en valeur CLR en un seul appel de méthode.  
  
> [!NOTE]
>  Dans .NET Framework version 1.0, la classe <xref:System.Xml.XmlConvert> était nécessaire pour la conversion entre les types CLR et de schéma XML.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mappage des Types de données XML en Types CLR](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 Décrit les mappages par défaut des types de données XML en types CLR.  
  
 [Notes de mise en œuvre de prise en charge de Type XML](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Explique certains détails de l'implémentation de la prise en charge du type.  
  
 [Conversion de Types de données XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Décrit l'utilisation de la classe <xref:System.Xml.XmlConvert> pour la conversion entre des types CLR et de schéma XML.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [L’accès à fortement typée des données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
