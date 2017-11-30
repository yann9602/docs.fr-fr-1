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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d10fdd9e33b078fa392e0ef359372913f9ba133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="45aaf-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="45aaf-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="45aaf-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="45aaf-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45aaf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45aaf-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="45aaf-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="45aaf-105">Methods</span></span>  
 <span data-ttu-id="45aaf-106">La classe ServiceMetadataBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="45aaf-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="45aaf-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="45aaf-107">Properties</span></span>  
 <span data-ttu-id="45aaf-108">La classe ServiceMetadataBehavior a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="45aaf-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="45aaf-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="45aaf-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="45aaf-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="45aaf-110">Data type: string</span></span>  
  
 <span data-ttu-id="45aaf-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="45aaf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45aaf-112">Définit l'emplacement vers lequel le service redirige les demandes de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="45aaf-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="45aaf-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="45aaf-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="45aaf-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="45aaf-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="45aaf-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="45aaf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45aaf-116">Vérifie si le service publie son WSDL à l'adresse contrôlée par l'attribut `HttpGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="45aaf-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="45aaf-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="45aaf-117">HttpGetUrl</span></span>  
 <span data-ttu-id="45aaf-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="45aaf-118">Data type: string</span></span>  
  
 <span data-ttu-id="45aaf-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="45aaf-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45aaf-120">Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTP.</span><span class="sxs-lookup"><span data-stu-id="45aaf-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="45aaf-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="45aaf-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="45aaf-122">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="45aaf-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="45aaf-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="45aaf-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45aaf-124">Vérifie si le service publie son WSDL sur HTTPS à l'adresse contrôlée par l'attribut `HttpsGetUrl`.</span><span class="sxs-lookup"><span data-stu-id="45aaf-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="45aaf-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="45aaf-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="45aaf-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="45aaf-126">Data type: string</span></span>  
  
 <span data-ttu-id="45aaf-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="45aaf-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45aaf-128">Définit l'emplacement auquel le service WSDL est publié pour récupération à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="45aaf-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45aaf-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="45aaf-129">Requirements</span></span>  
  
|<span data-ttu-id="45aaf-130">MOF</span><span class="sxs-lookup"><span data-stu-id="45aaf-130">MOF</span></span>|<span data-ttu-id="45aaf-131">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="45aaf-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="45aaf-132">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="45aaf-132">Namespace</span></span>|<span data-ttu-id="45aaf-133">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="45aaf-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45aaf-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45aaf-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
