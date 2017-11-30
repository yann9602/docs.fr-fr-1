---
title: NetworkInformation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: acf15eb79fab479036f182c58b8ec94d3ac43ea0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="networkinformation"></a>NetworkInformation
L’espace de noms <xref:System.Net.NetworkInformation> permet de recueillir des informations concernant les événements, les modifications, les statistiques et les propriétés liés au réseau. Vous pouvez également déterminer si un hôte distant est accessible à l’aide de la classe <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType>.  
  
## <a name="network-availability-and-events"></a>Disponibilité du réseau et événements réseau  
 La classe <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> permet de déterminer si l’adresse réseau ou la disponibilité du réseau ont changé. Pour utiliser cette classe, créez un gestionnaire d’événements en vue de traiter la modification, puis associez-la à un <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> ou un <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Pour plus d’informations, consultez [Guide pratique pour détecter la disponibilité réseau et les changements d’adresse](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Statistiques et propriétés du réseau  
 Vous pouvez collecter des informations relatives aux statistiques et aux propriétés du réseau au niveau d’une interface ou d’un protocole. Les classes <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType> et <xref:System.Net.NetworkInformation.PhysicalAddress> fournissent des informations sur les interfaces réseau, alors que les classes <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics> et <xref:System.Net.NetworkInformation.UdpStatistics> fournissent des informations sur les paquets des couches 3 et 4. Pour plus d’informations, consultez [Guide pratique pour obtenir des informations d’interface et de protocole](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Déterminer si un hôte distant est accessible  
 Vous pouvez utiliser la classe <xref:System.Net.NetworkInformation.Ping> pour déterminer si un hôte distant est disponible, s’il se trouve dans le réseau et s’il est accessible. Pour plus d’informations, consultez [Guide pratique pour effectuer un test ping](../../../docs/framework/network-programming/how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Exemple de technologie d’informations réseau](http://go.microsoft.com/fwlink/?LinkID=179564)  
 [Exemple de technologie NetStat](http://go.microsoft.com/fwlink/?LinkID=179562)  
 [Exemple de technologie de test ping à partir d’une application cliente](http://go.microsoft.com/fwlink/?LinkID=179565)
