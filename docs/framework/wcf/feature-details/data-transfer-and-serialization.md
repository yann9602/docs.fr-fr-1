---
title: "Transfert de données et sérialisation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8daadec1eef20e62747cdbfcafd1fd13cfc16093
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="4f75d-102">Transfert de données et sérialisation</span><span class="sxs-lookup"><span data-stu-id="4f75d-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="4f75d-103">Dans un système connecté, les services et les clients se reposent sur l’échange de données pour accomplir une tâche.</span><span class="sxs-lookup"><span data-stu-id="4f75d-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="4f75d-104">En tant que développeur d'un service ou d'un client, vous devez aussi comprendre comment [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] gère les données et la sérialisation des données pour créer des applications qui sont efficaces et d'une maintenance simple.</span><span class="sxs-lookup"><span data-stu-id="4f75d-104">As a developer of a service or client, you must also understand how [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f75d-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4f75d-105">In This Section</span></span>  
 [<span data-ttu-id="4f75d-106">Spécification du transfert de données dans des contrats de service</span><span class="sxs-lookup"><span data-stu-id="4f75d-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="4f75d-107">Décrit les concepts de base du transfert de données dans les services.</span><span class="sxs-lookup"><span data-stu-id="4f75d-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="4f75d-108">Utilisation de contrats de données</span><span class="sxs-lookup"><span data-stu-id="4f75d-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="4f75d-109">Définit les contrats de données et la méthode utilisée pour les créer et les utiliser.</span><span class="sxs-lookup"><span data-stu-id="4f75d-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="4f75d-110">Sérialiseur de contrat de données</span><span class="sxs-lookup"><span data-stu-id="4f75d-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="4f75d-111">Décrit comment accomplir la sérialisation des données avec la classe <xref:System.Runtime.Serialization.DataContractSerializer> ou une extension de la classe <xref:System.Runtime.Serialization.XmlObjectSerializer>.</span><span class="sxs-lookup"><span data-stu-id="4f75d-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="4f75d-112">Utilisation de la classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="4f75d-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="4f75d-113">Décrit comment et pourquoi utiliser la classe <xref:System.Xml.Serialization.XmlSerializer>, une alternative à la classe <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="4f75d-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="4f75d-114">Utilisation de contrats de message</span><span class="sxs-lookup"><span data-stu-id="4f75d-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="4f75d-115">Décrit comment les contrats de message autorisent un contrôle pointu sur les messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="4f75d-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="4f75d-116">Utilisation de la classe de message</span><span class="sxs-lookup"><span data-stu-id="4f75d-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="4f75d-117">Décrit comment utiliser les fonctionnalités de la classe Message.</span><span class="sxs-lookup"><span data-stu-id="4f75d-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="4f75d-118">Filtrage</span><span class="sxs-lookup"><span data-stu-id="4f75d-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="4f75d-119">Décrit le filtrage qui permet le pré-traitement d'un message selon différents critères.</span><span class="sxs-lookup"><span data-stu-id="4f75d-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="4f75d-120">Données volumineuses et streaming</span><span class="sxs-lookup"><span data-stu-id="4f75d-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="4f75d-121">Décrit comment envoyer un grand bloc de données, tel qu'un fichier binaire.</span><span class="sxs-lookup"><span data-stu-id="4f75d-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="4f75d-122">Considérations sur la sécurité des données</span><span class="sxs-lookup"><span data-stu-id="4f75d-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="4f75d-123">Décrit des éléments à connaître lors de la programmation du transfert de données et de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="4f75d-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="4f75d-124">Vue d’ensemble de l’architecture de transfert de données</span><span class="sxs-lookup"><span data-stu-id="4f75d-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="4f75d-125">Décrit une présentation de la conception totale du transfert de données dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f75d-125">Describes a view of the overall design of data transfer in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4f75d-126">Référence</span><span class="sxs-lookup"><span data-stu-id="4f75d-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="4f75d-127">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="4f75d-127">Related Sections</span></span>  
 [<span data-ttu-id="4f75d-128">Extension des encodeurs et des sérialiseurs</span><span class="sxs-lookup"><span data-stu-id="4f75d-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="4f75d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f75d-129">See Also</span></span>  
 [<span data-ttu-id="4f75d-130">Bonnes pratiques : gestion des versions des contrats de données</span><span class="sxs-lookup"><span data-stu-id="4f75d-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [<span data-ttu-id="4f75d-131">Gestion des versions des services</span><span class="sxs-lookup"><span data-stu-id="4f75d-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)
