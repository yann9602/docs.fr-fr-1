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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4cc9d7d7d46157b7df202c6daffb31b90fa98c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="0ad75-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="0ad75-102">ServiceCredentials</span></span>
<span data-ttu-id="0ad75-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="0ad75-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ad75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ad75-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="0ad75-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0ad75-105">Methods</span></span>  
 <span data-ttu-id="0ad75-106">La classe ServiceCredentials ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="0ad75-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0ad75-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0ad75-107">Properties</span></span>  
 <span data-ttu-id="0ad75-108">La classe ServiceCredentials a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="0ad75-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="0ad75-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="0ad75-109">ClientCertificate</span></span>  
 <span data-ttu-id="0ad75-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="0ad75-110">Data type: string</span></span>  
  
 <span data-ttu-id="0ad75-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="0ad75-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ad75-112">Paramètres d'authentification et d'approvisionnement des certificats clients pour ce service.</span><span class="sxs-lookup"><span data-stu-id="0ad75-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="0ad75-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="0ad75-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="0ad75-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="0ad75-114">Data type: string</span></span>  
  
 <span data-ttu-id="0ad75-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="0ad75-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ad75-116">Paramètres actuels d'authentification de jeton émis pour ce service.</span><span class="sxs-lookup"><span data-stu-id="0ad75-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="0ad75-117">Peer</span><span class="sxs-lookup"><span data-stu-id="0ad75-117">Peer</span></span>  
 <span data-ttu-id="0ad75-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="0ad75-118">Data type: string</span></span>  
  
 <span data-ttu-id="0ad75-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="0ad75-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ad75-120">Authentification des informations d'identification actuelles et fourniture des paramètres à utiliser par les points de terminaison de transport d'homologue.</span><span class="sxs-lookup"><span data-stu-id="0ad75-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="0ad75-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="0ad75-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="0ad75-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="0ad75-122">Data type: string</span></span>  
  
 <span data-ttu-id="0ad75-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="0ad75-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ad75-124">Spécifie les paramètres actuels de conversation sécurisée.</span><span class="sxs-lookup"><span data-stu-id="0ad75-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="0ad75-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="0ad75-125">ServiceCertificate</span></span>  
 <span data-ttu-id="0ad75-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="0ad75-126">Data type: string</span></span>  
  
 <span data-ttu-id="0ad75-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="0ad75-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ad75-128">Certificat associé à ce service.</span><span class="sxs-lookup"><span data-stu-id="0ad75-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="0ad75-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="0ad75-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="0ad75-130">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="0ad75-130">Data type: string</span></span>  
  
 <span data-ttu-id="0ad75-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="0ad75-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ad75-132">Paramètres de nom d'utilisateur/mot de passe pour ce service.</span><span class="sxs-lookup"><span data-stu-id="0ad75-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="0ad75-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="0ad75-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="0ad75-134">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="0ad75-134">Data type: string</span></span>  
  
 <span data-ttu-id="0ad75-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="0ad75-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ad75-136">Paramètres d'authentification Windows pour ce service.</span><span class="sxs-lookup"><span data-stu-id="0ad75-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ad75-137">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0ad75-137">Requirements</span></span>  
  
|<span data-ttu-id="0ad75-138">MOF</span><span class="sxs-lookup"><span data-stu-id="0ad75-138">MOF</span></span>|<span data-ttu-id="0ad75-139">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0ad75-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0ad75-140">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="0ad75-140">Namespace</span></span>|<span data-ttu-id="0ad75-141">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0ad75-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ad75-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ad75-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
