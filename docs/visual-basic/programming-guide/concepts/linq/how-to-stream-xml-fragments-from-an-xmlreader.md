---
title: "Procédure : diffuser des fragments XML en continu à partir d’un XmlReader (Visual Basic) | Documents Microsoft"
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
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
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
ms.openlocfilehash: c9c60bb4730ef6569390f76f63c40a2cbd1c9524
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>Procédure : diffuser des fragments XML en continu à partir d’un XmlReader (Visual Basic)
Lorsque vous devez traiter de grands fichiers XML, il peut être impossible de charger l’intégralité de l’arborescence XML en mémoire. Cette rubrique montre comment diffuser des fragments à l’aide d’un <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader>  
  
 Une des méthodes plus efficaces d’utiliser un <xref:System.Xml.XmlReader>pour lire <xref:System.Xml.Linq.XElement>objets consiste à écrire votre propre méthode d’axe personnalisée.</xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader> Une méthode d’axe retourne généralement une collection telle que <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>, comme illustré dans l’exemple dans cette rubrique.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> Dans la méthode d’axe personnalisée, après avoir créé le fragment XML en appelant le <xref:System.Xml.Linq.XNode.ReadFrom%2A>(méthode), retourner la collection à l’aide `yield return`.</xref:System.Xml.Linq.XNode.ReadFrom%2A> Cela fournit une sémantique d'exécution différée à votre méthode d'axe personnalisée.  
  
 Lorsque vous créez une arborescence XML à partir d’un <xref:System.Xml.XmlReader>objet, la <xref:System.Xml.XmlReader>doit être positionné sur un élément.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> Le <xref:System.Xml.Linq.XNode.ReadFrom%2A>méthode ne retourne pas jusqu'à ce qu’il a lu la balise de fermeture de l’élément.</xref:System.Xml.Linq.XNode.ReadFrom%2A>  
  
 Si vous souhaitez créer une arborescence partielle, vous pouvez instancier un <xref:System.Xml.XmlReader>, positionnez le lecteur sur le nœud que vous souhaitez convertir en un <xref:System.Xml.Linq.XElement>de l’arborescence, puis créer la <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader>  
  
 La rubrique [procédure : diffuser des fragments XML en continu avec accès aux informations d’en-tête (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contient des informations et un exemple sur la diffusion en continu un document plus complexe.  
  
 La rubrique [Comment : effectuer de diffusion en continu transformer des Documents XML volumineux (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contient un exemple d’utilisation de LINQ to XML pour transformer des documents XML extrêmement volumineux tout en maintenant un faible encombrement mémoire.  
  
## <a name="example"></a>Exemple  
 Cet exemple crée une méthode d'axe personnalisée. Vous pouvez l'interroger à l'aide d'une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]. La méthode d'axe personnalisée, `StreamRootChildDoc`, est une méthode conçue spécifiquement pour lire un document qui possède un élément `Child` à répétition.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Cet exemple génère la sortie suivante :  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Dans cet exemple, le document source est très petit. Toutefois, cet exemple aurait un faible encombrement mémoire même s'il y avait des millions d'éléments `Child`.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Implémentation IEnumerable(Of T) en Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)   
 [L’analyse XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
