---
title: "Vue d’ensemble (Visual Basic) des Classes LINQ to XML | Documents Microsoft"
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
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
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
ms.openlocfilehash: 12885f93bb7e56dd66d36090d41700195313e944
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-classes-overview-visual-basic"></a>LINQ to XML la vue d’ensemble de Classes (Visual Basic)
Cette rubrique fournit une liste de la [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes dans le <xref:System.Xml.Linq>espace de noms et une brève description de chacune.</xref:System.Xml.Linq>  
  
## <a name="linq-to-xml-classes"></a>Classes LINQ to XML  
  
### <a name="xattribute-class"></a>Classe XAttribute  
 <xref:System.Xml.Linq.XAttribute>représente un attribut XML.</xref:System.Xml.Linq.XAttribute> Pour des informations détaillées et des exemples, consultez [présentation (Visual Basic) de la classe XAttribute](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>Classe XCData  
 <xref:System.Xml.Linq.XCData>représente un nœud de texte CDATA.</xref:System.Xml.Linq.XCData>  
  
### <a name="xcomment-class"></a>Classe XComment  
 <xref:System.Xml.Linq.XComment>représente un commentaire XML.</xref:System.Xml.Linq.XComment>  
  
### <a name="xcontainer-class"></a>Classe XContainer  
 <xref:System.Xml.Linq.XContainer>est une classe de base abstraite pour tous les nœuds pouvant comporter des nœuds enfants.</xref:System.Xml.Linq.XContainer> Les classes suivantes dérivent de la <xref:System.Xml.Linq.XContainer>classe :</xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>Classe XDeclaration  
 <xref:System.Xml.Linq.XDeclaration>représente une déclaration XML.</xref:System.Xml.Linq.XDeclaration> Une déclaration XML est utilisée pour déclarer la version XML et l'encodage d'un document. Une déclaration XML spécifie également si le document XML est autonome. Si un document est autonome, il n'existe aucune déclaration de marque externe, que ce soit dans un DTD externe ou dans une entité de paramètre externe référencée à partir du sous-ensemble interne.  
  
### <a name="xdocument-class"></a>Classe XDocument  
 <xref:System.Xml.Linq.XDocument>représente un document XML.</xref:System.Xml.Linq.XDocument> Pour des informations détaillées et des exemples, consultez [présentation (Visual Basic) de la classe XDocument](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>Classe XDocumentType  
 <xref:System.Xml.Linq.XDocumentType>représente une définition de Type de Document (DTD) XML.</xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xelement-class"></a>Classe XElement  
 <xref:System.Xml.Linq.XElement>représente un élément XML.</xref:System.Xml.Linq.XElement> Pour des informations détaillées et des exemples, consultez [présentation (Visual Basic) de la classe XElement](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### <a name="xname-class"></a>Classe XName  
 <xref:System.Xml.Linq.XName>représente des noms d’éléments (<xref:System.Xml.Linq.XElement>) et les attributs (<xref:System.Xml.Linq.XAttribute>).</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XName> Pour des informations détaillées et des exemples, consultez [présentation (Visual Basic) de la classe XDocument](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] est conçu pour rendre les noms XML aussi simples que possible. En raison de leur complexité, les noms XML sont souvent considérés comme l'un des aspects les plus difficiles à appréhender du langage XML. En fait, cette complexité provient non pas des espaces de noms, que les développeurs utilisent régulièrement dans la programmation, mais des préfixes d'espaces de noms. Les préfixes d'espaces de noms peuvent être utiles pour réduire le nombre de frappes au clavier nécessaires lors de la saisie de code XML ou pour améliorer la lisibilité du code XML. Toutefois, les préfixes sont souvent simplement un raccourci pour l'ensemble de l'espace de noms XML, et ils ne sont pas nécessaires dans la plupart des cas. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]simplifie les noms XML en résolvant tous les préfixes à leur espace de noms XML correspondant. Les préfixes sont disponibles, s’ils sont requis par le <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>méthode.</xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>  
  
 Il est possible, si nécessaire, de contrôler les préfixes d'espaces de noms. Dans certains cas, si vous travaillez avec d'autres systèmes XML, tels que XSLT ou XAML, vous devez contrôler les préfixes d'espaces de noms. Par exemple, si vous avez une expression XPath qui utilise des préfixes d'espaces de noms et qui est incorporée dans une feuille de style XSLT, vous devez vous assurer que votre document XML est sérialisé avec des préfixes d'espaces de noms qui correspondent à ceux utilisés dans l'expression XPath.  
  
### <a name="xnamespace-class"></a>Classe XNamespace  
 <xref:System.Xml.Linq.XNamespace>représente un espace de noms pour un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XNamespace> Espaces de noms sont un composant d’un <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>  
  
### <a name="xnode-class"></a>Classe XNode  
 <xref:System.Xml.Linq.XNode>est une classe abstraite qui représente les nœuds d’une arborescence XML.</xref:System.Xml.Linq.XNode> Les classes suivantes dérivent de la <xref:System.Xml.Linq.XNode>classe :</xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XText></xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType></xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>Classe XNodeDocumentOrderComparer  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>Fournit des fonctionnalités permettant de comparer des nœuds pour l’ordre des documents.</xref:System.Xml.Linq.XNodeDocumentOrderComparer>  
  
### <a name="xnodeequalitycomparer-class"></a>Classe XNodeEqualityComparer  
 <xref:System.Xml.Linq.XNodeEqualityComparer>Fournit des fonctionnalités permettant de comparer des nœuds pour l’égalité des valeurs.</xref:System.Xml.Linq.XNodeEqualityComparer>  
  
### <a name="xobject-class"></a>Classe XObject  
 <xref:System.Xml.Linq.XObject>est une classe de base abstraite de <xref:System.Xml.Linq.XNode>et <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XObject> Elle fournit des fonctionnalités d'annotation et d'événement.  
  
### <a name="xobjectchange-class"></a>Classe XObjectChange  
 <xref:System.Xml.Linq.XObjectChange>Spécifie le type d’événement lorsqu’un événement est déclenché pour un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject></xref:System.Xml.Linq.XObjectChange>  
  
### <a name="xobjectchangeeventargs-class"></a>Classe XObjectChangeEventArgs  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>Fournit des données pour le <xref:System.Xml.Linq.XObject.Changing>et <xref:System.Xml.Linq.XObject.Changed>événements.</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing></xref:System.Xml.Linq.XObjectChangeEventArgs>  
  
### <a name="xprocessinginstruction-class"></a>Classe XProcessingInstruction  
 <xref:System.Xml.Linq.XProcessingInstruction>représente une instruction de traitement XML.</xref:System.Xml.Linq.XProcessingInstruction> Une instruction de traitement communique des informations à une application qui traite le code XML.  
  
### <a name="xtext-class"></a>Classe XText  
 <xref:System.Xml.Linq.XText>représente un nœud de texte.</xref:System.Xml.Linq.XText> Dans la plupart des cas, il est inutile d'utiliser cette classe. Cette classe est utilisée principalement pour du contenu mixte.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML programmation présentation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
