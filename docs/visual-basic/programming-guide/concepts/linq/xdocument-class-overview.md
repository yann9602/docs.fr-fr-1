---
title: "Vue d’ensemble de la classe XDocument (Visual Basic) | Documents Microsoft"
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
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
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
ms.openlocfilehash: 31111b23adb019aad3ad55787c073dc02446291d
ms.lasthandoff: 03/13/2017

---
# <a name="xdocument-class-overview-visual-basic"></a>Vue d’ensemble de la classe XDocument (Visual Basic)
Cette rubrique présente la <xref:System.Xml.Linq.XDocument>classe.</xref:System.Xml.Linq.XDocument>  
  
## <a name="overview-of-the-xdocument-class"></a>Vue d'ensemble de la classe XDocument  
 La <xref:System.Xml.Linq.XDocument>classe contient les informations nécessaires à un document XML valide.</xref:System.Xml.Linq.XDocument> Cela inclut une déclaration XML, des instructions de traitement et des commentaires.  
  
 Notez que vous devez uniquement créer des <xref:System.Xml.Linq.XDocument>objets, si vous avez besoin de la fonctionnalité spécifique fournie par la <xref:System.Xml.Linq.XDocument>classe.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument> Dans de nombreux cas, vous pouvez travailler directement avec <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> Travailler directement avec <xref:System.Xml.Linq.XElement>est un modèle de programmation plus simple.</xref:System.Xml.Linq.XElement>  
  
 <xref:System.Xml.Linq.XDocument>dérive de <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XDocument> Par conséquent, il peut contenir des nœuds enfants. Toutefois, <xref:System.Xml.Linq.XDocument>les objets peuvent avoir qu’un seul enfant <xref:System.Xml.Linq.XElement>nœud.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> Cela reflète la norme XML selon laquelle il ne doit y avoir qu'un seul élément racine dans un document XML.  
  
## <a name="components-of-xdocument"></a>Composants de XDocument  
 Un <xref:System.Xml.Linq.XDocument>peut contenir les éléments suivants :</xref:System.Xml.Linq.XDocument>  
  
-   Un <xref:System.Xml.Linq.XDeclaration>objet.</xref:System.Xml.Linq.XDeclaration> <xref:System.Xml.Linq.XDeclaration>permet de spécifier les parties pertinentes d’une déclaration XML : la version XML, l’encodage du document, et si le document XML est autonome.</xref:System.Xml.Linq.XDeclaration>  
  
-   Un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement> Il s'agit du nœud racine du document XML.  
  
-   Un nombre quelconque de <xref:System.Xml.Linq.XProcessingInstruction>objets.</xref:System.Xml.Linq.XProcessingInstruction> Une instruction de traitement communique des informations à une application qui traite le code XML.  
  
-   Un nombre quelconque de <xref:System.Xml.Linq.XComment>objets.</xref:System.Xml.Linq.XComment> Les commentaires seront des frères de l'élément racine. Le <xref:System.Xml.Linq.XComment>objet ne peut pas être le premier argument de la liste, car il n’est pas valide pour un document XML démarrer avec un commentaire.</xref:System.Xml.Linq.XComment>  
  
-   Un <xref:System.Xml.Linq.XDocumentType>pour le DTD.</xref:System.Xml.Linq.XDocumentType>  
  
 Lorsque vous sérialisez un <xref:System.Xml.Linq.XDocument>, même si `XDocument.Declaration` est `null`, la sortie aura une déclaration XML si le writer a `Writer.Settings.OmitXmlDeclaration` la valeur `false` (la valeur par défaut).</xref:System.Xml.Linq.XDocument>  
  
 Par défaut, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] définit la version à « 1.0 » l'encodage à « utf-8 ».  
  
## <a name="using-xelement-without-xdocument"></a>Utilisation de XElement sans XDocument  
 Comme mentionné précédemment, la <xref:System.Xml.Linq.XElement>classe est la classe principale dans le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] interface de programmation.</xref:System.Xml.Linq.XElement> Dans de nombreux cas, votre application ne nécessitera pas la création d'un document. À l’aide de la <xref:System.Xml.Linq.XElement>(classe), vous pouvez créer une arborescence XML, ajouter d’autres arborescences XML, modifiez l’arborescence XML et enregistrez celui-ci.</xref:System.Xml.Linq.XElement>  
  
## <a name="using-xdocument"></a>Utilisation de XDocument  
 Pour construire un <xref:System.Xml.Linq.XDocument>, utilisez la construction fonctionnelle, comme pour construire des <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument>  
  
 Le code suivant crée un <xref:System.Xml.Linq.XDocument>objet et ses objets contenus associés.</xref:System.Xml.Linq.XDocument>  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 Lorsque vous examinez le fichier test.xml, vous obtenez la sortie suivante :  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML programmation présentation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
