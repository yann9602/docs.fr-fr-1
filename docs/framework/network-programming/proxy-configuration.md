---
title: Configuration du proxy
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 41f7cfe76acfb4b6bbf66207685935c190a51901
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="proxy-configuration"></a><span data-ttu-id="7b8e4-102">Configuration du proxy</span><span class="sxs-lookup"><span data-stu-id="7b8e4-102">Proxy Configuration</span></span>
<span data-ttu-id="7b8e4-103">Un serveur proxy gère les demandes du client pour les ressources.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="7b8e4-104">Un proxy peut retourner une ressource demandée à partir de son cache ou transférer la demande au serveur sur lequel réside la ressource.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="7b8e4-105">Les proxies peuvent améliorer les performances réseau en réduisant le nombre de demandes envoyées aux serveurs distants.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="7b8e4-106">Les proxies peuvent également être utilisés pour restreindre l'accès aux ressources.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="7b8e4-107">Proxies adaptatifs</span><span class="sxs-lookup"><span data-stu-id="7b8e4-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="7b8e4-108">Dans le .NET Framework, les proxies sont fournis sous deux formes : adaptatifs et statiques.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="7b8e4-109">Les proxies adaptatifs ajustent leurs paramètres lorsque la configuration du réseau change.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="7b8e4-110">Par exemple, si l'utilisateur d'un ordinateur portable démarre une connexion réseau d'accès à distance, un proxy adaptatif identifie cette modification, détecte et exécute son nouveau script de configuration, et ajuste ses paramètres de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="7b8e4-111">Les proxys adaptatifs sont configurés par un script de configuration (voir [Détection automatique de proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="7b8e4-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="7b8e4-112">Le script génère un ensemble de protocoles d'application et un proxy pour chaque protocole.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="7b8e4-113">Plusieurs options contrôlent la façon dont le script de configuration est exécuté.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-113">Several options control how the configuration script is run.</span></span> <span data-ttu-id="7b8e4-114">Spécifiez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7b8e4-114">You can specify the following:</span></span>  
  
-   <span data-ttu-id="7b8e4-115">la fréquence de téléchargement et d'exécution du script de configuration ;</span><span class="sxs-lookup"><span data-stu-id="7b8e4-115">How often the configuration script is downloaded and run.</span></span>  
  
-   <span data-ttu-id="7b8e4-116">le délai d'attente pour le téléchargement du script ;</span><span class="sxs-lookup"><span data-stu-id="7b8e4-116">How long to wait for the script to download.</span></span>  
  
-   <span data-ttu-id="7b8e4-117">les informations d'identification que votre système doit utiliser pour accéder au proxy ;</span><span class="sxs-lookup"><span data-stu-id="7b8e4-117">Which credentials your system should use to access the proxy.</span></span>  
  
-   <span data-ttu-id="7b8e4-118">les informations d'identification que votre système doit utiliser pour télécharger le script de configuration.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-118">Which credentials your system should use to download the configuration script.</span></span>  
  
 <span data-ttu-id="7b8e4-119">Les modifications apportées à l'environnement réseau peuvent nécessiter que le système utilise un nouvel ensemble de proxies.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-119">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="7b8e4-120">En cas de défaillance d'une connexion réseau ou d'initialisation d'une nouvelle connexion réseau, le système doit détecter la source appropriée du script de configuration dans le nouvel environnement et exécuter le nouveau script.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-120">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="7b8e4-121">Le tableau suivant présente les options de configuration d'un proxy adaptatif.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-121">The following table shows configuration options for an adaptive proxy.</span></span>  
  
|<span data-ttu-id="7b8e4-122">Attribut, propriété ou paramètre de fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="7b8e4-122">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="7b8e4-123">Description</span><span class="sxs-lookup"><span data-stu-id="7b8e4-123">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|<span data-ttu-id="7b8e4-124">Temps écoulé, en secondes, entre les téléchargements du script.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-124">Elapsed time in seconds between script downloads.</span></span>|  
|`scriptDownloadTimeout`|<span data-ttu-id="7b8e4-125">Délai d'attente (en secondes) pour que le script se télécharge.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-125">Time to wait (in seconds) for the script to download.</span></span>|  
|<span data-ttu-id="7b8e4-126">`useDefaultCredentials` ou <xref:System.Net.WebProxy.UseDefaultCredentials></span><span class="sxs-lookup"><span data-stu-id="7b8e4-126">`useDefaultCredentials` or <xref:System.Net.WebProxy.UseDefaultCredentials></span></span>|<span data-ttu-id="7b8e4-127">Détermine si le système utilise les informations d'identification réseau par défaut pour accéder à un proxy.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-127">Controls whether the system uses the default network credentials to access a proxy.</span></span>|  
|`useDefaultCredentialForScriptDownload`|<span data-ttu-id="7b8e4-128">Détermine si le système utilise les informations d'identification réseau par défaut pour télécharger le script de configuration.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-128">Controls whether the system uses the default network credentials to download the configuration script.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="7b8e4-129">Détermine si les paramètres de proxy statiques (adresse de proxy, liste de contournement et contournement en local) doivent être lus depuis les paramètres de proxy Internet Explorer de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-129">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="7b8e4-130">Si cette valeur est définie sur « true », les paramètres de proxy statiques provenant d'Internet Explorer sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-130">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span><br /><br /> <span data-ttu-id="7b8e4-131">Si cette valeur est définie sur « false » ou non définie, les paramètres de proxy statiques peuvent être spécifiés dans la configuration et remplacer les paramètres de proxy Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-131">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="7b8e4-132">En outre, cette valeur doit être définie sur « false » ou ne pas être définie pour que les proxies adaptifs soient activés.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-132">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="7b8e4-133">L'exemple suivant illustre une configuration de proxy adaptatif classique.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-133">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="7b8e4-134">Proxies statiques</span><span class="sxs-lookup"><span data-stu-id="7b8e4-134">Static Proxies</span></span>  
 <span data-ttu-id="7b8e4-135">Les proxies statiques sont généralement configurés explicitement par une application, ou lorsqu'un fichier de configuration est appelé par une application ou le système.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-135">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="7b8e4-136">Les proxies statiques sont utiles dans les réseaux dans lesquels la topologie change rarement, par exemple dans le cas d'un ordinateur de bureau connecté à un réseau d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-136">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="7b8e4-137">Plusieurs options déterminent le fonctionnement d'un proxy statique.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-137">Several options control how a static proxy operates.</span></span> <span data-ttu-id="7b8e4-138">Spécifiez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7b8e4-138">You can specify the following:</span></span>  
  
-   <span data-ttu-id="7b8e4-139">l'adresse du proxy ;</span><span class="sxs-lookup"><span data-stu-id="7b8e4-139">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="7b8e4-140">si le proxy doit être ignoré pour les adresses locales ;</span><span class="sxs-lookup"><span data-stu-id="7b8e4-140">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="7b8e4-141">si le proxy doit être ignoré pour un ensemble d'adresses donné.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-141">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="7b8e4-142">Le tableau suivant présente les options de configuration d'un proxy statique.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-142">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="7b8e4-143">Attribut, propriété ou paramètre de fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="7b8e4-143">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="7b8e4-144">Description</span><span class="sxs-lookup"><span data-stu-id="7b8e4-144">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="7b8e4-145">`proxyaddress` ou <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="7b8e4-145">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="7b8e4-146">L'adresse du proxy à utiliser.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-146">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="7b8e4-147">`bypassonlocal` ou <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="7b8e4-147">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="7b8e4-148">Détermine si le proxy est ignoré pour les adresses locales.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-148">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="7b8e4-149">`bypasslist` ou <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="7b8e4-149">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="7b8e4-150">Décrit, avec des expressions régulières, un ensemble d'adresses qui ignorent le proxy.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-150">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="7b8e4-151">Détermine si les paramètres de proxy statiques (adresse de proxy, liste de contournement et contournement en local) doivent être lus depuis les paramètres de proxy Internet Explorer de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-151">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="7b8e4-152">Si cette valeur est définie sur « true », les paramètres de proxy statiques provenant d'Internet Explorer sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-152">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="7b8e4-153">Dans .NET Framework 2.0, lorsque cette valeur est définie sur « true », les paramètres de proxy Internet Explorer ne sont pas substitués par d'autres paramètres de proxy figurant dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-153">On .NET Framework 2.0 when this value is set to "true", the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="7b8e4-154">Sur .NET Framework 1.1, les paramètres de proxy Internet Explorer peuvent être substituées par d'autres paramètres de proxy figurant dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-154">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="7b8e4-155">Si cette valeur est définie sur « false » ou non définie, les paramètres de proxy statiques peuvent être spécifiés dans la configuration et remplacer les paramètres de proxy Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-155">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="7b8e4-156">En outre, cette valeur doit être définie sur « false » ou ne pas être définie pour que les proxies adaptifs soient activés.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-156">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="7b8e4-157">L'exemple suivant illustre une configuration de proxy statique classique.</span><span class="sxs-lookup"><span data-stu-id="7b8e4-157">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b8e4-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b8e4-158">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="7b8e4-159">Détection automatique de proxy</span><span class="sxs-lookup"><span data-stu-id="7b8e4-159">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
