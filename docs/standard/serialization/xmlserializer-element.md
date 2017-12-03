---
title: "Élément &lt;xmlSerializer&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17e4fcd1b471a5197f2e6a30bad10cbdbe22f216
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltxmlserializergt-element"></a><span data-ttu-id="083d7-102">Élément &lt;xmlSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="083d7-102">&lt;xmlSerializer&gt; Element</span></span>
<span data-ttu-id="083d7-103">Spécifie si un contrôle supplémentaire de la progression de <xref:System.Xml.Serialization.XmlSerializer> est effectué.</span><span class="sxs-lookup"><span data-stu-id="083d7-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="083d7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="083d7-104">\<configuration></span></span>  
<span data-ttu-id="083d7-105">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="083d7-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="083d7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="083d7-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="083d7-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="083d7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="083d7-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="083d7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="083d7-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="083d7-109">Attributes</span></span>  
  
|<span data-ttu-id="083d7-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="083d7-110">Attribute</span></span>|<span data-ttu-id="083d7-111">Description</span><span class="sxs-lookup"><span data-stu-id="083d7-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="083d7-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="083d7-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="083d7-113">Spécifie si la progression de <xref:System.Xml.Serialization.XmlSerializer> est vérifiée.</span><span class="sxs-lookup"><span data-stu-id="083d7-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="083d7-114">Affectez "true" ou "false" à l'attribut.</span><span class="sxs-lookup"><span data-stu-id="083d7-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="083d7-115">La valeur par défaut est "true".</span><span class="sxs-lookup"><span data-stu-id="083d7-115">The default is "true".</span></span>|  
|<span data-ttu-id="083d7-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="083d7-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="083d7-117">Spécifie si <xref:System.Xml.Serialization.XmlSerializer> utilise la génération de sérialisation héritée qui génère des assemblys en écrivant le code C# dans un fichier, puis en le compilant dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="083d7-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="083d7-118">La valeur par défaut est **false**.</span><span class="sxs-lookup"><span data-stu-id="083d7-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="083d7-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="083d7-119">Child Elements</span></span>  
 <span data-ttu-id="083d7-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="083d7-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="083d7-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="083d7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="083d7-122">Élément</span><span class="sxs-lookup"><span data-stu-id="083d7-122">Element</span></span>|<span data-ttu-id="083d7-123">Description</span><span class="sxs-lookup"><span data-stu-id="083d7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="083d7-124">\<system.xml.serialization>, élément</span><span class="sxs-lookup"><span data-stu-id="083d7-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="083d7-125">Contient des paramètres de configuration pour les classes <xref:System.Xml.Serialization.XmlSerializer> et <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="083d7-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="083d7-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="083d7-126">Remarks</span></span>  
 <span data-ttu-id="083d7-127">Par défaut, le <xref:System.Xml.Serialization.XmlSerializer> fournit une couche supplémentaire de sécurité contre des attaques par déni de service potentielles lors de la désérialisation de données non fiables.</span><span class="sxs-lookup"><span data-stu-id="083d7-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="083d7-128">Pour ce faire, il tente de détecter des boucles infinies pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="083d7-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="083d7-129">Si une telle condition est détectée, une exception est levée avec le message suivant : « Erreur interne : la désérialisation n’a pas pu avancer sur le flux de données sous-jacent. ».</span><span class="sxs-lookup"><span data-stu-id="083d7-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="083d7-130">Le fait de recevoir ce message n'indique pas nécessairement qu'une attaque par déni de service est en cours.</span><span class="sxs-lookup"><span data-stu-id="083d7-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="083d7-131">Dans de rares circonstances, le mécanisme de détection de boucles infinies génère un faux positif et l'exception est levée pour un message entrant légitime.</span><span class="sxs-lookup"><span data-stu-id="083d7-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="083d7-132">Si vous voyez, dans votre application, que des messages légitimes sont rejetés par cette couche de protection supplémentaire, définissez l’attribut **checkDeserializeAdvances** sur la valeur false.</span><span class="sxs-lookup"><span data-stu-id="083d7-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="083d7-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="083d7-133">Example</span></span>  
 <span data-ttu-id="083d7-134">L’exemple de code suivant assigne la valeur false à l’attribut **checkDeserializeAdvances**.</span><span class="sxs-lookup"><span data-stu-id="083d7-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="083d7-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="083d7-135">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="083d7-136">\<system.xml.serialization>, élément</span><span class="sxs-lookup"><span data-stu-id="083d7-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="083d7-137">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="083d7-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
