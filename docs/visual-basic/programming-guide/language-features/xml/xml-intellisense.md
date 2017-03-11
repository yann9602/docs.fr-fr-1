---
title: "XML IntelliSense in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, XML"
  - "XML IntelliSense [Visual Basic]"
  - "XML [Visual Basic], IntelliSense"
  - "IntelliSense [Visual Basic], XML"
ms.assetid: 59506ce9-d64e-417e-90fc-e9fe19f0a8fa
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# XML IntelliSense in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

L'éditeur de Code Visual Basic inclut des fonctionnalités IntelliSense pour XML qui offrent une saisie semi\-automatique de mots pour les éléments définis dans un schéma XML.  Si vous incluez un fichier XSD \(XML Schema Definition\) dans votre projet et importez l'espace de noms cible du schéma en utilisant l'instruction `Imports`, l'éditeur de code inclura des éléments du schéma XSD dans la liste des variables membre valides IntelliSense pour les objets <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XDocument>.  L'illustration suivante présente la liste de membres IntelliSense pour un objet <xref:System.Xml.Linq.XElement>.  
  
 ![XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/media/xml-intellisense.png "XML\_Intellisense")  
XML IntelliSense  
  
## Activation de XML IntelliSense dans Visual Basic  
 Pour activer XML IntelliSense dans Visual Basic, vous devez inclure un fichier de schéma XSD dans votre projet Visual Basic.  Vous devez également importer l'espace de noms cible pour l'espace de noms du schéma XSD dans votre fichier de code en utilisant l'instruction `Imports`.  Vous pouvez également ajouter l'espace de noms cible à la liste d'espaces de noms de niveau de projet en utilisant la page **Références** du concepteur de projets Visual Basic.  Pour obtenir des exemples, consultez [How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).  Pour plus d'informations, consultez [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) et [Page Références, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic).  
  
 Notez que par défaut, vous ne pouvez pas afficher de fichiers de schéma XSD dans les projets Visual Basic.  Vous devrez peut\-être cliquer sur le bouton **Afficher tous les fichiers** pour sélectionner un fichier XSD à inclure dans votre projet.  
  
### Création d'un fichier de schéma \(Inférence de schéma\)  
 Vous pouvez créer un schéma XSD pour un fichier XML existant en déduisant le schéma XSD à l'aide d'outils XML Visual Studio.  
  
-   À partir du SP1, vous pouvez utiliser l'Assistant Schéma XML vers pour créer un jeu de schémas XML qui est déduit d'un ou de plusieurs documents XML et l'inclut dans votre projet.  Vous pouvez utiliser toute combinaison de documents XML sous forme de fichiers texte, de flux XML disponibles via une adresse Internet HTTP ou de code XML tapé ou collé dans l'Assistant Schéma XML vers.  Pour accéder à l'Assistant Schéma XML vers, cliquez sur **Ajouter un nouvel élément** dans le menu **Projet** et ajoutez un modèle **Schéma XML vers** à partir du groupe de modèles **Données** ou **Éléments communs**.  Après avoir inclus toutes les sources de document XML à partir desquelles déduire le jeu de schémas XML, cliquez sur **OK** pour créer le jeu de schémas déduit.  Pour plus d'informations, consultez [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md).  
  
-   Vous pouvez également utiliser l'Éditeur XML de Visual Studio pour déduire un jeu de schémas XSD à partir d'un fichier XML.  Pour créer un jeu de schémas XML à l'aide de l'Éditeur XML, ouvrez le fichier XML dans le Concepteur XML de Visual Studio, puis cliquez sur **Créer un schéma** dans le menu **XML**.  Après avoir créé le jeu de schémas XSD, vous pouvez l'enregistrer dans un ou plusieurs fichiers XSD et inclure ces derniers dans votre projet.  Pour plus d'informations, consultez [How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).  
  
 Notez que les différents jeux de schémas XSD peuvent être déduits à partir de plusieurs documents XML conçus pour avoir le même schéma.  Cela peut se produire lorsque des éléments et attributs particuliers sont présents dans un fichier XML et pas dans un autre ou lorsque les éléments sont inclus dans un ordre différent, par exemple.  Vous devez passer en revue les jeux de schémas XSD déduits par souci d'exhaustivité et d'exactitude lorsque vous utilisez l'inférence de schéma XSD.  
  
## Liste des membres  
 Après avoir tapé un point \(.\) pour délimiter une instance d'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> \(ou une instance de `IEnumerable(Of XElement)` ou `IEnumerable(Of XDocument)`\), Visual Basic IntelliSense affiche une liste des membres d'objet possibles.  La liste initiale inclut trois options qui représentent des propriétés d'axe XML, comme décrit dans la liste suivante.  
  
|||  
|-|-|  
|Option|Description|  
|**\< \>**|Sélectionnez cette option pour afficher une liste d'éléments enfants possibles.  Pour plus d'informations, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et la méthode <xref:System.Xml.Linq.XContainer.Elements%2A>.|  
|**@**|Sélectionnez cette option pour afficher une liste d'attributs possibles.  Pour plus d'informations, consultez [XML Axis Properties](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md). Cette option est uniquement disponible pour les objets de type <xref:System.Xml.Linq.XElement>.|  
|**…\< \>**|Sélectionnez cette option pour afficher une liste d'éléments descendants.  Pour plus d'informations, consultez [How to: Access XML Descendant Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) et la méthode <xref:System.Xml.Linq.XContainer.Elements%2A>.|  
  
 Sélectionnez ou commencez à taper une des options XML de la liste.  La liste des membres affichera ensuite les membres potentiels du schéma XML qui sont spécifiques à l'option sélectionnée.  Si vous avez des espaces de noms XML importés associés à un préfixe d'espace de noms XML spécifique, une liste de préfixes d'espace de noms XML potentiels est incluse dans la liste des membres.  
  
 Considérons, par exemple, le schéma XSD suivant.  
  
```  
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
  
 Le XML valide pour le schéma XSD ressemblerait à ce qui suit.  
  
```  
<?xml version="1.0"?>  
<PurchaseOrders xmlns="http://SamplePurchaseOrder">  
  <PurchaseOrder PurchaseOrderNumber="12345" OrderDate="2000-1-1">  
    <Address />  
    <Items />  
    <Comment />  
  </PurchaseOrder>  
</PurchaseOrders>  
```  
  
 Si vous incluez ce fichier de schéma XSD dans un projet et importez l'espace de noms cible du schéma XSD dans votre fichier de code ou projet, Visual Basic IntelliSense affiche les membres du schéma à mesure que vous tapez votre code Visual Basic.  Si l'espace de noms cible pour le schéma XSD est importé comme espace de noms par défaut et que vous tapez les éléments suivants, IntelliSense affiche une liste d'éléments enfants possibles pour l'élément XML `PurchaseOrder`.  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 La liste se compose des éléments Adresse, Commentaire et Éléments.  
  
### Niveaux de certitude pour les éléments de liste IntelliSense  
 La détermination du type XSD à utiliser pour IntelliSense n'est pas exacte.  En conséquence, XML IntelliSense affichera souvent une liste développée de membres possibles.  Pour vous aider pour sélectionner un élément dans la liste des membres d'IntelliSense, les éléments sont affichés avec une indication du niveau de certitude qu'XML IntelliSense propose pour un membre particulier.  
  
 Quelquefois XML IntelliSense peut identifier un type spécifique à partir du schéma XSD.  Dans ces cas, il affichera des éléments enfants, des attributs ou des éléments descendants possibles pour ce type XSD avec un degré élevé de certitude.  Ces éléments sont identifiés par une coche.  
  
 Toutefois, XML IntelliSense n'est pas en mesure d'identifier un type spécifique à partir du schéma XSD.  Dans ces cas, il affichera une liste développée des éléments enfants, des attributs ou des éléments descendants possibles du schéma XSD pour le projet avec un faible degré de certitude.  Ces éléments sont identifiés par un point d'interrogation.  
  
## Voir aussi  
 [How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)   
 [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)   
 [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)   
 [XML Descendant Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [Page Références, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)