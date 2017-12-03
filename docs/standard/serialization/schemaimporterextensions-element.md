---
title: "Élément &lt;schemaImporterExtensions&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0296b207af0ed439c90374eb6db21fe11e00dd42
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="d1c9c-102">Élément &lt;schemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="d1c9c-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="d1c9c-103">Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1c9c-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="d1c9c-104">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1c9c-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c9c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1c9c-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="d1c9c-106">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d1c9c-106">Child Elements</span></span>  
  
|<span data-ttu-id="d1c9c-107">Élément</span><span class="sxs-lookup"><span data-stu-id="d1c9c-107">Element</span></span>|<span data-ttu-id="d1c9c-108">Description</span><span class="sxs-lookup"><span data-stu-id="d1c9c-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1c9c-109">\<add>, élément pour \<xmlSchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d1c9c-109">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|<span data-ttu-id="d1c9c-110">Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour créer des mappages.</span><span class="sxs-lookup"><span data-stu-id="d1c9c-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="d1c9c-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d1c9c-111">Parent Elements</span></span>  
  
|<span data-ttu-id="d1c9c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="d1c9c-112">Element</span></span>|<span data-ttu-id="d1c9c-113">Description</span><span class="sxs-lookup"><span data-stu-id="d1c9c-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1c9c-114">\<system.xml.serialization>, élément</span><span class="sxs-lookup"><span data-stu-id="d1c9c-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="d1c9c-115">Élément de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="d1c9c-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d1c9c-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1c9c-116">Example</span></span>  
 <span data-ttu-id="d1c9c-117">L'exemple de code suivant illustre comment ajouter des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1c9c-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1c9c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1c9c-118">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="d1c9c-119">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d1c9c-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d1c9c-120">\<dateTimeSerialization>, élément</span><span class="sxs-lookup"><span data-stu-id="d1c9c-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="d1c9c-121">\<add>, élément pour \<xmlSchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d1c9c-121">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="d1c9c-122">\<system.xml.serialization>, élément</span><span class="sxs-lookup"><span data-stu-id="d1c9c-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
