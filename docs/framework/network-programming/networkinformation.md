---
title: "NetworkInformation | Microsoft Docs"
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
  - "Réseau"
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# NetworkInformation
L'espace de noms d' <xref:System.Net.NetworkInformation> vous permet de collecter des informations sur des événements, des modifications, les compléments, les propriétés et du réseau.  Vous pouvez également déterminer si un hôte distant est accessible à l'aide de la classe d' <xref:System.Net.NetworkInformation.Ping?displayProperty=fullName> .  
  
## Disponibilité et événements de réseau  
 La classe d' <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=fullName> vous permet de déterminer si l'adresse réseau ou la disponibilité a changé.  Pour utiliser cette classe, créez un gestionnaire d'événements pour traiter la modification, et l'associer à <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> ou <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.  Pour plus d’informations, consultez [Comment : détecter la disponibilité réseau et les changements d’adresse](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).  
  
## Compléments et propriétés de réseau  
 Vous pouvez collecter des statistiques et des propriétés de réseau sur une interface ou une base du protocole.  <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, et les classes d' <xref:System.Net.NetworkInformation.PhysicalAddress> fournissent des informations sur une interface réseau particulière, tandis que <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, et les classes d' <xref:System.Net.NetworkInformation.UdpStatistics> fournissent des informations sur les packs de la couche 3 et de la couche 4.  Pour plus d’informations, consultez [Comment : obtenir des informations d’interface et de protocole](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).  
  
## Déterminez si un hôte distant est accessible  
 Vous pouvez utiliser la classe d' <xref:System.Net.NetworkInformation.Ping> pour déterminer si un hôte distant est en hausse, sur le réseau, et accessible.  Pour plus d’informations, consultez [Procédure : exécution d’une requête ping](../../../docs/framework/network-programming/how-to-ping-a-host.md).  
  
## Voir aussi  
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)   
 [Exemple de technologie informatique d'informations réseau](http://go.microsoft.com/fwlink/?LinkID=179564)   
 [Exemple de technologie d'outils de netstat](http://go.microsoft.com/fwlink/?LinkID=179562)   
 [Exemple de client technologie de ping](http://go.microsoft.com/fwlink/?LinkID=179565)