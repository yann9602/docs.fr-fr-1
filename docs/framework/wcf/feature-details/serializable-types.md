---
title: "Types sérialisables"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e368472db3bdca73661586821106174e13d4d24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="serializable-types"></a><span data-ttu-id="6d3cf-102">Types sérialisables</span><span class="sxs-lookup"><span data-stu-id="6d3cf-102">Serializable Types</span></span>
<span data-ttu-id="6d3cf-103">Par défaut, <xref:System.Runtime.Serialization.DataContractSerializer> sérialise tous les types accessibles publiquement.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-103">By default, the <xref:System.Runtime.Serialization.DataContractSerializer> serializes all publicly visible types.</span></span> <span data-ttu-id="6d3cf-104">Toutes les propriétés et tous les champs publics en lecture/écriture du type sont sérialisés.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-104">All public read/write properties and fields of the type are serialized.</span></span>  
  
 <span data-ttu-id="6d3cf-105">Vous pouvez modifier le comportement par défaut en appliquant les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> aux types et membres. Cette fonctionnalité peut être utile dans les situations dans lesquelles vous avez des types qui ne sont pas sous votre contrôle et ne peuvent pas être modifiés pour ajouter des attributs.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-105">You can change the default behavior by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the types and members This feature can be useful in situations in which you have types that are not under your control and cannot be modified to add attributes.</span></span> <span data-ttu-id="6d3cf-106">Le <xref:System.Runtime.Serialization.DataContractSerializer> reconnaît ces types "non marqués".</span><span class="sxs-lookup"><span data-stu-id="6d3cf-106">The <xref:System.Runtime.Serialization.DataContractSerializer> recognizes such "unmarked" types.</span></span>  
  
## <a name="serialization-defaults"></a><span data-ttu-id="6d3cf-107">Valeurs par défaut de sérialisation</span><span class="sxs-lookup"><span data-stu-id="6d3cf-107">Serialization Defaults</span></span>  
 <span data-ttu-id="6d3cf-108">Vous pouvez appliquer les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> pour contrôler explicitement ou personnaliser la sérialisation de types et membres.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-108">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to explicitly control or customize the serialization of types and members.</span></span> <span data-ttu-id="6d3cf-109">De plus, vous pouvez appliquer ces attributs aux champs privés.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-109">In addition, you can apply these attributes to private fields.</span></span> <span data-ttu-id="6d3cf-110">Toutefois, même les types qui ne sont pas marqués avec ces attributs sont sérialisés et désérialisés.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-110">However, even types that are not marked with these attributes are serialized and deserialized.</span></span> <span data-ttu-id="6d3cf-111">Les règles et les exceptions suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="6d3cf-111">The following rules and exceptions apply:</span></span>  
  
-   <span data-ttu-id="6d3cf-112">Le <xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données à partir des types sans attributs à l'aide des propriétés par défaut des types créés récemment.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-112">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract from types without attributes using the default properties of the newly created types.</span></span>  
  
-   <span data-ttu-id="6d3cf-113">Tous les champs publics et les propriétés avec les méthodes `get` et `set` publiques sont sérialisées, à moins que vous n'appliquiez l'attribut <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> à ce membre.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-113">All public fields, and properties with public `get` and `set` methods are serialized, unless you apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
-   <span data-ttu-id="6d3cf-114">La sémantique de sérialisation est similaire à celle du <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-114">The serialization semantics are similar to those of the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
-   <span data-ttu-id="6d3cf-115">Dans les types non marqués, seuls les types publics avec les constructeurs qui n'ont pas de paramètres sont sérialisés.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-115">In unmarked types, only public types with constructors that do not have parameters are serialized.</span></span> <span data-ttu-id="6d3cf-116">L'exception à cette règle est l'<xref:System.Runtime.Serialization.ExtensionDataObject> utilisé avec l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject>.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-116">The exception to this rule is <xref:System.Runtime.Serialization.ExtensionDataObject> used with the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
-   <span data-ttu-id="6d3cf-117">Les champs en lecture seule, les propriétés sans méthode `get` ou `set` et les propriétés avec des méthodes `set` ou `get` internes ou privées ne sont pas sérialisés.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-117">Read-only fields, properties without a `get` or `set` method, and properties with internal or private `set` or `get` methods are not serialized.</span></span> <span data-ttu-id="6d3cf-118">Ces propriétés sont ignorées et aucune exception n'est levée, sauf dans le cas des collections get-only.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-118">Such properties are ignored and no exception is thrown, except in the case of get-only collections.</span></span>  
  
-   <span data-ttu-id="6d3cf-119">Les attributs <xref:System.Xml.Serialization.XmlSerializer> (tels que  `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, etc.) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-119"><xref:System.Xml.Serialization.XmlSerializer> attributes (such as `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, and so on) are ignored.</span></span>  
  
-   <span data-ttu-id="6d3cf-120">Si vous n'appliquez pas l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à un type donné, le sérialiseur ignore tout membre dans ce type auquel l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> est appliqué.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-120">If you do not apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a given type, the serializer ignores any member in that type to which the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute is applied.</span></span>  
  
-   <span data-ttu-id="6d3cf-121">La propriété <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> est prise en charge dans les types non marqués avec l'attribut <xref:System.Runtime.Serialization.DataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-121">The <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> property is supported in types not marked with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute.</span></span> <span data-ttu-id="6d3cf-122">Cela inclut la prise en charge de l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute> sur les types non marqués.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-122">This includes support for the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on unmarked types.</span></span>  
  
-   <span data-ttu-id="6d3cf-123">Pour annuler le processus de sérialisation des membres publics, des propriétés ou des champs, appliquez l'attribut <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> à ce membre.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-123">To "opt out" of the serialization process for public members, properties, or fields, apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="6d3cf-124">Héritage</span><span class="sxs-lookup"><span data-stu-id="6d3cf-124">Inheritance</span></span>  
 <span data-ttu-id="6d3cf-125">Les types non marqués (type sans attribut <xref:System.Runtime.Serialization.DataContractAttribute>) peuvent hériter des types qui ont cet attribut. Toutefois, l'inverse n'est pas permis : les types avec l'attribut ne peuvent pas hériter de types non marqués.</span><span class="sxs-lookup"><span data-stu-id="6d3cf-125">Unmarked types (types without the <xref:System.Runtime.Serialization.DataContractAttribute> attribute) can inherit from types that do have this attribute; however, the reverse is not permitted: types with the attribute cannot inherit from unmarked types.</span></span> <span data-ttu-id="6d3cf-126">Cette règle est appliquée principalement pour garantir la compatibilité descendante avec le code écrit dans les versions antérieures de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d3cf-126">This rule is enforced primarily to ensure backward compatibility with code written in earlier versions of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3cf-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d3cf-127">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="6d3cf-128">Types pris en charge par le sérialiseur de contrat de données</span><span class="sxs-lookup"><span data-stu-id="6d3cf-128">Types Supported by the Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
