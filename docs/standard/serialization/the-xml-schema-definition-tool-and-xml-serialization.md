---
title: "Outil XML Schema Definition et sérialisation XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
caps.latest.revision: 7
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: c72269708526479d0e98cdfd694db57fe0d9e35e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a>Outil XML Schema Definition et sérialisation XML
L’outil de définition de schéma XML, [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md), est installé avec les outils .NET Framework lors de l’installation du Kit de développement logiciel (SDK) Windows®. L’outil a deux principaux objectifs :  
  
-   Générer des fichiers de classe C# ou Visual Basic qui se conforment à un schéma de langage XSD (XML Schema definition) spécifique. L'outil considère un schéma XML comme un argument et génère un fichier qui contient plusieurs classes qui, lorsqu'elles sont sérialisées avec <xref:System.Xml.Serialization.XmlSerializer>, se conforment au schéma. Pour plus d’informations sur l’utilisation de l’outil pour générer des classes qui se conforment à un schéma spécifique, consultez [Guide pratique pour utiliser l’outil XML Schema Definition pour la génération de classes et de documents de schéma XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).  
  
-   Générer un document de schéma XML à partir d’un fichier .dll ou .exe. Pour consulter le schéma d’un ensemble de fichiers que vous avez créé ou d’un ensemble qui a été modifié avec des attributs, passez le fichier DLL ou EXE comme argument à l’outil pour générer le schéma XML. Pour plus d’informations sur l’utilisation de l’outil pour générer un document de schéma XML à partir d’un ensemble de classes, consultez [Guide pratique pour utiliser l’outil XML Schema Definition pour la génération de classes et de documents de schéma XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).  
  
 Pour plus d’informations sur cet outil et d’autres outils, consultez [Outils](../../../docs/framework/tools/index.md). Pour plus d’informations sur les options de l’outil, consultez [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataSet>   
 [Introduction à la sérialisation XML](../../../docs/standard/serialization/introducing-xml-serialization.md)   
 [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)   
 <xref:System.Xml.Serialization.XmlSerializer>   
 [Guide pratique pour sérialiser un objet](../../../docs/standard/serialization/how-to-serialize-an-object.md)   
 [Guide pratique pour désérialiser un objet](../../../docs/standard/serialization/how-to-deserialize-an-object.md)   
 [Guide pratique pour utiliser l’outil XML Schema Definition pour la génération de classes et de documents de schéma XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)   
 [Prise en charge de la liaison de schéma XML dans .NET Framework](http://msdn.microsoft.com/en-us/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)

