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
ms.openlocfilehash: b543097d0fc85c502bd36f22225958f9239ccd71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="proxy-configuration"></a>Configuration du proxy
Un serveur proxy gère les demandes du client pour les ressources. Un proxy peut retourner une ressource demandée à partir de son cache ou transférer la demande au serveur sur lequel réside la ressource. Les proxies peuvent améliorer les performances réseau en réduisant le nombre de demandes envoyées aux serveurs distants. Les proxies peuvent également être utilisés pour restreindre l'accès aux ressources.  
  
## <a name="adaptive-proxies"></a>Proxies adaptatifs  
 Dans le .NET Framework, les proxies sont fournis sous deux formes : adaptatifs et statiques. Les proxies adaptatifs ajustent leurs paramètres lorsque la configuration du réseau change. Par exemple, si l'utilisateur d'un ordinateur portable démarre une connexion réseau d'accès à distance, un proxy adaptatif identifie cette modification, détecte et exécute son nouveau script de configuration, et ajuste ses paramètres de façon appropriée.  
  
 Les proxys adaptatifs sont configurés par un script de configuration (voir [Détection automatique de proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)). Le script génère un ensemble de protocoles d'application et un proxy pour chaque protocole.  
  
 Plusieurs options contrôlent la façon dont le script de configuration est exécuté. Spécifiez les informations suivantes :  
  
-   la fréquence de téléchargement et d'exécution du script de configuration ;  
  
-   le délai d'attente pour le téléchargement du script ;  
  
-   les informations d'identification que votre système doit utiliser pour accéder au proxy ;  
  
-   les informations d'identification que votre système doit utiliser pour télécharger le script de configuration.  
  
 Les modifications apportées à l'environnement réseau peuvent nécessiter que le système utilise un nouvel ensemble de proxies. En cas de défaillance d'une connexion réseau ou d'initialisation d'une nouvelle connexion réseau, le système doit détecter la source appropriée du script de configuration dans le nouvel environnement et exécuter le nouveau script.  
  
 Le tableau suivant présente les options de configuration d'un proxy adaptatif.  
  
|Attribut, propriété ou paramètre de fichier de configuration|Description|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|Temps écoulé, en secondes, entre les téléchargements du script.|  
|`scriptDownloadTimeout`|Délai d'attente (en secondes) pour que le script se télécharge.|  
|`useDefaultCredentials` ou <xref:System.Net.WebProxy.UseDefaultCredentials>|Détermine si le système utilise les informations d'identification réseau par défaut pour accéder à un proxy.|  
|`useDefaultCredentialForScriptDownload`|Détermine si le système utilise les informations d'identification réseau par défaut pour télécharger le script de configuration.|  
|`usesystemdefaults`|Détermine si les paramètres de proxy statiques (adresse de proxy, liste de contournement et contournement en local) doivent être lus depuis les paramètres de proxy Internet Explorer de l'utilisateur. Si cette valeur est définie sur « true », les paramètres de proxy statiques provenant d'Internet Explorer sont utilisés.<br /><br /> Si cette valeur est définie sur « false » ou non définie, les paramètres de proxy statiques peuvent être spécifiés dans la configuration et remplacer les paramètres de proxy Internet Explorer. En outre, cette valeur doit être définie sur « false » ou ne pas être définie pour que les proxies adaptifs soient activés.|  
  
 L'exemple suivant illustre une configuration de proxy adaptatif classique.  
  
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
  
## <a name="static-proxies"></a>Proxies statiques  
 Les proxies statiques sont généralement configurés explicitement par une application, ou lorsqu'un fichier de configuration est appelé par une application ou le système. Les proxies statiques sont utiles dans les réseaux dans lesquels la topologie change rarement, par exemple dans le cas d'un ordinateur de bureau connecté à un réseau d'entreprise.  
  
 Plusieurs options déterminent le fonctionnement d'un proxy statique. Spécifiez les informations suivantes :  
  
-   l'adresse du proxy ;  
  
-   si le proxy doit être ignoré pour les adresses locales ;  
  
-   si le proxy doit être ignoré pour un ensemble d'adresses donné.  
  
 Le tableau suivant présente les options de configuration d'un proxy statique.  
  
|Attribut, propriété ou paramètre de fichier de configuration|Description|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` ou <xref:System.Net.WebProxy.Address>|L'adresse du proxy à utiliser.|  
|`bypassonlocal` ou <xref:System.Net.WebProxy.BypassProxyOnLocal>|Détermine si le proxy est ignoré pour les adresses locales.|  
|`bypasslist` ou <xref:System.Net.WebProxy.BypassArrayList>|Décrit, avec des expressions régulières, un ensemble d'adresses qui ignorent le proxy.|  
|`usesystemdefaults`|Détermine si les paramètres de proxy statiques (adresse de proxy, liste de contournement et contournement en local) doivent être lus depuis les paramètres de proxy Internet Explorer de l'utilisateur. Si cette valeur est définie sur « true », les paramètres de proxy statiques provenant d'Internet Explorer sont utilisés. Dans .NET Framework 2.0, lorsque cette valeur est définie sur « true », les paramètres de proxy Internet Explorer ne sont pas substitués par d'autres paramètres de proxy figurant dans le fichier de configuration. Sur .NET Framework 1.1, les paramètres de proxy Internet Explorer peuvent être substituées par d'autres paramètres de proxy figurant dans le fichier de configuration.<br /><br /> Si cette valeur est définie sur « false » ou non définie, les paramètres de proxy statiques peuvent être spécifiés dans la configuration et remplacer les paramètres de proxy Internet Explorer. En outre, cette valeur doit être définie sur « false » ou ne pas être définie pour que les proxies adaptifs soient activés.|  
  
 L'exemple suivant illustre une configuration de proxy statique classique.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [Détection automatique de proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)
