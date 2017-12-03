---
title: ClientCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55f7ef12f67bd719f72f158a1fca6f120b4f448a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="clientcredentials"></a><span data-ttu-id="bc7b5-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="bc7b5-102">ClientCredentials</span></span>
<span data-ttu-id="bc7b5-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="bc7b5-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc7b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc7b5-104">Syntax</span></span>  
  
```  
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bc7b5-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bc7b5-105">Methods</span></span>  
 <span data-ttu-id="bc7b5-106">La classe ClientCredentials ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="bc7b5-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bc7b5-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bc7b5-107">Properties</span></span>  
 <span data-ttu-id="bc7b5-108">La classe ClientCredentials a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="bc7b5-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="bc7b5-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="bc7b5-109">ClientCertificate</span></span>  
 <span data-ttu-id="bc7b5-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bc7b5-110">Data type: string</span></span>  
  
 <span data-ttu-id="bc7b5-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bc7b5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc7b5-112">Certificat X.509 que le client utilise pour s'authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="bc7b5-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="bc7b5-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="bc7b5-113">HttpDigest</span></span>  
 <span data-ttu-id="bc7b5-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bc7b5-114">Data type: string</span></span>  
  
 <span data-ttu-id="bc7b5-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bc7b5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc7b5-116">Informations d'identification Http Digest actuelles.</span><span class="sxs-lookup"><span data-stu-id="bc7b5-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="bc7b5-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="bc7b5-117">IssuedToken</span></span>  
 <span data-ttu-id="bc7b5-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bc7b5-118">Data type: string</span></span>  
  
 <span data-ttu-id="bc7b5-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bc7b5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc7b5-120">Adresse de point de terminaison et liaison utilisées pour contacter le service de jetons de sécurité local.</span><span class="sxs-lookup"><span data-stu-id="bc7b5-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="bc7b5-121">Peer</span><span class="sxs-lookup"><span data-stu-id="bc7b5-121">Peer</span></span>  
 <span data-ttu-id="bc7b5-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bc7b5-122">Data type: string</span></span>  
  
 <span data-ttu-id="bc7b5-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bc7b5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc7b5-124">Informations d'identification que le nœud d'homologue utilise pour s'authentifier auprès d'autres nœuds dans la maille.</span><span class="sxs-lookup"><span data-stu-id="bc7b5-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="bc7b5-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="bc7b5-125">ServiceCertificate</span></span>  
 <span data-ttu-id="bc7b5-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bc7b5-126">Data type: string</span></span>  
  
 <span data-ttu-id="bc7b5-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bc7b5-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc7b5-128">Certificat X.509 du service.</span><span class="sxs-lookup"><span data-stu-id="bc7b5-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="bc7b5-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="bc7b5-129">SupportInteractive</span></span>  
 <span data-ttu-id="bc7b5-130">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="bc7b5-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="bc7b5-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bc7b5-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc7b5-132">Valeur booléenne qui spécifie si les informations d'identification prennent en charge la négociation interactive.</span><span class="sxs-lookup"><span data-stu-id="bc7b5-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="bc7b5-133">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="bc7b5-133">UserName</span></span>  
 <span data-ttu-id="bc7b5-134">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bc7b5-134">Data type: string</span></span>  
  
 <span data-ttu-id="bc7b5-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bc7b5-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc7b5-136">Nom d'utilisateur et mot de passe que le client utilise pour s'authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="bc7b5-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="bc7b5-137">Windows</span><span class="sxs-lookup"><span data-stu-id="bc7b5-137">Windows</span></span>  
 <span data-ttu-id="bc7b5-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bc7b5-138">Data type: string</span></span>  
  
 <span data-ttu-id="bc7b5-139">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bc7b5-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc7b5-140">Informations d'identification que le client utilise pour s'authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="bc7b5-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc7b5-141">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bc7b5-141">Requirements</span></span>  
  
|<span data-ttu-id="bc7b5-142">MOF</span><span class="sxs-lookup"><span data-stu-id="bc7b5-142">MOF</span></span>|<span data-ttu-id="bc7b5-143">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bc7b5-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bc7b5-144">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="bc7b5-144">Namespace</span></span>|<span data-ttu-id="bc7b5-145">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bc7b5-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc7b5-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc7b5-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
