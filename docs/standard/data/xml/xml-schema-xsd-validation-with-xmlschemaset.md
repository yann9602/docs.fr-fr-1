---
title: "Validation de sch&#233;ma XML (XSD) avec XmlSchemaSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Validation de sch&#233;ma XML (XSD) avec XmlSchemaSet
Les documents XML peuvent être validés par rapport à un schéma XSD \(XML Schema Definition\) dans un objet <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## Validation de documents XML  
 Les documents XML sont validés par la méthode <xref:System.Xml.XmlReader.Create%2A> de la classe <xref:System.Xml.XmlReader>.  Pour valider un document XML, vous construisez un objet <xref:System.Xml.XmlReaderSettings> qui contient un schéma de langage XSD \(XML Schema Definition\) permettant de valider le document XML.  
  
> [!NOTE]
>  L'espace de noms <xref:System.Xml.Schema> contient des méthodes d'extension qui facilitent la validation d'une arborescence XML par rapport à un fichier XSD lors de l'utilisation de [LINQ to XML](../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  Pour plus d'informations sur la validation de documents XML avec LINQ to XML, voir [Procédure : valider à l'aide de XSD](../Topic/How%20to:%20Validate%20Using%20XSD%20\(LINQ%20to%20XML\).md).  
  
 Vous pouvez ajouter un schéma individuel ou un jeu de schémas \(sous forme de <xref:System.Xml.Schema.XmlSchemaSet>\) à un <xref:System.Xml.Schema.XmlSchemaSet> en le passant en tant que paramètre à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de <xref:System.Xml.Schema.XmlSchemaSet>.  Notez que lorsque vous validez un document, son espace de noms cible doit correspondre à celui de l'espace de noms cible du jeu de schémas.  
  
 Voici un exemple de document XML.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Voici le schéma qui valide l'exemple de document XML.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 Dans l'exemple de code suivant, le schéma ci\-dessus est ajouté à la propriété <xref:System.Xml.XmlReaderSettings.Schemas%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> de l'objet <xref:System.Xml.XmlReaderSettings>.  L'objet <xref:System.Xml.XmlReaderSettings> est passé sous forme de paramètre à la méthode <xref:System.Xml.XmlReader.Create%2A> de l'objet <xref:System.Xml.XmlReader> qui valide le document XML ci\-dessus.  
  
 La propriété <xref:System.Xml.XmlReaderSettings.ValidationType%2A> de l'objet <xref:System.Xml.XmlReaderSettings> est définie sur `Schema` pour effectuer la validation du document XML par la méthode <xref:System.Xml.XmlReader.Create%2A> de l'objet <xref:System.Xml.XmlReader>.  Un objet <xref:System.Xml.Schema.ValidationEventHandler> est ajouté à l'objet <xref:System.Xml.XmlReaderSettings> pour gérer tous les événements <xref:System.Xml.Schema.XmlSeverityType> ou <xref:System.Xml.Schema.XmlSeverityType> déclenchés par des erreurs trouvées lors du processus de validation du document et du schéma XML.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## Voir aussi  
 [XmlSchemaSet pour la compilation de schémas](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)   
 [Utilisation de schémas XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)