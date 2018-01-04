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
ms.workload: dotnet
ms.openlocfilehash: 73fad36b5bf14745ca70d297fa988b90d46990df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="84770-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="84770-102">ServiceCredentials</span></span>
<span data-ttu-id="84770-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="84770-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84770-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84770-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="84770-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="84770-105">Methods</span></span>  
 <span data-ttu-id="84770-106">La classe ServiceCredentials ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="84770-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="84770-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="84770-107">Properties</span></span>  
 <span data-ttu-id="84770-108">La classe ServiceCredentials a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="84770-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="84770-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="84770-109">ClientCertificate</span></span>  
 <span data-ttu-id="84770-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="84770-110">Data type: string</span></span>  
  
 <span data-ttu-id="84770-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="84770-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84770-112">Paramètres d'authentification et d'approvisionnement des certificats clients pour ce service.</span><span class="sxs-lookup"><span data-stu-id="84770-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="84770-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="84770-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="84770-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="84770-114">Data type: string</span></span>  
  
 <span data-ttu-id="84770-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="84770-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84770-116">Paramètres actuels d'authentification de jeton émis pour ce service.</span><span class="sxs-lookup"><span data-stu-id="84770-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="84770-117">Peer</span><span class="sxs-lookup"><span data-stu-id="84770-117">Peer</span></span>  
 <span data-ttu-id="84770-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="84770-118">Data type: string</span></span>  
  
 <span data-ttu-id="84770-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="84770-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84770-120">Authentification des informations d'identification actuelles et fourniture des paramètres à utiliser par les points de terminaison de transport d'homologue.</span><span class="sxs-lookup"><span data-stu-id="84770-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="84770-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="84770-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="84770-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="84770-122">Data type: string</span></span>  
  
 <span data-ttu-id="84770-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="84770-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84770-124">Spécifie les paramètres actuels de conversation sécurisée.</span><span class="sxs-lookup"><span data-stu-id="84770-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="84770-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="84770-125">ServiceCertificate</span></span>  
 <span data-ttu-id="84770-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="84770-126">Data type: string</span></span>  
  
 <span data-ttu-id="84770-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="84770-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84770-128">Certificat associé à ce service.</span><span class="sxs-lookup"><span data-stu-id="84770-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="84770-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="84770-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="84770-130">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="84770-130">Data type: string</span></span>  
  
 <span data-ttu-id="84770-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="84770-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84770-132">Paramètres de nom d'utilisateur/mot de passe pour ce service.</span><span class="sxs-lookup"><span data-stu-id="84770-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="84770-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="84770-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="84770-134">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="84770-134">Data type: string</span></span>  
  
 <span data-ttu-id="84770-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="84770-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84770-136">Paramètres d'authentification Windows pour ce service.</span><span class="sxs-lookup"><span data-stu-id="84770-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84770-137">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="84770-137">Requirements</span></span>  
  
|<span data-ttu-id="84770-138">MOF</span><span class="sxs-lookup"><span data-stu-id="84770-138">MOF</span></span>|<span data-ttu-id="84770-139">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="84770-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="84770-140">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="84770-140">Namespace</span></span>|<span data-ttu-id="84770-141">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="84770-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84770-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84770-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
