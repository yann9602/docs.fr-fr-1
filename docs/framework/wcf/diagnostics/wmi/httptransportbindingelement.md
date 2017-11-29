---
title: HttpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b1542406caf9bb3684ccf2d97ed441f1dc3d0db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="07993-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="07993-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="07993-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="07993-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07993-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07993-104">Syntax</span></span>  
  
```  
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="07993-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="07993-105">Methods</span></span>  
 <span data-ttu-id="07993-106">La classe HttpTransportBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="07993-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="07993-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="07993-107">Properties</span></span>  
 <span data-ttu-id="07993-108">La classe HttpTransportBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="07993-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="07993-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="07993-109">AllowCookies</span></span>  
 <span data-ttu-id="07993-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="07993-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="07993-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-112">Valeur qui indique si le client accepte les cookies et les propage aux demandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="07993-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="07993-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="07993-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="07993-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="07993-114">Data type: string</span></span>  
  
 <span data-ttu-id="07993-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-116">Schéma d'authentification utilisé pour authentifier les demandes d'un client traitées par un écouteur HTTP.</span><span class="sxs-lookup"><span data-stu-id="07993-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="07993-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="07993-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="07993-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="07993-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="07993-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-120">Valeur qui indique si les proxys sont ignorés pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="07993-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="07993-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="07993-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="07993-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="07993-122">Data type: string</span></span>  
  
 <span data-ttu-id="07993-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-124">Valeur qui indique si le nom d'hôte est utilisé pour atteindre le service lors de la correspondance avec l'URI.</span><span class="sxs-lookup"><span data-stu-id="07993-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="07993-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="07993-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="07993-126">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="07993-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="07993-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-128">En cas d'activation, les connexions HTTP sont maintenues indépendamment du niveau d'activité.</span><span class="sxs-lookup"><span data-stu-id="07993-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="07993-129">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="07993-129">MaxBufferSize</span></span>  
 <span data-ttu-id="07993-130">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="07993-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="07993-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-132">La taille maximale du pool de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="07993-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="07993-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="07993-133">ProxyAddress</span></span>  
 <span data-ttu-id="07993-134">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="07993-134">Data type: string</span></span>  
  
 <span data-ttu-id="07993-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-136">URI qui contient l'adresse du proxy à utiliser pour les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="07993-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="07993-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="07993-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="07993-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="07993-138">Data type: string</span></span>  
  
 <span data-ttu-id="07993-139">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-140">Schéma d'authentification utilisé pour authentifier les demandes d'un client traitées par un proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="07993-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="07993-141">Realm</span><span class="sxs-lookup"><span data-stu-id="07993-141">Realm</span></span>  
 <span data-ttu-id="07993-142">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="07993-142">Data type: string</span></span>  
  
 <span data-ttu-id="07993-143">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-144">Domaine d'authentification.</span><span class="sxs-lookup"><span data-stu-id="07993-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="07993-145">TransferMode</span><span class="sxs-lookup"><span data-stu-id="07993-145">TransferMode</span></span>  
 <span data-ttu-id="07993-146">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="07993-146">Data type: string</span></span>  
  
 <span data-ttu-id="07993-147">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-148">Valeur qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu ou s'il s'agit d'une demande ou d'une réponse.</span><span class="sxs-lookup"><span data-stu-id="07993-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="07993-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="07993-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="07993-150">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="07993-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="07993-151">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-152">Valeur qui indique si le partage de connexion non sécurisé est activé sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="07993-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="07993-153">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="07993-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="07993-154">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="07993-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="07993-155">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="07993-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07993-156">Valeur qui indique si les paramètres de proxy à l'échelle de l'ordinateur sont utilisés à la place des paramètres propres à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="07993-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07993-157">Spécifications</span><span class="sxs-lookup"><span data-stu-id="07993-157">Requirements</span></span>  
  
|<span data-ttu-id="07993-158">MOF</span><span class="sxs-lookup"><span data-stu-id="07993-158">MOF</span></span>|<span data-ttu-id="07993-159">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="07993-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="07993-160">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="07993-160">Namespace</span></span>|<span data-ttu-id="07993-161">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="07993-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07993-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07993-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
