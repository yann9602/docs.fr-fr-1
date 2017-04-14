---
title: "Modifications d&#39;ex&#233;cution dans le&#160;.NET Framework&#160;4.5.1 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "compatibilité des applications"
  - "modifications du runtime"
  - ".NET Framework 4.5.1"
ms.assetid: da880ad7-ba0a-4368-b340-705e3533c351
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Modifications d&#39;ex&#233;cution dans le&#160;.NET Framework&#160;4.5.1
Dans de rares cas, les modifications du runtime peuvent affecter les applications existantes qui ciblent le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ou 4.5 mais qui s'exécutent sur le runtime 4.5.1. Il s'agit notamment des modifications dans les domaines suivants :  
  
-   [Core](#Core)  
  
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
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> sérialisation</TKey, TValue>|A <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objet sérialisé dans le .NET Framework 4.5 avec le <xref:System.Runtime.Serialization.NetDataContractSerializer> ne peut pas être désérialisé uniquement en raison de changements internes dans le type dans le .NET Framework 4.5.1 et 4.5.2.\</TKey, TValue><br /><br /> Cette modification est *pas* s’appliquent dans les scénarios suivants :<br /><br /> A <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objet sérialisé dans le .NET Framework 4.5 et désérialisé dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].</TKey, TValue> Le <xref:System.Runtime.Serialization.NetDataContractSerializer> dans les [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] est capable de désérialiser l’objet.<br /><br /> A <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objet sérialisé dans une version ultérieure du .NET Framework et désérialisé dans le .NET Framework 4.5.\</TKey, TValue> Le <xref:System.Runtime.Serialization.NetDataContractSerializer> dans le .NET Framework 4.5 est capable de désérialiser l’objet.<br /><br /> Version de la sérialisation et la désérialisation d’un <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objet entre n’importe quelle version du .NET Framework après le .NET Framework 4.5.</TKey, TValue> Cette modification s’applique aux objets sérialisés avec le .NET Framework 4.5 *uniquement*.|Deux solutions sont disponibles si nécessaire sérialiser un <xref:System.Collections.Concurrent.ConcurrentDictionary%602> de l’objet sur le .NET Framework 4.5 et désérialiser sur une version ultérieure du .NET Framework :\</TKey, TValue><br /><br /> Utiliser un autre sérialiseur, tel que le <xref:System.Runtime.Serialization.DataContractSerializer> ou <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.<br /><br /> Mise à niveau vers le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], qui prend en charge la désérialisation des <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objet sérialisé avec le .NET Framework 4.5.\</TKey, TValue>|Secondaire|  
|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> (classe)|<xref:System.Diagnostics.Tracing.EventListener> tronque les chaînes comportant des valeurs null incorporées. Caractères null ne sont pas pris en charge par le <xref:System.Diagnostics.Tracing.EventSource> classe.|La modification affecte uniquement les applications qui utilisent <xref:System.Diagnostics.Tracing.EventListener> en <xref:System.Diagnostics.Tracing.EventSource> données de processus et qui utilisent des caractères null comme délimiteurs.|Bord|  
|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> (classe)|Le runtime applique à présent le contrat qui spécifie les éléments suivants : une classe dérivée de <xref:System.Diagnostics.Tracing.EventSource> qui définit un ETW méthode d’événement doit appeler la classe de base <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=fullName> méthode avec l’ID d’événement suivi par les mêmes arguments passés à la méthode d’événement ETW.|Un <xref:System.IndexOutOfRangeException> exception est levée si une <xref:System.Diagnostics.Tracing.EventListener> lit <xref:System.Diagnostics.Tracing.EventSource> données dans le processus pour une source d’événements qui ne respecte pas ce contrat.<br /><br /> Consultez [atténuation : méthode EventSource.WriteEvent](../../../docs/framework/migration-guide/mitigation-eventsource-writeevent-method-calls.md)|Secondaire|  
|Désérialisation d'objets entre les domaines d'application|Dans certains cas, quand une application utilise deux domaines d'application ou plus avec des bases d'application différentes, une tentative de désérialisation des objets dans le contexte d'appel logique entre les domaines d'application lève une exception.|Ce problème survient dans un scénario très spécifique. Pour plus d’informations et d’atténuation, consultez [atténuation : désérialisation des objets entre les domaines d’application](../../../docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md).|Bord|  
|<xref:System.IO.Stream.Dispose%2A?displayProperty=fullName> (méthode)|Dans [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] applications, [!INCLUDE[wrt](../../../includes/wrt-md.md)] adaptateurs de flux n’appellent plus la <xref:System.IO.Stream.FlushAsync%2A> méthode à partir de la <xref:System.IO.Stream.Dispose%2A> méthode.|Cette modification devrait être transparente. Les développeurs peuvent rétablir le comportement précédent en écrivant du code comme le suivant :<br /><br /> `using (System.IO.Stream stream = GetWindowsRuntimeStream() As Stream)  {     // do something     await stream.FlushAsync();   }`|Transparent|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf-runtime-changes"></a>Modifications du runtime Windows Communication Foundation (WCF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|[minFreeMemoryPercentageToActiveService](http://msdn.microsoft.com/library/ms731336.aspx) de configuration|Le paramètre détermine la mémoire minimale devant être disponible sur le serveur avant l'activation d'un service WCF. Il est conçu pour empêcher <xref:System.OutOfMemoryException> exceptions. Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ce paramètre est sans effet. Dans le [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], ce paramètre est observé.|Une exception se produit si la mémoire disponible sur le serveur web est inférieure au pourcentage défini par le paramètre de configuration. Certains services WCF qui ont réussi à démarrer et à s'exécuter dans un environnement où la mémoire est limitée risquent à présent d'échouer.<br /><br /> Consultez la page [atténuation : minFreeMemoryPercentageToActiveService de configuration](../../../docs/framework/migration-guide/mitigation-minfreememorypercentagetoactiveservice-configuration-setting.md).|Secondaire|  
  
## <a name="see-also"></a>Voir aussi  
 [Reciblage des modifications](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-1.md)   
 [Compatibilité des applications dans 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilité des applications dans la version 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)