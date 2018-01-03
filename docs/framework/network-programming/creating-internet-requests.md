---
title: "Création de requêtes Internet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8cbbb0db657f002c189ab4db9311ca48d83c32a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-internet-requests"></a>Création de requêtes Internet
Les applications créent des instances de <xref:System.Net.WebRequest> par le biais de la méthode <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>. Il s’agit d’une méthode statique qui crée une classe dérivée de **WebRequest** basée sur le schéma d’URI qui lui est passé.  
  
## <a name="web-file-and-ftp-requests"></a>Requêtes web, FTP et de fichier  
 Le .NET Framework fournit la classe <xref:System.Net.HttpWebRequest>, qui est dérivée de **WebRequest**, pour gérer les requêtes HTTP et HTTPS. Dans la plupart des cas, la classe **WebRequest** fournit toutes les propriétés dont vous avez besoin pour effectuer une requête ; toutefois, si nécessaire, vous pouvez effectuer un cast d’objets **WebRequest** créés par la méthode **WebRequest.Create** vers le type **HttpWebRequest** pour accéder aux propriétés de la requête propres à HTTP. De même, l’objet **HttpWebResponse** gère les réponses aux requêtes HTTP et HTTPS. Pour accéder aux propriétés de l’objet **HttpWebResponse** propres à HTTP, vous devez effectuer un cast des objets **WebResponse** vers le type **HttpWebResponse**.  
  
 Le .NET Framework fournit également les classes <xref:System.Net.FileWebRequest> et <xref:System.Net.FileWebResponse> afin de gérer les requêtes pour les ressources qui utilisent le schéma d’URI « file: ». De même, les classes <xref:System.Net.FtpWebRequest> et <xref:System.Net.FtpWebResponse> sont fournies pour gérer les requêtes pour les ressources qui utilisent le schéma d’URI « ftp: ». Si votre requête concerne une ressource qui utilise l’un de ces schémas, vous pouvez utiliser la méthode **WebRequest.Create** pour obtenir un objet avec lequel effectuer votre requête.  
  
 Pour gérer les requêtes qui utilisent d’autres protocoles au niveau de l’application, vous devez implémenter des classes propres au protocole dérivées de **WebRequest** et **WebResponse**. Pour plus d’informations, consultez [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour demander des données à l’aide de la classe WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)
