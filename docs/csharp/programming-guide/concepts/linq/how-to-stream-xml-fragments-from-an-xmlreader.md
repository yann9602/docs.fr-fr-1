---
title: "Guide pratique pour diffuser des fragments XML en continu à partir d’un XmlReader (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4bb11e120a123b701e45916b983032797c0ea8b6
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Guide pratique pour diffuser des fragments XML en continu à partir d’un XmlReader (C#)
Lorsque vous devez traiter de grands fichiers XML, il peut être impossible de charger l’intégralité de l’arborescence XML en mémoire. Cette rubrique montre comment diffuser des fragments à l’aide d’un <xref:System.Xml.XmlReader>.  
  
 L’une des méthodes les plus efficaces pour utiliser un <xref:System.Xml.XmlReader> dans le but de lire des objets <xref:System.Xml.Linq.XElement> est d’écrire votre propre méthode d’axe personnalisée. Une méthode d’axe retourne généralement une collection telle qu’une <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, comme le montre l’exemple de cette rubrique. Dans la méthode d’axe personnalisée, après avoir créé le fragment XML en appelant la méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A>, retournez la collection à l’aide de `yield return`. Cela fournit une sémantique d'exécution différée à votre méthode d'axe personnalisée.  
  
 Lorsque vous créez une arborescence XML à partir d’un objet <xref:System.Xml.XmlReader>, le <xref:System.Xml.XmlReader> doit être positionné sur un élément. La méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A> ne retourne rien tant qu’elle n’a pas lu la balise de fermeture de l’élément.  
  
 Si vous souhaitez créer une arborescence partielle, vous pouvez instancier un <xref:System.Xml.XmlReader>, positionner le lecteur sur le nœud que vous souhaitez convertir en arborescence <xref:System.Xml.Linq.XElement>, puis créer l’objet <xref:System.Xml.Linq.XElement>.  
  
 La rubrique [Guide pratique pour diffuser des fragments XML en continu avec accès aux informations d’en-tête (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contient des informations et un exemple sur la diffusion en continu d’un document plus complexe.  
  
 La rubrique [Guide pratique pour effectuer une transformation de streaming de documents XML volumineux (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contient un exemple d’utilisation de LINQ to XML pour transformer des documents XML extrêmement volumineux tout en maintenant un faible encombrement mémoire.  
  
## <a name="example"></a>Exemple  
 Cet exemple crée une méthode d'axe personnalisée. Vous pouvez l'interroger à l'aide d'une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]. La méthode d'axe personnalisée, `StreamRootChildDoc`, est une méthode conçue spécifiquement pour lire un document qui possède un élément `Child` à répétition.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Cet exemple génère la sortie suivante :  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Dans cet exemple, le document source est très petit. Toutefois, cet exemple aurait un faible encombrement mémoire même s'il y avait des millions d'éléments `Child`.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de code XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
