---
title: "Modification du runtime dans le .NET Framework 4.5.1 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- runtime changes
- .NET Framework 4.5.1
ms.assetid: da880ad7-ba0a-4368-b340-705e3533c351
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4e4903c2f25354005f95b3ed8f9728cfe8a0a92e
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-451"></a>Modifications du runtime dans le .NET Framework 4.5.1
Dans de rares cas, les modifications du runtime peuvent affecter les applications existantes qui ciblent le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ou 4.5 mais qui s'exécutent sur le runtime 4.5.1. Il s'agit notamment des modifications dans les domaines suivants :  
  
-   [Fonctionnalités de base](#Core)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
 La colonne Portée des tableaux suivants indique l'importance de chaque modification :  
  
-   Majeur. Modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code. Notez qu'aucune des modifications du runtime ne correspond à cette catégorie.  
  
-   Mineur. Modification qui affecte un petit nombre d'applications ou qui nécessite peu de modifications du code.  
  
-   Limité. Modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.  
  
-   Transparent. Modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application. L'application n'a pas besoin d'être modifiée en raison de cette modification.  
  
<a name="Core"></a>   
## <a name="core-runtime-changes"></a>Principales modifications du runtime  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> serialization|Un objet sérialisé <xref:System.Collections.Concurrent.ConcurrentDictionary%602> dans le .NET Framework 4.5 avec <xref:System.Runtime.Serialization.NetDataContractSerializer> ne peut pas être désérialisé dans le .NET Framework 4.5.1 et 4.5.2 en raison de changements internes au niveau du type.<br /><br /> Ce changement *ne s’applique pas* dans les scénarios suivants :<br /><br /> Un objet <xref:System.Collections.Concurrent.ConcurrentDictionary%602>qui est sérialisé dans le .NET Framework 4.5 et désérialisé dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Le <xref:System.Runtime.Serialization.NetDataContractSerializer> du [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] qui est capable de désérialiser l’objet.<br /><br /> Un objet <xref:System.Collections.Concurrent.ConcurrentDictionary%602>qui est sérialisé dans une version ultérieure du .NET Framework et désérialisé dans le .NET Framework 4.5. Le <xref:System.Runtime.Serialization.NetDataContractSerializer> du .NET Framework 4.5 qui est capable de désérialiser l’objet.<br /><br /> La sérialisation et la désérialisation interversions d’un objet <xref:System.Collections.Concurrent.ConcurrentDictionary%602> entre n’importe quelle version du .NET Framework postérieure au .NET Framework 4.5. Ce changement s’applique *uniquement* aux objets sérialisés avec le .NET Framework 4.5.|Deux solutions de contournement sont disponibles si vous devez sérialiser un objet <xref:System.Collections.Concurrent.ConcurrentDictionary%602> dans le .NET Framework 4.5 et le désérialiser dans une version ultérieure du .NET Framework :<br /><br /> Utilisez un autre sérialiseur, tel que <xref:System.Runtime.Serialization.DataContractSerializer> ou <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.<br /><br /> Effectuez une mise à niveau vers le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], qui prend en charge la désérialisation d’un objet <xref:System.Collections.Concurrent.ConcurrentDictionary%602>sérialisé dans le .NET Framework 4.5.|Mineur|  
|Classe <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName>|<xref:System.Diagnostics.Tracing.EventListener> tronque les chaînes ayant des valeurs Null incorporées. Les caractères Null ne sont pas pris en charge par la classe <xref:System.Diagnostics.Tracing.EventSource>.|Cette modification affecte uniquement les applications qui utilisent <xref:System.Diagnostics.Tracing.EventListener> pour lire des données <xref:System.Diagnostics.Tracing.EventSource> dans le processus et qui utilisent des caractères Null comme délimiteurs.|Limité|  
|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> class|Le runtime applique à présent le contrat qui stipule ce qui suit : une classe dérivée d’<xref:System.Diagnostics.Tracing.EventSource> qui définit une méthode d’événement ETW doit appeler la méthode <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=fullName> de la classe de base avec l’ID d’événement, suivi des mêmes arguments que ceux passés à la méthode d’événement ETW.|Une exception <xref:System.IndexOutOfRangeException> est levée si un <xref:System.Diagnostics.Tracing.EventListener> lit des données <xref:System.Diagnostics.Tracing.EventSource> pour une source d’événements qui ne respecte pas ce contrat.<br /><br /> Consultez [Atténuation : appels de la méthode EventSource.WriteEvent](../../../docs/framework/migration-guide/mitigation-eventsource-writeevent-method-calls.md).|Mineur|  
|Désérialisation d'objets entre les domaines d'application|Dans certains cas, quand une application utilise deux domaines d'application ou plus avec des bases d'application différentes, une tentative de désérialisation des objets dans le contexte d'appel logique entre les domaines d'application lève une exception.|Ce problème survient dans un scénario très spécifique. Pour plus d’informations sur l’atténuation, consultez [Atténuation : désérialisation des objets à travers les domaines d’application](../../../docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md).|Limité|  
|<xref:System.IO.Stream.Dispose%2A?displayProperty=fullName> method|Dans les applications [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)], les adaptateurs de flux [!INCLUDE[wrt](../../../includes/wrt-md.md)] n’appellent plus la méthode <xref:System.IO.Stream.FlushAsync%2A> à partir de la méthode <xref:System.IO.Stream.Dispose%2A>.|Cette modification devrait être transparente. Les développeurs peuvent rétablir le comportement précédent en écrivant du code comme le suivant :<br /><br /> `using (System.IO.Stream stream = GetWindowsRuntimeStream() As Stream)  {     // do something     await stream.FlushAsync();   }`|Transparent|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf-runtime-changes"></a>Modifications du runtime Windows Communication Foundation (WCF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Paramètre de configuration [minFreeMemoryPercentageToActiveService](http://msdn.microsoft.com/library/ms731336.aspx)|Le paramètre détermine la mémoire minimale devant être disponible sur le serveur avant l'activation d'un service WCF. Il est conçu pour éviter les exceptions <xref:System.OutOfMemoryException>. Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ce paramètre est sans effet. Dans le [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], ce paramètre est observé.|Une exception se produit si la mémoire disponible sur le serveur web est inférieure au pourcentage défini par le paramètre de configuration. Certains services WCF qui ont réussi à démarrer et à s'exécuter dans un environnement où la mémoire est limitée risquent à présent d'échouer.<br /><br /> Consultez [Atténuation : paramètre de configuration minFreeMemoryPercentageToActiveService](../../../docs/framework/migration-guide/mitigation-minfreememorypercentagetoactiveservice-configuration-setting.md).|Mineur|  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-1.md)   
 [Compatibilité des applications dans la version 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilité des applications dans la version 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)
