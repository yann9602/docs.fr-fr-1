---
title: "Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 052996bedcb10494cb2fee1ccf3ba7b5a083356b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="c73c5-102">Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="c73c5-102">Attributes That Control Encoded SOAP Serialization</span></span> 
<span data-ttu-id="c73c5-103">Le document World Wide Web Consortium (www.w3.org) intitulé « Simple Object Access Protocol (SOAP) 1.1 » contient une section facultative (section 5) qui décrit comment les paramètres SOAP peuvent être encodés.</span><span class="sxs-lookup"><span data-stu-id="c73c5-103">The World Wide Web Consortium (www.w3.org) document named "Simple Object Access Protocol (SOAP) 1.1" contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="c73c5-104">Pour se conformer à la section 5 de la spécification, vous devez utiliser un ensemble spécial d’attributs figurant dans l’espace de noms <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="c73c5-104">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="c73c5-105">Appliquez ces attributs en fonction des classes et membres de classes, puis utilisez <xref:System.Xml.Serialization.XmlSerializer> pour sérialiser les instances de la ou des classes.</span><span class="sxs-lookup"><span data-stu-id="c73c5-105">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>  
  
 <span data-ttu-id="c73c5-106">Le tableau suivant affiche les attributs, leurs conditions d'application et l'action qu'ils entraînent.</span><span class="sxs-lookup"><span data-stu-id="c73c5-106">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="c73c5-107">Pour plus d’informations sur l’utilisation de ces attributs pour contrôler la sérialisation XML, consultez [Guide pratique pour sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) et [Guide pratique pour remplacer la sérialisation XML encodée selon le protocole SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="c73c5-107">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span></span>  
  
 <span data-ttu-id="c73c5-108">Pour plus d’informations sur les attributs, consultez [Attributs](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="c73c5-108">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span>  
  
|<span data-ttu-id="c73c5-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c73c5-109">Attribute</span></span>|<span data-ttu-id="c73c5-110">S'applique à</span><span class="sxs-lookup"><span data-stu-id="c73c5-110">Applies to</span></span>|<span data-ttu-id="c73c5-111">Informations fournies</span><span class="sxs-lookup"><span data-stu-id="c73c5-111">Specifies</span></span>|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="c73c5-112">Champ public, propriété, paramètre ou valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="c73c5-112">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="c73c5-113">Le membre de classe est sérialisé en tant qu'attribut XML.</span><span class="sxs-lookup"><span data-stu-id="c73c5-113">The class member will be serialized as an XML attribute.</span></span>|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="c73c5-114">Champ public, propriété, paramètre ou valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="c73c5-114">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="c73c5-115">La classe est sérialisée en tant qu'élément XML.</span><span class="sxs-lookup"><span data-stu-id="c73c5-115">The class will be serialized as an XML element.</span></span>|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="c73c5-116">Champ public qui est un identificateur d'énumération.</span><span class="sxs-lookup"><span data-stu-id="c73c5-116">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="c73c5-117">Nom d'élément d'un membre d'énumération.</span><span class="sxs-lookup"><span data-stu-id="c73c5-117">The element name of an enumeration member.</span></span>|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="c73c5-118">Champs et propriétés publics.</span><span class="sxs-lookup"><span data-stu-id="c73c5-118">Public properties and fields.</span></span>|<span data-ttu-id="c73c5-119">La propriété ou le champ doit être ignoré lorsque la classe conteneur est sérialisée.</span><span class="sxs-lookup"><span data-stu-id="c73c5-119">The property or field should be ignored when the containing class is serialized.</span></span>|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="c73c5-120">Déclarations de classe dérivée publiques et méthodes publiques pour les documents WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="c73c5-120">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="c73c5-121">Le type doit être inclus lors de la génération de schémas (afin d'être reconnu en cas de sérialisation).</span><span class="sxs-lookup"><span data-stu-id="c73c5-121">The type should be included when generating schemas (to be recognized when serialized).</span></span>|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="c73c5-122">Déclarations de classe publiques.</span><span class="sxs-lookup"><span data-stu-id="c73c5-122">Public class declarations.</span></span>|<span data-ttu-id="c73c5-123">La classe doit être sérialisée en tant que type XML.</span><span class="sxs-lookup"><span data-stu-id="c73c5-123">The class should be serialized as an XML type.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c73c5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c73c5-124">See Also</span></span>  
 [<span data-ttu-id="c73c5-125">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="c73c5-125">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="c73c5-126">Guide pratique pour sérialiser un objet en tant que flux XML encodé selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="c73c5-126">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [<span data-ttu-id="c73c5-127">Guide pratique pour remplacer la sérialisation XML encodée selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="c73c5-127">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [<span data-ttu-id="c73c5-128">Attributs</span><span class="sxs-lookup"><span data-stu-id="c73c5-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="c73c5-129">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="c73c5-129">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="c73c5-130">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="c73c5-130">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
