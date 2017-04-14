---
title: "Changements apport&#233;s &#224; l’authentification NTLM pour HttpWebRequest dans la version&#160;3.5 SP1 | Microsoft Docs"
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
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# Changements apport&#233;s &#224; l’authentification NTLM pour HttpWebRequest dans la version&#160;3.5 SP1
Les modifications de sécurité ont été apportées dans le .NET Framework version 3.5 SP1 et ultérieurement cet affectent la façon dont l'authentification Windows intégrée est gérée par <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Security.NegotiateStream>, et les classes associées dans l'espace de noms System.Net.  Ces modifications peuvent affecter les applications qui utilisent ces classes pour faire des demandes de site Web et de recevoir des réponses où l'authentification Windows intégrée basée sur NTLM est utilisée.  Cette modification peut exécuter les serveurs Web et des applications clientes qui sont configurés pour utiliser l'authentification Windows intégrée.  
  
## Vue d'ensemble  
 La conception de l'authentification Windows intégrée permet à des réponses informations d'identification sont universelle, ce qui signifie qu'il peut être réutilisée ou effectue le suivi.  Si cette fonctionnalité de création particulière n'est pas exigée, les fournisseurs d'authentification doivent diffuser des informations spécifiques cibles de informations spécifiques ainsi que de canal.  Les services peuvent ensuite assurer la protection étendue pour garantir que les réponses informations d'identification contiennent des informations spécifiques de service telles qu'un nom de clé du service \(SPN\).  Avec ces informations dans les échanges d'identification, les services peuvent mieux protéger contre une utilisation malveillante des réponses informations d'identification qui auraient pu être obtenues incorrectement.  
  
 Plusieurs composants dans <xref:System.Net> et les espaces de noms d' <xref:System.Net.Security> exécutent l'authentification Windows intégrée de la part d'une application appelante.  Cette section décrit les composants de System.Net pour ajouter une protection étendue dans leur utilisation de l'authentification Windows intégrée.  
  
## Modifications  
 La procédure d'authentification NTLM utilisée avec l'authentification Windows intégrée inclut un défi émise par l'ordinateur de destination et en arrière envoyé à l'ordinateur client.  Lorsqu'un ordinateur reçoit un défi qu'il est généré, l'authentification échoue à moins que la connexion soit une connexion de réalimentation \(adresse IPv4 127.0.0.1, par exemple\).  
  
 En accédant à un test de service sur un serveur Web interne, il est courant pour accéder au service à l'aide d'une URL semblable à http:\/\/contoso\/service ou https:\/\/contoso\/service.  Le nom « contoso » n'est souvent pas le nom d'ordinateur de l'ordinateur sur lequel le service est déployé.  <xref:System.Net> et le support relatifs aux espaces de noms à l'aide de active directory, DNS, NetBIOS, le fichier des hôtes de l'ordinateur local \(en général WINDOWS\\system32\\drivers\\etc\\hosts,  par exemple,\) ou le fichier lmhosts de l'ordinateur local \(en général WINDOWS\\system32\\drivers\\etc\\lmhosts, par exemple\) pour résoudre les noms des adresses.  Le nom « contoso » est résolu afin que les demandes envoyées à « contoso » soient envoyées au serveur approprié.  
  
 Une fois configuré pour les grands déploiements, il est également fréquent qu'un nom de serveur virtuel unique soit spécifié au déploiement avec les noms de l'ordinateur sous\-jacents jamais utilisés par les applications clientes et des utilisateurs finaux.  Par exemple, vous pouvez appeler le serveur www.contoso.com, mais dans une utilisation « contoso » réseau interne uniquement.  Ce nom est appelé l'en\-tête d'hôte dans la requête cliente de site Web.  Comme spécifié par le protocole HTTP, le champ d'en\-tête de demande hôte spécifie l'hôte Internet et le numéro de port de la ressource est demandée.  Ces informations sont obtenues à partir de l'URI d'origine fourni par l'utilisateur ou consultant la ressource \(généralement une URL HTTP\).  Dans le .NET Framework version 4, ces informations peuvent également être définies par le client à l'aide de la nouvelle propriété d' <xref:System.Net.HttpWebRequest.Host%2A> .  
  
 La classe d' <xref:System.Net.AuthenticationManager> contrôle des composants managés d'authentification \(« module »\) utilisés par des classes dérivées d' <xref:System.Net.WebRequest> et la classe d' <xref:System.Net.WebClient> .  La classe d' <xref:System.Net.AuthenticationManager> fournit une propriété qui expose un objet d' <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=fullName> , indexée par la chaîne d'URI, car les applications de fournir une chaîne de le personnalisé SPN à utiliser pendant l'authentification.  
  
 La version 3.5 SP1 spécifie maintenant par défaut le nom d'hôte de l'URL de demande dans le SPN lors de l'échange d'authentification NTLM \(NT LAN Manager\) si la propriété <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> n'est pas définie.  Le nom d'hôte utilisé dans l'URL de requête peut être différent de l'en\-tête de l'hôte spécifié dans <xref:System.Net.HttpRequestHeader?displayProperty=fullName> dans la demande du client.  Le nom d'hôte utilisé dans l'URL de requête peut être différent du nom d'hôte réel du serveur, le nom d'ordinateur du serveur, l'adresse IP de l'ordinateur ou l'adresse de bouclage.  Dans ces cas, Windows échouera la demande d'authentification.  Pour résoudre le problème, nous devons informer les fenêtres que le nom d'hôte utilisé dans l'URL de requête dans la requête du client \(« contoso », par exemple\) est en réalité un autre nom de l'ordinateur local.  
  
 Il existe plusieurs méthodes possibles pour application serveur de contourner cette modification.  L'approche recommandée consiste à mapper le nom d'hôte utilisé dans l'URL de requête à la clé d' `BackConnectionHostNames` dans le Registre sur le serveur.  La clé de Registre d' `BackConnectionHostNames` est généralement utilisée pour mapper un nom d'hôte à une adresse de réalimentation.  Les étapes sont répertoriées ci\-dessous.  
  
 Pour spécifier les noms d'hôte qui sont mappés vers l'adresse de réalimentation et peuvent se connecter aux sites Web hébergés sur un ordinateur local, suivez ces étapes :  
  
 1.  Cliquez sur Démarrer, sur Exécuter, tapez regedit, puis cliquez sur OK.  
  
 2.  Dans l'éditeur du registre, recherchez et sélectionnez la clé de Registre suivante :  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`  
  
 3.  Cliquez avec le bouton droit sur MSV1\_0, pointez sur nouveau, puis cliquez sur la valeur de plusieurs Chaîne.  
  
 4.  Tapez `BackConnectionHostNames`, puis appuyez sur ENTRÉE.  
  
 5.  Cliquez avec le bouton droit sur `BackConnectionHostNames`, puis cliquez sur modifier.  
  
 6.  Dans la zone de données valeur, tapez le nom d'hôte ou les noms d'hôte pour les sites \(le nom d'hôte utilisé dans l'URL de la requête\) qui sont sur l'ordinateur local, puis cliquez sur OK.  
  
 7.  Quittez l'éditeur du registre, puis redémarrez le service et le passage IISReset d'IISAdmin.  
  
 Un travail moins sécurisé est autour de désactiver le contrôle de réalimentation, comme décrit dans [http:\/\/support.microsoft.com\/kb\/896861](http://go.microsoft.com/fwlink/?LinkID=179657).  Cela désactive la protection contre les attaques de réflexion.  Il vaut mieux contraindre le jeu d'autres noms uniquement à ceux que vous attendez que l'ordinateur utilise réellement.  
  
## Voir aussi  
 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=fullName>   
 <xref:System.Net.HttpRequestHeader?displayProperty=fullName>   
 <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=fullName>