---
title: "&lt;socket&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#socket"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<socket> (élément)"
  - "socket (élément)"
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
caps.latest.revision: 21
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 21
---
# &lt;socket&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Spécifie si les opérations de socket utilisent des ports de terminaison.  
  
## Syntaxe  
  
```  
  
      <socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel ="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/socket>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|**Attribut**|**Description**|  
|------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|Indique si le socket doit toujours utiliser des ports de terminaison pour les appels à la méthode Accept.  La valeur par défaut est `false`.|  
|`alwaysUseCompletionPortsForConnect`|Indique si le socket doit toujours utiliser des ports de terminaison pour les appels à la méthode Connect.  La valeur par défaut est `false`.|  
|`ipProtectionLevel`|Spécifie le <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> par défaut à utiliser pour un socket.  La valeur par défaut dépend de la version de Windows.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[paramètres](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configure les options réseau de base pour l'espace de noms <xref:System.Net>.|  
  
## Notes  
 Les attributs `alwaysUseCompletionPortsForConnect` et `alwaysUseCompletionPortsForAccept` sont utilisés pour spécifier le comportement par défaut concernant l'utilisation de ports de terminaison par les classes dans <xref:System.Net.Sockets?displayProperty=fullName>.namespace.  Les ports de terminaison sont recommandés pour les applications serveur hautement performantes.  
  
 La valeur par défaut pour les attributs `alwaysUseCompletionPortsForAccept` et `alwaysUseCompletionPortsForConnect` est **false**.  
  
 La propriété <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> peut être utilisée pour obtenir la valeur actuelle de l'attribut `alwaysUseCompletionPortsForAccept` de fichiers de configuration applicables.  La propriété <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> peut être utilisée pour obtenir la valeur actuelle de l'attribut `alwaysUseCompletionPortsForConnect` de fichiers de configuration applicables.  
  
 L'attribut `ipProtectionLevel` spécifie le <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> par défaut à utiliser pour un socket.  La propriété <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> permet la configuration d'une restriction pour un socket IPv6 à une portée spécifiée, telle que les adresses avec le même préfixe de lien local ou site local.  Cette option permet aux applications de placer des restrictions d'accès sur les sockets IPv6.  Ces restrictions permettent à une application qui s'exécute sur un réseau local privé de se renforcer facilement et efficacement contre les attaques externes.  Cette option étend ou limite la portée d'un socket d'écoute, en permettant l'accès illimité des utilisateurs privés et publics lorsque cela s'avère nécessaire ou en restreignant uniquement l'accès au même site, comme requis.  
  
 Ce paramètre d'attribut `ipProtectionLevel` affecte le trafic entrant initial uniquement :  
  
-   Serveur TCP qui écoute des connexions entrantes sur un socket.  
  
-   Application UDP qui reçoit un paquet sur un socket.  
  
 Ce paramètre de configuration n'affecte pas les connexions TCP déjà établies \(le trafic n'est pas restreint dans les deux directions\) et n'affecte pas une application qui envoie des paquets UDP.  
  
 Les valeurs possibles pour le paramètre de l'attribut `ipProtectionLevel` correspondent aux niveaux de protection définis spécifiés dans l'énumération <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> comme suit :  
  
|||  
|-|-|  
|**Valeur d'attribut**|**Description**|  
|EdgeRestricted|Le niveau de protection IP est limité à un périmètre donné.  Cette valeur peut être utilisée par les applications conçues pour fonctionner sur Internet.  Ce paramètre n'autorise pas la traversée du traducteur d'adresses réseau \(NAT\) à l'aide de l'implémentation de Windows Teredo.  Ces applications peuvent contourner les pare\-feux IPv4 ; elles doivent donc être renforcées contre les attaques Internet dirigées sur le port ouvert.  Sous Windows Server 2003 et Windows XP, la valeur par défaut pour le niveau de protection IP sur un socket est Périmètre limité.|  
|Restricted|Le niveau de protection IP est limité.  Cette valeur peut être utilisée par les applications intranet qui n'implémentent pas de scénarios Internet.  Ces applications ne sont généralement pas testées ou renforcées contre les attaques Internet.  Ce paramètre limitera uniquement le trafic reçu aux liens locaux.|  
|Non restreint|Le niveau de protection IP est illimité.  Cette valeur peut être utilisée par les applications conçues pour fonctionner sur Internet, notamment les applications qui tirent parti des fonctions de traversée NAT IPv6 intégrées à Windows \(Teredo, par exemple\).  Ces applications peuvent contourner les pare\-feux IPv4 ; elles doivent donc être renforcées contre les attaques Internet dirigées sur le port ouvert.  Sous Windows Server 2008 R2 et Windows Vista, la valeur par défaut pour le niveau de protection IP sur un socket est illimitée.|  
|Non spécifié|Le niveau de protection IP n'est pas spécifié.  Sous Windows 7 et Windows Server 2008 R2, la valeur par défaut pour le niveau de protection IP sur un socket n'est pas spécifiée.|  
  
 La valeur par défaut pour l'attribut `ipProtectionLevel` est **Non spécifié**.  
  
 La propriété <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> peut être utilisée pour obtenir la valeur actuelle de l'attribut `ipProtectionLevel` de fichiers de configuration applicables.  
  
## Fichiers de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application ou dans le fichier de configuration machine \(Machine.config\).  
  
## Exemple  
 L'exemple de code suivant indique comment spécifier que les ports de terminaison doivent être utilisés et que le <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> par défaut ne doit pas être restreint.  
  
```  
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
  
## Voir aussi  
 <xref:System.Net?displayProperty=fullName>   
 <xref:System.Net.Configuration.SocketElement?displayProperty=fullName>   
 <xref:System.Net.Sockets?displayProperty=fullName>   
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName>   
 <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)