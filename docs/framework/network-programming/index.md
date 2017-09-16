---
title: "Programmation réseau dans le .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
caps.latest.revision: 24
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4b63aeadb795e5457266bd75d1f2bf0e695eac7f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="network-programming-in-the-net-framework"></a>Programmation réseau dans le .NET Framework
Microsoft .NET Framework fournit une implémentation en couche, extensible et managée des services Internet que vous pouvez intégrer rapidement et facilement à vos applications. Les applications réseau peuvent générer des protocoles enfichables pour tirer parti automatiquement de nouveaux protocoles Internet, ou elles peuvent utiliser une implémentation managée de l'interface Windows Socket pour fonctionner au niveau du socket.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Introduction aux protocoles enfichables](../../../docs/framework/network-programming/introducing-pluggable-protocols.md)  
 Décrit comment accéder à une ressource réseau sans tenir compte du protocole d'accès dont elle a besoin.  
  
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)  
 Explique comment utiliser des protocoles enfichables pour charger et télécharger les données à partir des ressources Internet.  
  
 [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 Explique comment dériver les classes spécifiques au protocole pour implémenter des protocoles enfichables.  
  
 [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)  
 Décrit les applications de programmation qui tirent parti des protocoles réseau comme TCP, UDP, et HTTP.  
  
 [Protocole IPv6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 Décrit les avantages du protocole IPv6 (Internet Protocol version 6) par rapport à la version actuelle de la suite des protocoles Internet (IPv4), décrit l’adressage IPv6, le routage et la configuration automatique, et comment activer et désactiver IPv6.  
  
 [Configuration des applications Internet](../../../docs/framework/network-programming/configuring-internet-applications.md)  
 Explique comment utiliser les fichiers de configuration .NET Framework pour configurer les applications Web.  
  
 [Traçage réseau dans .NET Framework](../../../docs/framework/network-programming/network-tracing.md)  
 Explique comment utiliser le traçage réseau pour obtenir des informations sur les appels de méthode et le trafic réseau généré par une application managée.  
  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 Décrit comment utiliser la mise en cache pour les applications qui utilisent les classes <xref:System.Net.WebClient?displayProperty=fullName>, <xref:System.Net.WebRequest?displayProperty=fullName>et <xref:System.Net.HttpWebRequest?displayProperty=fullName> .  
  
 [Sécurité dans la programmation réseau](../../../docs/framework/network-programming/security-in-network-programming.md)  
 Explique comment utiliser des techniques standard de sécurité Internet et d'authentification.  
  
 [Bonnes pratiques pour les classes System.Net](../../../docs/framework/network-programming/best-practices-for-system-net-classes.md)  
 Fournit des conseils et des astuces pour profiter au mieux de vos applications Web.  
  
 [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 Décrit comment configurer des proxies.  
  
 [NetworkInformation](../../../docs/framework/network-programming/networkinformation.md)  
 Explique comment collecter des informations sur les événements, les modifications, les statistiques et les propriétés réseau et explique également comment déterminer si un hôte distant est accessible ou non à l'aide de la classe <xref:System.Net.NetworkInformation.Ping?displayProperty=fullName> .  
  
 [Modifications apportées à l’espace de noms System.Uri dans la version 2.0](../../../docs/framework/network-programming/changes-to-the-system-uri-namespace-in-version-2-0.md)  
 Décrit plusieurs modifications apportées à la classe <xref:System.Uri?displayProperty=fullName> dans la version 2.0 pour corriger les comportements incorrects, améliorer la convivialité et la sécurité.  
  
 [Prise en charge de l’identificateur de ressource internationalisée (IRI) dans System.Uri](../../../docs/framework/network-programming/international-resource-identifier-support-in-system-uri.md)  
 Décrit les améliorations apportées à la classe <xref:System.Uri?displayProperty=fullName> dans la version 3.5, 3.0 SP1, et 2.0 SP1 pour la prise en charge de l'identifiant de ressource internationalisée et du nom de domaine internationalisé.  
  
 [Améliorations des performances de socket dans la version 3.5](../../../docs/framework/network-programming/socket-performance-enhancements-in-version-3-5.md)  
 Décrit un ensemble d'améliorations apportées à la classe <xref:System.Net.Sockets.Socket?displayProperty=fullName> dans la version 3.5, 3.0 SP1 et 2.0 SP1 qui fournit un autre modèle asynchrone pouvant être utilisé par les applications de socket spécialisées très performantes.  
  
 [Protocole PNRP](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)  
 Décrit l’ajout de la prise en charge à la version 3.5 pour prendre en charge le protocole PNRP (Peer Name Resolution Protocol), une inscription de noms dynamiques et sans serveur et un protocole de résolution de noms. Ces nouvelles fonctionnalités sont prises en charge par l'espace de noms <xref:System.Net.PeerToPeer?displayProperty=fullName> .  
  
 [Collaboration pair à pair](../../../docs/framework/network-programming/peer-to-peer-collaboration.md)  
 Décrit l'ajout de la prise en charge à la version 3.5 pour prendre en charge la collaboration pair à pair qui s'appuie sur PNRP. Ces nouvelles fonctionnalités sont prises en charge par l'espace de noms <xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName> .  
  
 [Changements apportés à l’authentification NTLM pour HttpWebRequest dans la version 3.5 SP1](../../../docs/framework/network-programming/changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 Décrit les changements de sécurité apportés à la version 3.5 SP1 qui affectent la manière dont l'intégration de l'authentification Windows est gérée par <xref:System.Net.HttpWebRequest?displayProperty=fullName>, <xref:System.Net.HttpListener?displayProperty=fullName>, <xref:System.Net.Security.NegotiateStream?displayProperty=fullName>, et les classes associées dans l'espace de noms System.Net.  
  
 [Authentification Windows intégrée avec protection étendue](../../../docs/framework/network-programming/integrated-windows-authentication-with-extended-protection.md)  
 Décrit les améliorations de la protection étendue qui affectent la manière dont l'authentification Windows intégrée est gérée par <xref:System.Net.HttpWebRequest?displayProperty=fullName>, <xref:System.Net.HttpListener?displayProperty=fullName>, <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>, <xref:System.Net.Security.SslStream?displayProperty=fullName>, <xref:System.Net.Security.NegotiateStream?displayProperty=fullName>, et les classes associées dans <xref:System.Net?displayProperty=fullName> et les espaces de noms associés.  
  
 [Parcours NAT avec IPv6 et Teredo](../../../docs/framework/network-programming/nat-traversal-using-ipv6-and-teredo.md)  
 Décrit les améliorations apportées aux espaces de noms <xref:System.Net?displayProperty=fullName>, <xref:System.Net.NetworkInformation?displayProperty=fullName>, et <xref:System.Net.Sockets?displayProperty=fullName> pour prendre en charge le parcours NAT avec IPv6 et Teredo.  
  
 [Isolement réseau pour les applications du Windows Store](../../../docs/framework/network-programming/network-isolation-for-windows-store-apps.md)  
 Décrit l'impact de l'isolement réseau lorsque les classes des espaces de noms <xref:System.Net>, <xref:System.Net.Http>, et <xref:System.Net.Http.Headers> sont utilisées dans les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] .  
  
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)  
 Liens vers des exemples téléchargeables de programmation qui utilisent des classes dans les espaces de noms <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> .  
  
## <a name="reference"></a>Référence  
 <xref:System.Net?displayProperty=fullName>  
 Constitue une interface de programmation simple pour un grand nombre des protocoles réseau employés aujourd'hui. Les classes <xref:System.Net.WebRequest?displayProperty=fullName> et <xref:System.Net.WebResponse?displayProperty=fullName> de cet espace de noms servent de base aux protocoles enfichables.  
  
 <xref:System.Net.Cache?displayProperty=fullName>  
 Définit les types et les énumérations utilisés pour définir des stratégies de cache applicables aux ressources et obtenus via l'utilisation des classes <xref:System.Net.WebRequest?displayProperty=fullName> et <xref:System.Net.HttpWebRequest?displayProperty=fullName> .  
  
 <xref:System.Net.Configuration?displayProperty=fullName>  
 Classes utilisées par les applications pour accéder et mettre à jour par programmation des paramètres de configuration pour les espaces de noms System.Net.  
  
 <xref:System.Net.Http?displayProperty=fullName>  
 Classes qui fournissent une interface de programmation pour les applications HTTP modernes.  
  
 <xref:System.Net.Http.Headers?displayProperty=fullName>  
 Prend en charge les collections d'en-têtes HTTP utilisés par l'espace de noms <xref:System.Net.Http?displayProperty=fullName>  
  
 <xref:System.Net.Mail?displayProperty=fullName>  
 Classes pour composer et envoyer des messages à l'aide du protocole SMTP.  
  
 <xref:System.Net.Mime?displayProperty=fullName>  
 Définit les types utilisés pour représenter les en-têtes MIME (Multipurpose Internet Mail Exchange) utilisés par les classes de l'espace de noms <xref:System.Net.Mail?displayProperty=fullName> .  
  
 <xref:System.Net.NetworkInformation?displayProperty=fullName>  
 Classes permettant de recueillir des informations par programmation sur les événements, les modifications, des statistiques et les propriétés réseau.  
  
 <xref:System.Net.PeerToPeer?displayProperty=fullName>  
 Fournit une implémentation managée du protocole PNRP (Peer Name Resolution Protocol) pour les développeurs.  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName>  
 Fournit une implémentation managée de l'interface de collaboration pair à pair aux développeurs.  
  
 <xref:System.Net.Security?displayProperty=fullName>  
 Classes pour fournir des flux de réseau pour des communications sécurisées entre les hôtes.  
  
 <xref:System.Net.Sockets?displayProperty=fullName>  
 Fournit une implémentation managée de l'interface Windows Sockets (Winsock) pour les développeurs qui doivent aider à contrôler étroitement l'accès au réseau.  
  
 <xref:System.Net.WebSockets?displayProperty=fullName>  
 Fournit une implémentation managée de l'interface WebSocket pour les développeurs.  
  
 <xref:System.Uri?displayProperty=fullName>  
 Fournit une représentation objet d'un URI (Uniform Resource Identifier) et un accès simplifié aux parties de l'identificateur.  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=fullName>  
 Fournit un support pour l'authentification à l'aide de la protection étendue pour les applications.  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=fullName>  
 Fournit un support pour la configuration de l'authentification à l'aide de la protection étendue pour les applications.  
  
## <a name="see-also"></a>Voir aussi  
 [Guides pratiques relatifs à la programmation réseau](../../../docs/framework/network-programming/network-programming-how-to-topics.md)   
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)   
 [Exemples de mise en réseau pour .NET dans MSDN Code Gallery](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)   
 [Exemple HttpClient](http://go.microsoft.com/fwlink/?LinkId=242550)

