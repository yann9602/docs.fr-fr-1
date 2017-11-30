---
title: "Outil XML Schema Definition et sérialisation XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b943251ff426d5557c4715a856ffdadd3013b9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="fefd9-102">Outil XML Schema Definition et sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="fefd9-102">The XML Schema Definition Tool and XML Serialization</span></span>
<span data-ttu-id="fefd9-103">L’outil de définition de schéma XML, [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md), est installé avec les outils .NET Framework lors de l’installation du Kit de développement logiciel (SDK) Windows®.</span><span class="sxs-lookup"><span data-stu-id="fefd9-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows® Software Development Kit (SDK).</span></span> <span data-ttu-id="fefd9-104">L’outil a deux principaux objectifs :</span><span class="sxs-lookup"><span data-stu-id="fefd9-104">The tool is designed primarily for two purposes:</span></span>  
  
-   <span data-ttu-id="fefd9-105">Générer des fichiers de classe C# ou Visual Basic qui se conforment à un schéma de langage XSD (XML Schema definition) spécifique.</span><span class="sxs-lookup"><span data-stu-id="fefd9-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="fefd9-106">L'outil considère un schéma XML comme un argument et génère un fichier qui contient plusieurs classes qui, lorsqu'elles sont sérialisées avec <xref:System.Xml.Serialization.XmlSerializer>, se conforment au schéma.</span><span class="sxs-lookup"><span data-stu-id="fefd9-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="fefd9-107">Pour plus d’informations sur l’utilisation de l’outil pour générer des classes qui se conforment à un schéma spécifique, consultez [Guide pratique pour utiliser l’outil XML Schema Definition pour la génération de classes et de documents de schéma XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="fefd9-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
-   <span data-ttu-id="fefd9-108">Générer un document de schéma XML à partir d’un fichier .dll ou .exe.</span><span class="sxs-lookup"><span data-stu-id="fefd9-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="fefd9-109">Pour consulter le schéma d’un ensemble de fichiers que vous avez créé ou d’un ensemble qui a été modifié avec des attributs, passez le fichier DLL ou EXE comme argument à l’outil pour générer le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="fefd9-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="fefd9-110">Pour plus d’informations sur l’utilisation de l’outil pour générer un document de schéma XML à partir d’un ensemble de classes, consultez [Guide pratique pour utiliser l’outil XML Schema Definition pour la génération de classes et de documents de schéma XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="fefd9-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
 <span data-ttu-id="fefd9-111">Pour plus d’informations sur cet outil et d’autres outils, consultez [Outils](../../../docs/framework/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="fefd9-111">For more information about this tool and others, see [Tools](../../../docs/framework/tools/index.md).</span></span> <span data-ttu-id="fefd9-112">Pour plus d’informations sur les options de l’outil, consultez [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fefd9-112">For information about the tool's options, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fefd9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fefd9-113">See Also</span></span>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="fefd9-114">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="fefd9-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="fefd9-115">Outil XML Schema Definition (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="fefd9-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="fefd9-116">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="fefd9-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="fefd9-117">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="fefd9-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="fefd9-118">Guide pratique pour utiliser l’outil XML Schema Definition pour la génération de classes et de documents de schéma XML</span><span class="sxs-lookup"><span data-stu-id="fefd9-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)  
 [<span data-ttu-id="fefd9-119">Prise en charge de la liaison de schéma XML dans .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fefd9-119">XML Schema Binding Support in the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)
