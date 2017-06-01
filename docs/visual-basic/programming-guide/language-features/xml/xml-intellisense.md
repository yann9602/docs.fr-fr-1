---
title: XML IntelliSense dans Visual Basic | Documents Microsoft
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
helpviewer_keywords:
- Visual Basic code, XML
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: 59506ce9-d64e-417e-90fc-e9fe19f0a8fa
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8c43db3d2010e4fa92eebeec8a973c50052b1340
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="xml-intellisense-in-visual-basic"></a>XML IntelliSense dans Visual Basic
L’éditeur de Code Visual Basic inclut des fonctionnalités IntelliSense pour XML qui offrent une saisie semi-automatique de mots pour les éléments définis dans un schéma XML. Si vous incluez un fichier de définition de schéma XML (XSD) dans votre projet et importer l’espace de noms cible du schéma à l’aide de la `Imports` instruction, l’éditeur de Code inclura des éléments du schéma XSD dans la liste IntelliSense des variables de membre valide pour <xref:System.Xml.Linq.XElement>et <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> L’illustration suivante montre la liste de membres IntelliSense pour un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement>  
  
 ![XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")  
XML IntelliSense  
  
## <a name="enabling-xml-intellisense-in-visual-basic"></a>Activer XML IntelliSense dans Visual Basic  
 Pour activer XML IntelliSense dans Visual Basic, vous devez inclure un fichier de schéma XSD dans votre projet Visual Basic. Vous devez également importer l’espace de noms cible du schéma XSD dans votre fichier de code à l’aide de la `Imports` instruction. Vous pouvez également ajouter l’espace de noms cible à la liste de l’espace de noms au niveau du projet à l’aide de la **références** page du Concepteur de projets Visual Basic. Pour obtenir des exemples, consultez [Comment : activer XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md). Pour plus d’informations, consultez [l’instruction Imports (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) et [Page références, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
 Notez que par défaut, vous ne pouvez pas voir les fichiers de schéma XSD dans les projets Visual Basic. Il se peut que vous deviez cliquer sur le **afficher tous les fichiers** pour sélectionner un fichier XSD à inclure dans votre projet.  
  
### <a name="generating-a-schema-file-schema-inference"></a>Génération d’un fichier de schéma (inférence de schéma)  
 Vous pouvez créer un schéma XSD pour un fichier XML existant en déduisant le schéma XSD à l’aide des outils XML Visual Studio.  
  
-   À compter de SP1, vous pouvez utiliser l’Assistant schéma XML vers pour créer un jeu de schémas XML qui est déduit à partir d’un ou plusieurs documents XML et l’inclure dans votre projet. Vous pouvez utiliser n’importe quelle combinaison de documents XML sous la forme de fichiers texte, XML à partir d’une adresse HTTP Internet ou code XML tapé ou collé dans l’Assistant schéma XML vers. Pour accéder à l’Assistant schéma XML vers, cliquez sur **ajouter un nouvel élément** sur la **projet** menu et ajoutez un **XML au schéma** modèle à partir de le le **données** ou **éléments communs** groupe de modèles. Une fois que vous avez inclus toutes les sources de document XML pour déduire le jeu de schémas XML à partir de, cliquez sur **OK** pour créer le schéma déduit jeu. Pour plus d’informations, consultez [Assistant XML vers schéma](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md).  
  
-   Vous pouvez également utiliser l’éditeur XML de Visual Studio pour déduire un schéma XSD à partir d’un fichier XML. Pour créer un schéma XML défini à l’aide de l’éditeur XML, ouvrez un fichier XML dans le Concepteur XML de Visual Studio, puis cliquez **Create Schema** sur la **XML** menu. Après avoir créé le jeu de schémas XSD, vous pouvez enregistrer le jeu de schémas créés dans un ou plusieurs fichiers XSD et les inclure dans votre projet. Pour plus d’informations, consultez[Comment : activer XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).  
  
 Notez que les différents jeux de schémas XSD peut-être être déduits à partir de plusieurs documents XML conçus pour avoir le même schéma. Cela peut se produire lorsque des éléments et attributs particuliers sont trouvées dans un fichier XML et pas dans un autre, ou lorsque les éléments sont inclus dans un ordre différent, par exemple. Vous devez examiner les jeux de schémas XSD déduits pour l’exhaustivité et la précision lorsque vous utilisez l’inférence de schéma XSD.  
  
## <a name="member-list"></a>Liste des membres  
 Après avoir tapé un point (.) pour délimiter une instance d’un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objet (ou une instance de `IEnumerable(Of XElement)` ou `IEnumerable(Of XDocument)`), Visual Basic IntelliSense affiche une liste des membres d’objet possibles.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> La liste initiale inclut trois options qui représentent les propriétés d’axe XML, comme décrit dans la liste suivante.  
  
|Option|Description|  
|---|---|  
|**\< >**|Sélectionnez cette option pour afficher des éléments d’une liste d’enfants possibles. Pour plus d’informations, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et <xref:System.Xml.Linq.XContainer.Elements%2A>méthode.</xref:System.Xml.Linq.XContainer.Elements%2A>|  
|**@**|Sélectionnez cette option pour afficher une liste d’attributs possibles. Pour plus d’informations, consultez [propriétés d’axe XML](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md). Cette option est disponible uniquement pour les objets de type <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>|  
|**…\< >**|Sélectionnez cette option pour afficher une liste d’éléments descendants. Pour plus d’informations, consultez [Comment : accéder aux éléments de Descendant XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) et <xref:System.Xml.Linq.XContainer.Elements%2A>méthode.</xref:System.Xml.Linq.XContainer.Elements%2A>|  
  
 Sélectionnez ou commencez à taper une des options de la liste XML. La liste des membres affichera ensuite les membres potentiels du schéma XML qui sont spécifiques à l’option sélectionnée. Si vous avez des espaces de noms XML importés associés à un préfixe d’espace de noms XML spécifique, une liste de préfixes d’espace de noms XML potentiels est incluse dans la liste des membres.  
  
 Par exemple, considérez le schéma XSD suivant.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified"   
           elementFormDefault="qualified"   
           targetNamespace="http://SamplePurchaseOrder"   
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="PurchaseOrders">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="PurchaseOrder">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Address" />  
              <xs:element name="Items" />  
              <xs:element name="Comment" />  
            </xs:sequence>  
            <xs:attribute name="PurchaseOrderNumber" type="xs:unsignedShort" use="required" />  
            <xs:attribute name="OrderDate" type="xs:string" use="required" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 XML Valid pour le schéma XSD se présente comme suit.  
  
```xml  
<?xml version="1.0"?>  
<PurchaseOrders xmlns="http://SamplePurchaseOrder">  
  <PurchaseOrder PurchaseOrderNumber="12345" OrderDate="2000-1-1">  
    <Address />  
    <Items />  
    <Comment />  
  </PurchaseOrder>  
</PurchaseOrders>  
```  
  
 Si vous incluez ce fichier de schéma XSD dans un projet et importez l’espace de noms cible du schéma XSD dans votre fichier de code ou un projet, Visual Basic IntelliSense affiche les membres à partir du schéma lorsque vous tapez votre code Visual Basic. Si l’espace de noms cible pour le schéma XSD est importé comme espace de noms par défaut et que vous tapez la commande suivante, IntelliSense affiche une liste d’éléments enfants possibles pour le `PurchaseOrder` (élément XML).  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 La liste se compose des éléments adresse, commentaire et éléments.  
  
### <a name="certainty-levels-for-intellisense-list-items"></a>Niveaux de certitude pour les éléments de liste IntelliSense  
 Détermination du type XSD à utiliser pour IntelliSense n’est pas exact. En conséquence, XML IntelliSense affichera souvent une liste développée de membres possibles. Pour sélectionner un élément dans la liste des membres IntelliSense, les éléments sont affichés avec une indication du niveau de certitude que XML IntelliSense propose pour un membre particulier.  
  
 Quelquefois XML IntelliSense peut identifier un type spécifique à partir du schéma XSD. Dans ces cas, il affichera des éléments enfants possibles, des attributs ou des éléments descendants pour ce type XSD avec un degré élevé de certitude. Ces éléments sont identifiés par une coche.  
  
 Cependant, parfois XML IntelliSense n’est pas en mesure d’identifier un type spécifique à partir du schéma XSD. Dans ces cas, il affichera une liste développée des éléments enfants possibles, des attributs ou des éléments descendants à partir du schéma XSD pour le projet avec un faible degré de certitude. Ces éléments sont identifiés par un point d’interrogation.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : activer XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)   
 [Assistant schéma XML vers](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)   
 [Imports, instruction (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Propriété d’axe d’attribut XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)   
 [Propriété d’axe Descendant XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [Page Références, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)
