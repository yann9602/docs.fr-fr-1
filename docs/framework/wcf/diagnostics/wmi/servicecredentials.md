---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89aff21ed916e1b486a191f86dde5ed8b3e4ba22
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="ba2f3-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="ba2f3-102">ServiceCredentials</span></span>
<span data-ttu-id="ba2f3-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="ba2f3-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba2f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba2f3-104">Syntax</span></span>  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ba2f3-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ba2f3-105">Methods</span></span>  
 <span data-ttu-id="ba2f3-106">La classe ServiceCredentials ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="ba2f3-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ba2f3-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ba2f3-107">Properties</span></span>  
 <span data-ttu-id="ba2f3-108">La classe ServiceCredentials a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba2f3-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="ba2f3-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="ba2f3-109">ClientCertificate</span></span>  
 <span data-ttu-id="ba2f3-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="ba2f3-110">Data type: string</span></span>  
  
 <span data-ttu-id="ba2f3-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ba2f3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba2f3-112">Paramètres d'authentification et d'approvisionnement des certificats clients pour ce service.</span><span class="sxs-lookup"><span data-stu-id="ba2f3-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="ba2f3-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="ba2f3-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="ba2f3-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="ba2f3-114">Data type: string</span></span>  
  
 <span data-ttu-id="ba2f3-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ba2f3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba2f3-116">Paramètres actuels d'authentification de jeton émis pour ce service.</span><span class="sxs-lookup"><span data-stu-id="ba2f3-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="ba2f3-117">Peer</span><span class="sxs-lookup"><span data-stu-id="ba2f3-117">Peer</span></span>  
 <span data-ttu-id="ba2f3-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="ba2f3-118">Data type: string</span></span>  
  
 <span data-ttu-id="ba2f3-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ba2f3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba2f3-120">Authentification des informations d'identification actuelles et fourniture des paramètres à utiliser par les points de terminaison de transport d'homologue.</span><span class="sxs-lookup"><span data-stu-id="ba2f3-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="ba2f3-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="ba2f3-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="ba2f3-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="ba2f3-122">Data type: string</span></span>  
  
 <span data-ttu-id="ba2f3-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ba2f3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba2f3-124">Spécifie les paramètres actuels de conversation sécurisée.</span><span class="sxs-lookup"><span data-stu-id="ba2f3-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="ba2f3-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="ba2f3-125">ServiceCertificate</span></span>  
 <span data-ttu-id="ba2f3-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="ba2f3-126">Data type: string</span></span>  
  
 <span data-ttu-id="ba2f3-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ba2f3-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba2f3-128">Certificat associé à ce service.</span><span class="sxs-lookup"><span data-stu-id="ba2f3-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="ba2f3-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="ba2f3-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="ba2f3-130">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="ba2f3-130">Data type: string</span></span>  
  
 <span data-ttu-id="ba2f3-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ba2f3-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba2f3-132">Paramètres de nom d'utilisateur/mot de passe pour ce service.</span><span class="sxs-lookup"><span data-stu-id="ba2f3-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="ba2f3-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="ba2f3-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="ba2f3-134">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="ba2f3-134">Data type: string</span></span>  
  
 <span data-ttu-id="ba2f3-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ba2f3-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba2f3-136">Paramètres d'authentification Windows pour ce service.</span><span class="sxs-lookup"><span data-stu-id="ba2f3-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba2f3-137">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ba2f3-137">Requirements</span></span>  
  
|<span data-ttu-id="ba2f3-138">MOF</span><span class="sxs-lookup"><span data-stu-id="ba2f3-138">MOF</span></span>|<span data-ttu-id="ba2f3-139">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ba2f3-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ba2f3-140">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="ba2f3-140">Namespace</span></span>|<span data-ttu-id="ba2f3-141">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ba2f3-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba2f3-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba2f3-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
