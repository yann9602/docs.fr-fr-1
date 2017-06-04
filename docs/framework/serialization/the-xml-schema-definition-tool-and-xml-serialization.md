---
title: "Outil&#160;XML Schema Definition et s&#233;rialisation&#160;XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Xsd.exe"
  - "sérialisation XML, outil XML Schema Definition"
  - "Outil XML Schema Definition"
  - "sérialisation, outil XML Schema Definition"
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Outil&#160;XML Schema Definition et s&#233;rialisation&#160;XML
L’outil XML Schema Definition \([Outil XML Schema Definition \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md)\) est installé avec les outils .NET Framework lors de l’installation du Kit de développement logiciel Windows® \(SDK\). L’outil a deux principaux objectifs :  
  
-   Générer des fichiers de classe C\# ou Visual Basic conformes à un schéma de langage XSD \(XML Schema Definition\) spécifique. L’outil prend un schéma XML comme argument et génère un fichier qui contient plusieurs classes qui, lorsqu’elles sont sérialisées avec [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx), se conforment au schéma. Pour plus d’informations sur la façon d’utiliser l’outil pour générer des classes qui se conforment à un schéma spécifique, consultez [Comment : utiliser l'outil XML Schema Definition pour générer des classes et des documents de schéma XML](../../../docs/framework/serialization/xml-schema-def-tool-gen.md).  
  
-   Générer un document de schéma XML à partir d’un fichier .dll ou .exe. Pour consulter le schéma d’un ensemble de fichiers que vous avez créé ou d’un ensemble qui a été modifié avec des attributs, passez le fichier DLL ou EXE comme argument à l’outil pour générer le schéma XML. Pour plus d’informations sur la façon d’utiliser l’outil pour générer un document de schéma XML à partir d’un ensemble de classes, consultez [Comment : utiliser l'outil XML Schema Definition pour générer des classes et des documents de schéma XML](../../../docs/framework/serialization/xml-schema-def-tool-gen.md).  
  
 Pour plus d’informations sur cet outil et d’autres outils, consultez [Tools](../../../docs/framework/tools/index.md). Pour plus d’informations sur les options de l’outil, consultez [Outil XML Schema Definition \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
## Voir aussi  
 [Introduction à la sérialisation XML](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [DataSet](frlrfSystemDataDataSetClassTopic)   
 [Outil XML Schema Definition \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [Comment : sérialiser un objet](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [Comment : désérialiser un objet](../../../docs/framework/serialization/how-to-deserialize-an-object.md)   
 [Comment : utiliser l'outil XML Schema Definition pour générer des classes et des documents de schéma XML](../../../docs/framework/serialization/xml-schema-def-tool-gen.md)   
 [Prise en charge de la liaison de schéma XML dans .NET Framework](http://msdn.microsoft.com/fr-fr/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)