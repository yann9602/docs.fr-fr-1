---
title: "&lt;network&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#network"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<network> (élément)"
  - "network (élément)"
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;network&gt;, &#233;l&#233;ment (param&#232;tres r&#233;seau)
Configure les options réseau pour un serveur SMTP \(Simple Mail Transport Protocol\).  
  
## Syntaxe  
  
```  
  
      <network  
  clientDomain="string"   
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"   
  password="string"  
  port="integer"   
  targetName="string"  
  userName="string"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`clientDomain`|Spécifie le nom de domaine client à utiliser dans la requête initiale de protocole SMTP pour se connecter au serveur de messagerie SMTP.  La valeur par défaut est le nom du localhost de l'ordinateur local qui envoie la demande.|  
|`defaultCredentials`|Spécifie si les informations d'identification de l'utilisateur par défaut doivent être utilisées pour accéder au serveur de messagerie SMTP pour les transactions SMTP.  La valeur par défaut est `false`.|  
|`enableSsl`|Spécifie si SSL est utilisé pour accéder à un serveur de messagerie SMTP.  La valeur par défaut est `false`.|  
|`host`|Spécifie le nom d'hôte du serveur de messagerie SMTP à utiliser pour les transactions SMTP.  Cet attribut n'a pas de valeur par défaut.|  
|`password`|Spécifie le mot de passe à utiliser pour l'authentification au serveur de messagerie SMTP.  Cet attribut n'a pas de valeur par défaut.|  
|`port`|Spécifie le numéro de port à utiliser pour se connecter au serveur de messagerie SMTP.  La valeur par défaut est 25.|  
|`targetName`|Spécifie le nom du fournisseur de services à utiliser pour l'authentification lors de l'utilisation de la protection étendue pour les transactions SMTP.  Cet attribut n'a pas de valeur par défaut.|  
|`userName`|Spécifie le nom d'utilisateur à utiliser pour l'authentification au serveur de messagerie SMTP.  Cet attribut n'a pas de valeur par défaut.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<smtp\>, élément \(paramètres réseau\)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Configure les options d'envoi du courrier SMTP.|  
  
## Notes  
 Certains serveurs SMTP requièrent que vous vous authentifiiez auprès du serveur avant utilisation.  Si vous souhaitez vous authentifier à l'aide des informations d'identification réseau par défaut sur votre hôte, affectez à l'attribut `defaultCredentials` la valeur `true`.  La propriété <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=fullName> peut être utilisée pour obtenir la valeur actuelle de l'attribut `defaultCredentials` de fichiers de configuration applicables.  
  
 Vous pouvez également utiliser l'authentification de base \(un nom d'utilisateur et un mot de passe\) pour vous authentifier auprès du serveur SMTP.  Pour utiliser cette option, vous devez spécifier un nom d'utilisateur et un mot de passe valides pour le serveur SMTP spécifié.  
  
> [!NOTE]
>  L'authentification de base envoie les valeurs `userName` et `password` non chiffrées au serveur.  Quiconque contrôlant le trafic réseau peut consulter vos informations d'identification et les utiliser pour se connecter au serveur.  Vous devez utiliser un mécanisme d'authentification plus sécurisé, tel que Kerberos ou NT LAN Manager \(NTLM\). Si `defaultCredentials` a la valeur `true`, Kerberos ou NTLM sera utilisé, à condition que le serveur prenne en charge ces protocoles.  
  
 Les options des informations d'identification réseau par défaut et de l'authentification de base par défaut sont mutuellement exclusives ; si vous affectez à `defaultCredentials` la valeur `true` et spécifiez un nom d'utilisateur ainsi qu'un mot de passe, les informations d'identification réseau par défaut sont utilisées et les données de l'authentification de base sont ignorées.  
  
 Pour l'authentification de base si vous spécifiez un `userName`, vous devez également spécifier un `password` à l'authentification de vous\-même au serveur de messagerie.  
  
 La propriété <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=fullName> peut être utilisée pour obtenir la valeur actuelle de l'attribut `userName` de fichiers de configuration applicables.  La propriété <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=fullName> peut être utilisée pour obtenir la valeur actuelle de l'attribut `password` de fichiers de configuration applicables.  Un attribut `password` ne serait pas entré normalement pour des raisons de sécurité dans les fichiers de configuration.  
  
 L'attribut `clientDomain` modifie le nom de domaine client utilisé dans la requête initiale de protocole SMTP à un serveur SMTP.  L'attribut `clientDomain` peut avoir pour valeur le nom de domaine complet de l'ordinateur local, plutôt que le nom du localhost utilisé par défaut.  Cela fournit une conformité supérieure aux normes de protocole SMTP.  La valeur par défaut est le nom du localhost de l'ordinateur local qui envoie la demande.  La propriété <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=fullName> peut être utilisée pour obtenir la valeur actuelle de l'attribut `clientDomain` de fichiers de configuration applicables.  
  
 L'attribut `targetName` est utilisé pour l'authentification lors de l'utilisation de la protection étendue.  La valeur par défaut se présente sous la forme "SMTPSVC\/\<hôte\>" où \<hôte\> représente le nom d'hôte du serveur de messagerie SMTP.  La propriété <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=fullName> peut être utilisée pour obtenir la valeur actuelle de l'attribut `targetName` de fichiers de configuration applicables.  
  
 L'attribut `enableSsl` spécifie si la couche SSL est utilisée pour accéder à un serveur de messagerie SMTP.  La classe <xref:System.Net.Mail.SmtpClient?displayProperty=fullName> prend en charge seulement l'Extension de service SMTP pour SMTP sécurisé sur le protocole TLS comme défini dans RFC 3207.  Dans ce mode, la session SMTP commence sur un canal non chiffré, puis, une commande STARTTLS est émise par le client au serveur pour basculer vers la communication sécurisée à l'aide de SSL.  Consultez la RFC 3207 publiée par l'Internet Engineering Task Force \(IETF\) pour plus d'informations.  
  
 Une autre méthode de connexion consiste à établir une session SSL en amont avant l'envoi de toute commande de protocole.  Cette méthode de connexion est quelquefois appelée SMTPS et utilise par défaut le port 465.  Cette autre méthode de connexion à l'aide de SSL n'est pas prise en charge actuellement.  
  
 La propriété <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=fullName> peut être utilisée pour obtenir la valeur actuelle de l'attribut `enableSsl` de fichiers de configuration applicables.  
  
## Exemple  
 L'exemple de code suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l'aide des informations d'identification réseau par défaut.  
  
```  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=fullName>   
 <xref:System.Net.Configuration.SmtpSection?displayProperty=fullName>   
 <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>   
 [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)