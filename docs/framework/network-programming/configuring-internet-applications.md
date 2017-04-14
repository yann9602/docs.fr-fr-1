---
title: "Configuration des applications Internet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "téléchargement de ressources Internet, proxy par défaut"
  - "envoi de données, proxy par défaut"
  - "réception de données, proxy par défaut"
  - "téléchargement de ressources Internet, configuration des applications Internet"
  - "modules propres au protocole"
  - "modules d’authentification personnalisée"
  - "réception de données, configuration des applications Internet"
  - "paramètres de configuration (.NET Framework), applications Internet"
  - "demande de données en provenance d’Internet, configuration des applications Internet"
  - "demande de données en provenance d’Internet, proxy par défaut"
  - "réponse à une demande Internet, proxy par défaut"
  - "Internet, configuration des applications Internet"
  - "réponse à une demande Internet, configuration des applications Internet"
  - "proxy par défaut"
  - "ressources réseau, proxy par défaut"
  - "envoi de données, configuration des applications Internet"
  - "ressources réseau, configuration des applications Internet"
  - "Internet, proxy par défaut"
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# Configuration des applications Internet
L'élément de configuration de [\<system.Net\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) contient les informations de configuration réseau pour les applications.  Utilisation de l'élément [\<system.Net\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) , vous pouvez définir des serveurs proxy, définissez les paramètres de gestion de connexion, puis incorporer les modules personnalisés d'identification et de demande dans votre application.  
  
 l'élément de [\<defaultProxy\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) définit le serveur proxy retourné par la classe d' `GlobalProxySelection` .  Tout <xref:System.Net.HttpWebRequest> qui n'a pas son propre jeu de propriétés d' <xref:System.Net.HttpWebRequest.Proxy%2A> sur une valeur spécifique utilise le proxy par défaut.  En plus de définir l'adresse de proxy, vous pouvez créer une liste d'adresses du serveur qui n'utilisent pas le proxy, et vous pouvez indiquer que le proxy ne doit pas être utilisé pour les adresses locales.  
  
 Il est important de noter que les paramètres de Microsoft Internet Explorer sont combinées avec les paramètres de configuration, la dernière priorité prenant.  
  
 L'exemple suivant définit l'adresse par défaut du serveur proxy à http:\/\/proxyserver, indique que le proxy ne doit pas être utilisé pour les adresses locales, et spécifie que toutes les demandes des serveurs trouvent dans le domaine de contoso.com doivent ignorer le proxy.  
  
```  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 Utilisez l'élément de [\<connectionManagement\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) pour configurer le nombre de rapports persistants qui peuvent être générés à un serveur spécifique ou à tous les autres serveurs.  L'exemple suivant configure l'application d'utiliser deux connexions persistantes au serveur www.contoso.com, quatre connexions persistantes au serveur avec l'adresse IP 192.168.1.2, et une connexion persistante à tous les autres serveurs.  
  
```  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 Les modules personnalisés d'identification sont configurés avec l'élément d' [\<authenticationModules\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) .  Les modules personnalisés d'identification doit implémenter l'interface d' <xref:System.Net.IAuthenticationModule> .  
  
 l'exemple suivant configure un module personnalisé d'authentification.  
  
```  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Vous pouvez utiliser l'élément de [\<webRequestModules\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) pour configurer votre application pour utiliser des modules spécifiques au protocole personnalisés pour demander des informations des ressources Internet.  Les modules spécifiés doivent implémenter l'interface d' <xref:System.Net.IWebRequestCreate> .  Vous pouvez substituer HTTP par défaut, S\-HTTP, et les modules de demande de fichier en spécifiant votre module personnalisé dans le fichier de configuration, comme dans l'exemple suivant.  
  
```  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## Voir aussi  
 [Programmation réseau dans le .NET Framework](../../../docs/framework/network-programming/index.md)   
 [Schéma des paramètres réseau](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<system.Net\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)