---
title: "Conservation des espaces lors du chargement ou de l’analyse XML2 | Documents Microsoft"
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
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 39e4270acc0e9a9df5c3855f8c087f41d9612197
ms.lasthandoff: 03/13/2017

---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Conservation des espaces lors du chargement ou de l'analyse de code XML
Cette rubrique décrit comment contrôler le comportement d'espace blanc de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait. Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés. Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait. Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière. Pour ce faire dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous devez conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.  
  
 Cette rubrique décrit le comportement des espaces blancs des méthodes qui remplissent les arborescences XML. Pour plus d’informations sur le contrôle des espaces blancs lorsque vous sérialisez des arborescences XML, consultez [conserver un espace blanc tandis que sérialisation](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Comportement des méthodes qui remplissent des arborescences XML  
 Les méthodes suivantes dans le <xref:System.Xml.Linq.XElement>et <xref:System.Xml.Linq.XDocument>classes de remplissent une arborescence XML.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> Vous pouvez remplir une arborescence XML à partir d’un fichier, un <xref:System.IO.TextReader>, un <xref:System.Xml.XmlReader>, ou une chaîne :</xref:System.Xml.XmlReader> </xref:System.IO.TextReader>  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>  
  
 Si la méthode ne prend pas <xref:System.Xml.Linq.LoadOptions>en tant qu’argument, la méthode ne conserve pas les espaces blancs non significatifs.</xref:System.Xml.Linq.LoadOptions>  
  
 Dans la plupart des cas, si la méthode accepte <xref:System.Xml.Linq.LoadOptions>en tant qu’argument, vous pouvez éventuellement conserver les espaces blancs non significatifs en tant que nœuds de texte dans l’arborescence XML.</xref:System.Xml.Linq.LoadOptions> Toutefois, si la méthode charge les données XML un <xref:System.Xml.XmlReader>, le <xref:System.Xml.XmlReader>détermine si les espaces blancs sont conservés.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> Définition <xref:System.Xml.Linq.LoadOptions>n’a aucun effet.</xref:System.Xml.Linq.LoadOptions>  
  
 Avec ces méthodes, si les espaces blancs sont conservés, espaces blancs non significatifs sont insérés dans l’arborescence XML en tant que <xref:System.Xml.Linq.XText>nœuds.</xref:System.Xml.Linq.XText> Si les espaces ne sont pas conservés, aucun nœud de texte n'est inséré.  
  
 Vous pouvez créer une arborescence XML à l’aide d’un <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> Les nœuds qui sont écrits dans le <xref:System.Xml.XmlWriter>sont remplis dans l’arborescence.</xref:System.Xml.XmlWriter> Toutefois, lorsque vous générez une arborescence XML à l’aide de cette méthode, tous les nœuds sont conservés, qu’ils soient constitués d’espaces ou non et que ces espaces soient significatifs ou non.  
  
## <a name="see-also"></a>Voir aussi  
 [L’analyse XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
