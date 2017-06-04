---
title: "Parcours NAT avec IPv6 et Teredo | Microsoft Docs"
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
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# Parcours NAT avec IPv6 et Teredo
Il a effectué des améliorations qui prennent en charge le parcours de \(NAT\) de traduction d'adresse réseau NAT.  Ces modifications sont conçues pour une utilisation avec IPv6 et Teredo le, mais elles s'appliquent également à d'autres technologies de tunneling IP.  Ces améliorations affectent les classes dans <xref:System.Net> et les espaces de noms associés.  
  
 Ces modifications peuvent affecter les applications de client et serveur qui classent pour utiliser les technologies de tunneling IP.  
  
 Les modifications pour prendre en charge parcours NAT sont uniquement disponibles pour les applications utilisant le .NET Framework version 4.  Ces fonctionnalités sont pas disponibles dans les versions antérieures du .NET Framework.  
  
## Vue d'ensemble  
 La version 4 \(IPv4\) Internet Protocol\) a défini une adresse IPv4 comme 32 bits de temps.  Par conséquent, l'IPv4 prend environ 4 milliards de uniques adresses IP \(2^32\).  Comme un nombre d'ordinateurs et de périphériques réseau sur Internet développés en années 1990, les limites de l'espace d'adresses IPv4 sont devenues explicite.  
  
 Une plusieurs techniques utilisées pour étendre la durée de vie de l'IPv4 a été de déployer NAT pour permettre à une seule adresse IP publique unique pour représenter un grand nombre d'adresses IP privées \(intranet privé\).  Les adresses IP privées derrière le périphérique NATIONAL partagent l'adresse IPv4 publique unique.  Le périphérique NATIONAL peut être un module matériel dédié \(un point d'accès et routeur wireless moins coûteux, par exemple\) ou un ordinateur qui exécute un service pour fournir NAT.  Un périphérique ou un service de cette adresse IP publique traduit des paquets de réseau adresses d'Internet et l'intranet privé.  
  
 Cette méthode fonctionne bien pour les applications clientes qui s'exécutent sur l'intranet privé qui envoient des demandes à d'autres adresses IP \(généralement serveurs\) sur Internet.  Le périphérique ou le serveur NATIONAL peut conserver un mappage des demandes du client afin que lorsqu'une réponse est retourné sait où envoyer la réponse.  Mais ce modèle pose des problèmes pour les applications qui s'exécutent dans intranet privé derrière le périphérique NATIONAL qui veulent fournir des services, écoutent des paquets, et répondent.  C'est notamment le point de droite pour les applications peer to peer.  
  
 Le protocole d'IPv6 a défini une adresse IPv4 comme 128 bits de temps.  Par conséquent, très IPv6 prend en charge un grand espace d'adresses IP de 3,2 adresses uniques x 10^38 \(2^128\).  Avec un espace d'adressage de cette taille, il est possible pour chaque appareil connecté à Internet pour donner une adresse unique.  Mais il existe des problèmes.  Une grande partie du monde utilise toujours uniquement l'IPv4.  En particulier, plusieurs des routeurs existants et les points d'accès sans fil utilisés par les petites entreprise, d'organisations, et les ménages ne prennent pas IPv6.  Également des fournisseurs d'accès Internet qui utilisent ces clients ne prennent pas ou n'ont pas configuré la prise en charge de IPv6.  
  
 Plusieurs technologies de transition de IPv6 ont été développées pour percer un tunnel des adresses de IPv6 dans un à en\-tête pack IPv4.  Ces technologies incluent 6to4, ISATAP, et tunnels de Teredo qui fournissent l'affectation d'adresses et l'hôte\-à\- hôte tunneling automatique pour le trafic de IPv6 de monodiffusion lorsque les hôtes de IPv6 doivent parcourir les réseaux IP4 pour atteindre d'autres réseaux de IPv6.  Les packs de IPv6 sont envoyés ont percé un tunnel comme paquets IPv4.  Il utilise plusieurs techniques de tunneling qui permettent NAT parcours des adresses de IPv6 via un périphérique NATIONAL.  
  
 Le Teredo est l'une des technologies de transition de IPv6 qui apporte la connectivité de IPv6 des réseaux IPv4.  Le Teredo est documenté dans la norme RFC 4380 publiée par le groupe de travail IETF \(IETF\).  Windows XP SP2 et fournissent plus loin la prise en charge d'un adaptateur virtuel de Teredo qui peut fournir une adresse IPv6 publique dans la plage 2001:0::\/32.  Cette adresse IPv6 peut être utilisée pour écouter les connexions entrantes de Internet et peut être fournie à IPv6 a activé les clients qui souhaitent se connecter au service écoutant.  Cela libère une application de vous préoccuper de la façon de résoudre un ordinateur derrière un périphérique NATIONAL, étant donné que l'application peut simplement se connecter à celui\-ci en utilisant son adresse Teredo de IPv6.  
  
## Améliorations pour prendre en charge le parcours NAT et Teredo  
 Les améliorations sont ajoutées à <xref:System.Net>, à <xref:System.Net.NetworkInformation>, et aux espaces de noms d' <xref:System.Net.Sockets> pour prendre en charge parcours NAT à l'aide de IPv6 et le Teredo.  
  
 Plusieurs méthodes sont ajoutées à la classe d' <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=fullName> pour obtenir la liste des adresses IP unicasts sur l'hôte.  La méthode d' <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> démarre une requête asynchrone de récupérer la table d'adresses IP unicast stable sur l'ordinateur local.  La méthode d' <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> termine une requête asynchrone en attente de récupérer la table d'adresses IP unicast stable sur l'ordinateur local.  La méthode d' <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> est une requête synchrone de récupérer la table d'adresses IP unicast stable sur l'ordinateur local, qui attend jusqu'à ce que la table\) se stabilise si nécessaire.  
  
 La propriété d' <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=fullName> peut être utilisée pour déterminer si <xref:System.Net.IPAddress> est une adresse Teredo de IPv6.  
  
 À l'aide de ces nouvelles méthodes de classe d' <xref:System.Net.NetworkInformation.IPGlobalProperties> en association avec la propriété d' <xref:System.Net.IPAddress.IsIPv6Teredo%2A> permet à une application de rechercher facilement l'adresse Teredo.  Une application doit normalement seulement connaître l'adresse Teredo locale si elle communique ces informations aux applications distantes.  Par exemple, une application peer to peer peut envoyer toutes ses adresses de IPv6 à un serveur d'équivalent qui peut ensuite les envoyer vers d'autres scrute pour activer la transmission directe.  
  
 Une application doit normalement définir son service écoutant pour écouter sur <xref:System.Net.IPAddress.IPv6Any?displayProperty=fullName> plutôt que sur l'adresse Teredo locale.  Si un client distant ou un homologue a un itinéraire directe de IPv6 à l'hôte de service écoutant, le client ou l'homologue peut se connecter directement à l'aide de IPv6 et ne doit pas utiliser le Teredo pour percer un tunnel des paquets.  
  
 Pour les applications TCP, la classe d' <xref:System.Net.Sockets.TcpListener?displayProperty=fullName> a une méthode d' <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> pour activer parcours NAT.  Pour les applications d'UDP, la classe d' <xref:System.Net.Sockets.UdpClient?displayProperty=fullName> a une méthode d' <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> pour activer parcours NAT.  
  
 Pour les applications qui utilisent <xref:System.Net.Sockets.Socket?displayProperty=fullName> et les classes associées, l' <xref:System.Net.Sockets.Socket.GetSocketOption%2A> et des méthodes d' <xref:System.Net.Sockets.Socket.SetSocketOption%2A> peuvent être utilisés avec l'option de socket d' <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName> d'interroger, activer, désactiver ou parcours NAT.  
  
## Voir aussi  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName>   
 <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=fullName>