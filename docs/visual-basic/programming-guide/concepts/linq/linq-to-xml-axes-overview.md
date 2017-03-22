---
title: "Vue d’ensemble (Visual Basic) des Axes LINQ to XML | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b127aa6b443e865c76831d886f110550ec785e9b
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>LINQ to XML Axes présentation (Visual Basic)
Après avoir créé une arborescence XML ou chargé un document XML dans une arborescence XML, vous pouvez l'interroger pour rechercher des éléments et des attributs et récupérer leurs valeurs. Récupérer des collections à l’aide du *des méthodes d’axe*, également appelé *axes*. Certains des axes sont des méthodes dans le <xref:System.Xml.Linq.XElement>et <xref:System.Xml.Linq.XDocument>qui retournent des classes <xref:System.Collections.Generic.IEnumerable%601>collections.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> Certains des axes sont des méthodes d’extension dans la <xref:System.Xml.Linq.Extensions>classe.</xref:System.Xml.Linq.Extensions> Les axes qui sont implémentés en tant que méthodes d’extension opèrent sur des collections et retournent des collections.  
  
 Comme décrit dans [vue d’ensemble de la classe XElement](http://msdn.microsoft.com/library/d35180fe-7016-4895-9bfc-ba1e3f7875ec), un <xref:System.Xml.Linq.XElement>objet représente un seul nœud d’élément.</xref:System.Xml.Linq.XElement> Le contenu de l'élément peut être complexe (parfois appelé contenu structuré) ou il peut s'agir d'un simple élément. Un élément simple peut être vide ou peut contenir une valeur. Si le nœud contient du contenu structuré, vous pouvez utiliser les différentes méthodes d'axe pour récupérer des énumérations d'éléments descendants. Les méthodes d’axe les plus couramment utilisées sont <xref:System.Xml.Linq.XContainer.Elements%2A>et <xref:System.Xml.Linq.XContainer.Descendants%2A>.</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XContainer.Elements%2A>  
  
 Outre les méthodes d’axe, qui retournent des collections, il existe deux autres méthodes que vous utiliserez fréquemment dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] des requêtes. La <xref:System.Xml.Linq.XContainer.Element%2A>méthode retourne un seul <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer.Element%2A> La <xref:System.Xml.Linq.XElement.Attribute%2A>méthode retourne un seul <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement.Attribute%2A>  
  
 Pour de nombreux scénarios, les requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] constituent la manière la plus puissante d'examiner une arborescence, d'en extraire des données et de la transformer. [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]les requêtes fonctionnent sur les objets qui implémentent <xref:System.Collections.Generic.IEnumerable%601>et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] axes retour <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>collections, et <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XAttribute>collections.</xref:System.Xml.Linq.XAttribute> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.Generic.IEnumerable%601> Vous avez besoin de ces collections pour effectuer vos requêtes.  
  
 Outre les méthodes d’axe qui récupèrent des collections d’éléments et d’attributs, il existe des méthodes d’axe qui vous permettent d’itérer au sein de l’arborescence en détail. Par exemple, au lieu de travailler au niveau des éléments et des attributs, vous pouvez travailler avec les nœuds de l'arborescence. Les nœuds représentent un niveau de granularité plus élevé que les éléments et les attributs. Lorsque vous travaillez avec des nœuds, vous pouvez examiner les commentaires XML, les nœuds de texte, les instructions de traitement, et bien plus encore. Cette fonctionnalité est importante, par exemple pour quelqu'un qui écrit un traitement de texte et qui souhaite enregistrer des documents au format XML. Toutefois, la plupart des programmeurs XML sont principalement concernés par les éléments, les attributs et leurs valeurs.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Méthodes pour récupérer une collection d’éléments  
 Voici un résumé des méthodes de la <xref:System.Xml.Linq.XElement>classe (ou ses classes de base) que vous appelez sur un <xref:System.Xml.Linq.XElement>pour retourner une collection d’éléments.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement>  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName>|Retourne un <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>des ancêtres de cet élément.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Une surcharge retourne un <xref:System.Collections.Generic.IEnumerable%601>des <xref:System.Xml.Linq.XElement>ancêtres qui ont le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName>|Retourne un <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>des descendants de cet élément.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Une surcharge retourne un <xref:System.Collections.Generic.IEnumerable%601>des <xref:System.Xml.Linq.XElement>descendants qui ont le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>|Retourne un <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>des éléments enfants de cet élément.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Une surcharge retourne un <xref:System.Collections.Generic.IEnumerable%601>des <xref:System.Xml.Linq.XElement>éléments enfants qui ont le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName>|Retourne un <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>des éléments enfants placés après cet élément.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Une surcharge retourne un <xref:System.Collections.Generic.IEnumerable%601>des <xref:System.Xml.Linq.XElement>éléments après cet élément qui ont le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>|Retourne un <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>des éléments enfants placés avant cet élément.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Une surcharge retourne un <xref:System.Collections.Generic.IEnumerable%601>des <xref:System.Xml.Linq.XElement>éléments avant cet élément qui ont le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName>|Retourne un <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>de cet élément et ses ancêtres.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Une surcharge retourne un <xref:System.Collections.Generic.IEnumerable%601>des <xref:System.Xml.Linq.XElement>éléments qui ont le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName>|Retourne un <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>de cet élément et ses descendants.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Une surcharge retourne un <xref:System.Collections.Generic.IEnumerable%601>des <xref:System.Xml.Linq.XElement>éléments qui ont le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601>|  
  
## <a name="method-for-retrieving-a-single-element"></a>Méthode pour récupérer un seul élément  
 La méthode suivante récupère un seul enfant d’un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement>  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>|Retourne le premier enfant <xref:System.Xml.Linq.XElement>objet qui a le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XElement>|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Méthode pour récupérer une collection d’attributs  
 La méthode suivante récupère des attributs d’un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement>  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName>|Retourne un <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XAttribute>de tous les attributs.</xref:System.Xml.Linq.XAttribute> </xref:System.Collections.Generic.IEnumerable%601>|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Méthode pour récupérer un seul attribut  
 La méthode suivante récupère un seul attribut d’un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement>  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>|Retourne <xref:System.Xml.Linq.XAttribute>qui a le type spécifié <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XAttribute>|  
  
## <a name="see-also"></a>Voir aussi  
 [Axes LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
