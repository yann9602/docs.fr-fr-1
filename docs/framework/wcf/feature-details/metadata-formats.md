---
title: "Formats de métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d250b57282d24780dcdd1e045f18d7528bd86a90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="metadata-formats"></a><span data-ttu-id="de5ea-102">Formats de métadonnées</span><span class="sxs-lookup"><span data-stu-id="de5ea-102">Metadata Formats</span></span>
<span data-ttu-id="de5ea-103">Le tableau suivant répertorie les formats de métadonnées pris en charge par [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de5ea-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports the metadata formats in the following table.</span></span>  
  
## <a name="metadata-specifications-and-usage"></a><span data-ttu-id="de5ea-104">Spécification et utilisation des métadonnées</span><span class="sxs-lookup"><span data-stu-id="de5ea-104">Metadata Specifications and Usage</span></span>  
  
|<span data-ttu-id="de5ea-105">Protocole</span><span class="sxs-lookup"><span data-stu-id="de5ea-105">Protocol</span></span>|<span data-ttu-id="de5ea-106">Spécification et utilisation</span><span class="sxs-lookup"><span data-stu-id="de5ea-106">Specification and usage</span></span>|  
|--------------|-----------------------------|  
|<span data-ttu-id="de5ea-107">WSDL 1.1</span><span class="sxs-lookup"><span data-stu-id="de5ea-107">WSDL 1.1</span></span>|[<span data-ttu-id="de5ea-108">Web Services Description Language (WSDL) 1.1</span><span class="sxs-lookup"><span data-stu-id="de5ea-108">Web Services Description Language (WSDL) 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="de5ea-109"> utilise WSDL (Web Services Description Language) pour décrire des services.</span><span class="sxs-lookup"><span data-stu-id="de5ea-109"> uses Web Services Description Language (WSDL) to describe services.</span></span>|  
|<span data-ttu-id="de5ea-110">Schéma XML</span><span class="sxs-lookup"><span data-stu-id="de5ea-110">XML Schema</span></span>|<span data-ttu-id="de5ea-111">[XML Schema Part 2 : Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861) et [XML Schema Part 1 : Structures, deuxième édition](http://go.microsoft.com/fwlink/?LinkId=94862)</span><span class="sxs-lookup"><span data-stu-id="de5ea-111">[XML Schema Part 2: Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861) and [XML Schema Part 1: Structures Second Edition](http://go.microsoft.com/fwlink/?LinkId=94862)</span></span><br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="de5ea-112"> utilise le schéma XML pour décrire les types de données utilisés dans les messages.</span><span class="sxs-lookup"><span data-stu-id="de5ea-112"> uses the XML Schema to describe data types used in messages.</span></span>|  
|<span data-ttu-id="de5ea-113">WS-Policy</span><span class="sxs-lookup"><span data-stu-id="de5ea-113">WS Policy</span></span>|[<span data-ttu-id="de5ea-114">Stratégie de Services Web 1.2 - infrastructure (WS-Policy)</span><span class="sxs-lookup"><span data-stu-id="de5ea-114">Web Services Policy 1.2 - Framework (WS-Policy)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [<span data-ttu-id="de5ea-115">Web Services Policy 1.5 - infrastructure</span><span class="sxs-lookup"><span data-stu-id="de5ea-115">Web Services Policy 1.5 - Framework</span></span>](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="de5ea-116"> utilise la spécification WS-Policy 1.2 ou 1.5 avec des assertions spécifiques au domaine pour décrire les spécifications et les fonctions du service.</span><span class="sxs-lookup"><span data-stu-id="de5ea-116"> uses the WS-Policy 1.2 or 1.5 specifications with domain-specific assertions to describe service requirements and capabilities.</span></span>|  
|<span data-ttu-id="de5ea-117">Pièces jointes WS-Policy</span><span class="sxs-lookup"><span data-stu-id="de5ea-117">WS Policy Attachments</span></span>|[<span data-ttu-id="de5ea-118">Stratégie de Services Web 1.2 - pièce jointe (WS-PolicyAttachment)</span><span class="sxs-lookup"><span data-stu-id="de5ea-118">Web Services Policy 1.2 - Attachment (WS-PolicyAttachment)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="de5ea-119"> implémente les pièces jointes WS-Policy pour joindre des expressions de stratégie à différentes étendues dans WSDL.</span><span class="sxs-lookup"><span data-stu-id="de5ea-119"> implements WS-Policy Attachments to attach policy expressions at various scopes in WSDL.</span></span>|  
|<span data-ttu-id="de5ea-120">Échange de métadonnées WS</span><span class="sxs-lookup"><span data-stu-id="de5ea-120">WS Metadata Exchange</span></span>|[<span data-ttu-id="de5ea-121">Échange de métadonnées de Services Web (WS-MetadataExchange) version 1.1</span><span class="sxs-lookup"><span data-stu-id="de5ea-121">Web Services Metadata Exchange (WS-MetadataExchange) version 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="de5ea-122"> implémente WS-MetadataExchange pour récupérer XML Schema, WSDL et WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="de5ea-122"> implements WS-MetadataExchange to retrieve XML Schema, WSDL, and WS-Policy.</span></span>|  
|<span data-ttu-id="de5ea-123">WS-Addressing Binding pour WSDL</span><span class="sxs-lookup"><span data-stu-id="de5ea-123">WS Addressing Binding for WSDL</span></span>|[<span data-ttu-id="de5ea-124">Web Services Addressing 1.0 - liaison WSDL</span><span class="sxs-lookup"><span data-stu-id="de5ea-124">Web Services Addressing 1.0 - WSDL Binding</span></span>](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="de5ea-125"> implémente WS-Addressing Binding pour WSDL pour joindre des données d'adressage dans WSDL.</span><span class="sxs-lookup"><span data-stu-id="de5ea-125"> implements WS-Addressing Binding for WSDL to attach addressing information in WSDL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de5ea-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de5ea-126">See Also</span></span>  
 [<span data-ttu-id="de5ea-127">Protocoles pris en charge par les liaisons d’interopérabilité fournies par le système des Services Web</span><span class="sxs-lookup"><span data-stu-id="de5ea-127">Web Services Protocols Supported by System-Provided Interoperability Bindings</span></span>](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [<span data-ttu-id="de5ea-128">WSDL et stratégie</span><span class="sxs-lookup"><span data-stu-id="de5ea-128">WSDL and Policy</span></span>](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
