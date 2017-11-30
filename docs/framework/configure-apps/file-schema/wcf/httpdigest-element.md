---
title: "&lt;httpDigest&gt;, élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22c89aa69ea686274bb232eb04eec930ffc5b51d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lthttpdigestgt-element"></a><span data-ttu-id="0705a-102">&lt;httpDigest&gt;, élément</span><span class="sxs-lookup"><span data-stu-id="0705a-102">&lt;httpDigest&gt; Element</span></span>
<span data-ttu-id="0705a-103">Spécifie une information d’identification de type condensat utilisée lors de l’authentification du client à un service.</span><span class="sxs-lookup"><span data-stu-id="0705a-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="0705a-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0705a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0705a-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="0705a-105">\<behaviors></span></span>  
<span data-ttu-id="0705a-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0705a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="0705a-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="0705a-107">\<behavior></span></span>  
<span data-ttu-id="0705a-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="0705a-108">\<clientCredentials></span></span>  
<span data-ttu-id="0705a-109">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="0705a-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0705a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0705a-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0705a-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0705a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0705a-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0705a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0705a-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="0705a-113">Attributes</span></span>  
  
|<span data-ttu-id="0705a-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="0705a-114">Attribute</span></span>|<span data-ttu-id="0705a-115">Description</span><span class="sxs-lookup"><span data-stu-id="0705a-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="0705a-116">Définit la préférence d'emprunt d'identité que le client communique au serveur.</span><span class="sxs-lookup"><span data-stu-id="0705a-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="0705a-117">Le mode d'emprunt d'identité que le client sélectionne n'est pas appliqué sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="0705a-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="0705a-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0705a-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0705a-119">-Identification : Le serveur peut obtenir l’identité et les privilèges du client, mais ne peut pas l’identité du client.</span><span class="sxs-lookup"><span data-stu-id="0705a-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="0705a-120">-L’emprunt d’identité : Le serveur peut emprunter l’identité de contexte de sécurité du client sur le système local.</span><span class="sxs-lookup"><span data-stu-id="0705a-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="0705a-121">-Delegation : Le serveur peut emprunter l’identité de contexte de sécurité du client sur les systèmes distants.</span><span class="sxs-lookup"><span data-stu-id="0705a-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="0705a-122">-Anonyme : Le serveur ne peut pas emprunter l’identité ou identifier le client.</span><span class="sxs-lookup"><span data-stu-id="0705a-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="0705a-123">-None : Un niveau d’emprunt d’identité n’est affecté.</span><span class="sxs-lookup"><span data-stu-id="0705a-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="0705a-124">La valeur par défaut est Identification.</span><span class="sxs-lookup"><span data-stu-id="0705a-124">The default is Identification.</span></span> <span data-ttu-id="0705a-125">Cet attribut est de type <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="0705a-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0705a-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0705a-126">Child Elements</span></span>  
 <span data-ttu-id="0705a-127">None</span><span class="sxs-lookup"><span data-stu-id="0705a-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0705a-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0705a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="0705a-129">Élément</span><span class="sxs-lookup"><span data-stu-id="0705a-129">Element</span></span>|<span data-ttu-id="0705a-130">Description</span><span class="sxs-lookup"><span data-stu-id="0705a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0705a-131">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="0705a-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="0705a-132">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="0705a-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0705a-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="0705a-133">Remarks</span></span>  
 <span data-ttu-id="0705a-134">Un condensat est un hachage déterminé à l’aide d’un algorithme et d’un jeu d’entrées.</span><span class="sxs-lookup"><span data-stu-id="0705a-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="0705a-135">L'authentificateur et l'authentifié acceptent un algorithme et échangent les données utilisées comme entrées.</span><span class="sxs-lookup"><span data-stu-id="0705a-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="0705a-136">Le client peut calculer le hachage et l'envoyer au service.</span><span class="sxs-lookup"><span data-stu-id="0705a-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="0705a-137">Le service calcule également le hachage et compare les valeurs.</span><span class="sxs-lookup"><span data-stu-id="0705a-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="0705a-138">Une correspondance valide le client.</span><span class="sxs-lookup"><span data-stu-id="0705a-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="0705a-139">Cette fonctionnalité doit être activée avec Active Directory sur Windows et les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="0705a-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="0705a-140">[L’authentification dans IIS 6.0 digest](http://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="0705a-140"> [Digest Authentication in IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0705a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0705a-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [<span data-ttu-id="0705a-142">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="0705a-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="0705a-143">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="0705a-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="0705a-144">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="0705a-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="0705a-145">Sécurisation des Services et Clients</span><span class="sxs-lookup"><span data-stu-id="0705a-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
