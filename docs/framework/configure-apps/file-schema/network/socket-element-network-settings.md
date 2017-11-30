---
title: "&lt;socket&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3d1adc163e889a0de6ad27347c8f122ac26d3524
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsocketgt-element-network-settings"></a>&lt;socket&gt; élément (paramètres réseau)
Spécifie si les opérations de socket utilisent des ports de terminaison.  
  
 \<configuration>  
\<System.NET >  
\<Paramètres >  
\<Socket >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|Indique si le socket doit toujours utiliser des ports de terminaison pour accepter les appels de méthode. La valeur par défaut est `false`.|  
|`alwaysUseCompletionPortsForConnect`|Indique si le socket doit toujours utiliser des ports de terminaison pour les appels de méthode de connexion. La valeur par défaut est `false`.|  
|`ipProtectionLevel`|Spécifie la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> à utiliser pour un socket. La valeur par défaut dépend de la version de Windows.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[Paramètres](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configure les options réseau de base pour l’espace de noms <xref:System.Net>.|  
  
## <a name="remarks"></a>Remarques  
 Le `alwaysUseCompletionPortsForAccept` et `alwaysUseCompletionPortsForConnect` attributs sont utilisés pour spécifier le comportement par défaut concernant l’utilisation de ports de terminaison par les classes dans le <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace. Ports de terminaison sont recommandés pour les applications de serveur hautes performances.  
  
 La valeur par défaut pour le `alwaysUseCompletionPortsForAccept` et `alwaysUseCompletionPortsForConnect` attributs est **false**.  
  
 Le <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> peut être utilisé pour obtenir la valeur actuelle de la `alwaysUseCompletionPortsForAccept` attribut à partir des fichiers de configuration applicables. Le <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> peut être utilisé pour obtenir la valeur actuelle de la `alwaysUseCompletionPortsForConnect` attribut à partir des fichiers de configuration applicables.  
  
 Le `ipProtectionLevel` attribut spécifie la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> à utiliser pour un socket. Le <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriété permet la configuration d’une restriction pour un socket IPv6 à une portée spécifiée, telles que les adresses avec le même lien locales préfixe ou de site local. Cette option permet aux applications de placer des restrictions d’accès sur les sockets IPv6. Ces restrictions permettent à une application qui s'exécute sur un réseau local privé de se renforcer facilement et efficacement contre les attaques externes. Cette option élargit ou limite la portée d’un socket en écoute, permettant l’accès illimité des utilisateurs publics et privés le cas échéant, ou restreindre l’accès au même site, en fonction des besoins.  
  
 Cela `ipProtectionLevel` paramètre d’attribut affecte uniquement le trafic entrant initial :  
  
-   Un serveur TCP à l’écoute les connexions entrantes sur un socket.  
  
-   Application UDP qui reçoit un paquet sur un socket.  
  
 Ce paramètre de configuration n’affecte pas les connexions TCP déjà établies (le trafic n’est pas restreint dans les deux directions) et n’affecte pas une application envoie des paquets UDP.  
  
 Les valeurs possibles pour le `ipProtectionLevel` paramètre d’attribut correspondent aux niveaux de protection définis spécifiés dans le <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> énumération comme suit :  
  
|**Valeur d’attribut**|**Description**|  
|-|-|  
|EdgeRestricted|Le niveau de protection IP est limité à un périmètre. Cette valeur peut être utilisée par les applications conçues pour fonctionner sur Internet. Ce paramètre n’autorise pas de parcours de traduction d’adresses réseau (NAT) à l’aide de l’implémentation de Windows Teredo. Ces applications peuvent contourner les pare-feux IPv4, donc les applications doivent être protégées contre les attaques Internet dirigées vers le port ouvert. Sur Windows Server 2003 et Windows XP, la valeur par défaut pour le niveau de Protection IP sur un socket est limité à un périmètre.|  
|Restreint|Le niveau de protection IP est limité. Cette valeur peut être utilisée par les applications intranet qui n’implémentent pas de scénarios Internet. Ces applications sont généralement pas testées ou renforcées contre les attaques de type Internet. Ce paramètre limite le trafic reçu aux liens locaux uniquement.|  
|Non restreint|Le niveau de protection IP est illimité. Cette valeur peut être utilisée par les applications conçues pour fonctionner sur Internet, notamment les applications qui tirent parti des fonctionnalités de traversée NAT IPv6 intégrées à Windows (Teredo, par exemple). Ces applications peuvent contourner les pare-feux IPv4, donc les applications doivent être protégées contre les attaques Internet dirigées vers le port ouvert. Sur Windows Server 2008 R2 et Windows Vista, la valeur par défaut pour le niveau de Protection IP sur un socket est illimitée.|  
|Non spécifié|Le niveau de protection IP n’est pas spécifié. Sur Windows 7 et Windows Server 2008 R2, la valeur par défaut pour le niveau de Protection IP sur un socket n’est pas spécifiée.|  
  
 La valeur par défaut pour le `ipProtectionLevel` attribut est **Unspecified**.  
  
 Le <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriété peut être utilisée pour obtenir la valeur actuelle de la `ipProtectionLevel` attribut à partir des fichiers de configuration applicables.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier que les ports de terminaison doivent être utilisés et que la valeur par défaut <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> doit être non restreint.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
