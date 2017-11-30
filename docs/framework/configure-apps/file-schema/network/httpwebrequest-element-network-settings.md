---
title: "&lt;httpWebRequest&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0a4490870cb12ff221f75b043f01baad9b5c7c96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lthttpwebrequestgt-element-network-settings"></a><span data-ttu-id="0cde6-102">&lt;httpWebRequest&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="0cde6-102">&lt;httpWebRequest&gt; Element (Network Settings)</span></span>
<span data-ttu-id="0cde6-103">Personnalise les paramètres de la demande Web.</span><span class="sxs-lookup"><span data-stu-id="0cde6-103">Customizes Web request parameters.</span></span>  
  
 <span data-ttu-id="0cde6-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0cde6-104">\<configuration></span></span>  
<span data-ttu-id="0cde6-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="0cde6-105">\<system.net></span></span>  
<span data-ttu-id="0cde6-106">\<Paramètres ></span><span class="sxs-lookup"><span data-stu-id="0cde6-106">\<settings></span></span>  
<span data-ttu-id="0cde6-107">\<httpWebRequest ></span><span class="sxs-lookup"><span data-stu-id="0cde6-107">\<httpWebRequest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cde6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cde6-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cde6-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0cde6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0cde6-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0cde6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cde6-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0cde6-111">Attributes</span></span>  
  
|<span data-ttu-id="0cde6-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="0cde6-112">**Attribute**</span></span>|<span data-ttu-id="0cde6-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="0cde6-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="0cde6-114">Spécifie la longueur maximale d’un en-tête de réponse, en kilo-octets.</span><span class="sxs-lookup"><span data-stu-id="0cde6-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="0cde6-115">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="0cde6-115">The default is 64.</span></span> <span data-ttu-id="0cde6-116">La valeur -1 indique qu’aucune limite de taille ne sera imposée sur les en-têtes de réponse.</span><span class="sxs-lookup"><span data-stu-id="0cde6-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="0cde6-117">Spécifie la longueur maximale d’une réponse d’erreur, en kilo-octets.</span><span class="sxs-lookup"><span data-stu-id="0cde6-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="0cde6-118">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="0cde6-118">The default is 64.</span></span> <span data-ttu-id="0cde6-119">La valeur -1 indique qu’aucune limite de taille ne sera imposée sur la réponse d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0cde6-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="0cde6-120">Spécifie la longueur maximale d’un téléchargement en réponse à un code d’erreur non autorisée, en octets.</span><span class="sxs-lookup"><span data-stu-id="0cde6-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="0cde6-121">La valeur par défaut est -1.</span><span class="sxs-lookup"><span data-stu-id="0cde6-121">The default is -1.</span></span> <span data-ttu-id="0cde6-122">La valeur -1 indique qu’aucune limite de taille ne sera imposée pour le téléchargement.</span><span class="sxs-lookup"><span data-stu-id="0cde6-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="0cde6-123">Spécifie si l’analyse des en-têtes non sécurisé est activé.</span><span class="sxs-lookup"><span data-stu-id="0cde6-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="0cde6-124">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="0cde6-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0cde6-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0cde6-125">Child Elements</span></span>  
 <span data-ttu-id="0cde6-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0cde6-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0cde6-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0cde6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0cde6-128">**Élément**</span><span class="sxs-lookup"><span data-stu-id="0cde6-128">**Element**</span></span>|<span data-ttu-id="0cde6-129">**Description**</span><span class="sxs-lookup"><span data-stu-id="0cde6-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0cde6-130">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0cde6-130">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="0cde6-131">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="0cde6-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cde6-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="0cde6-132">Remarks</span></span>  
 <span data-ttu-id="0cde6-133">Par défaut, le .NET Framework applique strictement la norme RFC 2616 pour l’analyse URI.</span><span class="sxs-lookup"><span data-stu-id="0cde6-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="0cde6-134">Certaines réponses du serveur peuvent inclure des caractères de contrôle dans les champs interdits, ce qui provoquent le <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> méthode pour lever une <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="0cde6-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="0cde6-135">Si **useUnsafeHeaderParsing** a la valeur **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> ne lèvent pas dans ce cas ; cependant, votre application sera vulnérable à plusieurs formes d’attaques d’analyse URI.</span><span class="sxs-lookup"><span data-stu-id="0cde6-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="0cde6-136">La meilleure solution consiste à modifier le serveur afin que la réponse n’inclut pas les caractères de contrôle.</span><span class="sxs-lookup"><span data-stu-id="0cde6-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0cde6-137">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="0cde6-137">Configuration Files</span></span>  
 <span data-ttu-id="0cde6-138">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0cde6-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cde6-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="0cde6-139">Example</span></span>  
 <span data-ttu-id="0cde6-140">L’exemple suivant montre comment spécifier une valeur plus élevée que la longueur maximale d’en-tête normal.</span><span class="sxs-lookup"><span data-stu-id="0cde6-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cde6-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cde6-141">See Also</span></span>  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
 [<span data-ttu-id="0cde6-142">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="0cde6-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
