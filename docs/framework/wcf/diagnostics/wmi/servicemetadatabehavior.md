---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c05f6be9fc0507b7e2f1de4374e3b9bbe3e2a10e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="f8bd9-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="f8bd9-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="f8bd9-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="f8bd9-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8bd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8bd9-104">Syntax</span></span>  
  
```  
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f8bd9-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f8bd9-105">Methods</span></span>  
 <span data-ttu-id="f8bd9-106">La classe ServiceMetadataBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f8bd9-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f8bd9-107">Properties</span></span>  
 <span data-ttu-id="f8bd9-108">La classe ServiceMetadataBehavior a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="f8bd9-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="f8bd9-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="f8bd9-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="f8bd9-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="f8bd9-110">Data type: string</span></span>  
  
 <span data-ttu-id="f8bd9-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="f8bd9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f8bd9-112">Définit l'emplacement vers lequel le service redirige les demandes de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="f8bd9-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="f8bd9-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="f8bd9-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="f8bd9-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="f8bd9-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="f8bd9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f8bd9-116">Vérifie si le service publie son WSDL à l'adresse contrôlée par l'attribut `HttpGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="f8bd9-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="f8bd9-117">HttpGetUrl</span></span>  
 <span data-ttu-id="f8bd9-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="f8bd9-118">Data type: string</span></span>  
  
 <span data-ttu-id="f8bd9-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="f8bd9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f8bd9-120">Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTP.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="f8bd9-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="f8bd9-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="f8bd9-122">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="f8bd9-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="f8bd9-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="f8bd9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f8bd9-124">Vérifie si le service publie son WSDL sur HTTPS à l'adresse contrôlée par l'attribut `HttpsGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="f8bd9-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="f8bd9-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="f8bd9-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="f8bd9-126">Data type: string</span></span>  
  
 <span data-ttu-id="f8bd9-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="f8bd9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f8bd9-128">Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8bd9-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f8bd9-129">Requirements</span></span>  
  
|<span data-ttu-id="f8bd9-130">MOF</span><span class="sxs-lookup"><span data-stu-id="f8bd9-130">MOF</span></span>|<span data-ttu-id="f8bd9-131">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f8bd9-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f8bd9-132">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="f8bd9-132">Namespace</span></span>|<span data-ttu-id="f8bd9-133">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f8bd9-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8bd9-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8bd9-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
