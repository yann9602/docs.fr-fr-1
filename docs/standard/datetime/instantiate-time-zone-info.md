---
title: "Comment&#160;: instancier un objet TimeZoneInfo | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instancier des objets de fuseau horaire"
  - "objet de fuseau horaire (.NET Framework), instanciation"
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: instancier un objet TimeZoneInfo
La façon la plus courante pour instancier un objet <xref:System.TimeZoneInfo> consiste à récupérer les informations le concernant à partir du registre. Cette rubrique explique comment instancier un objet <xref:System.TimeZoneInfo> à partir du registre système local.  
  
### Pour instancier un objet TimeZoneInfo  
  
1.  Déclarez un objet <xref:System.TimeZoneInfo>.  
  
2.  Appelez la méthode <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=fullName>`static` \(`Shared` dans Visual Basic\).  
  
3.  Gérez toutes les exceptions levées par la méthode, en particulier l’exception <xref:System.TimeZoneNotFoundException> qui est levée si le fuseau horaire n’est pas défini dans le registre.  
  
## Exemple  
 Le code suivant récupère un objet <xref:System.TimeZoneInfo> qui représente le fuseau horaire EST et affiche l’heure EST qui correspond à l’heure locale.  
  
 [!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
 [!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]  
  
 Le paramètre unique de la méthode <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=fullName> est l’identificateur du fuseau horaire que vous souhaitez récupérer, qui correspond à la propriété <xref:System.TimeZoneInfo.Id%2A?displayProperty=fullName> de l’objet. L'identificateur de fuseau horaire est un champ clé qui identifie le fuseau horaire de manière unique. Alors que la plupart des clés sont relativement courtes, l'identificateur de fuseau horaire est long. Dans la plupart des cas, sa valeur correspond à la propriété <xref:System.TimeZoneInfo.StandardName%2A> d’un objet <xref:System.TimeZoneInfo>, qui est utilisée pour fournir le nom de l’heure standard du fuseau horaire. Toutefois, il existe des exceptions. Pour vous assurer que l’identificateur fourni est valide, il est recommandé d’énumérer les fuseaux horaires disponibles sur votre système et de noter les identificateurs associés. Pour voir un exemple, consultez [Comment : énumérer les fuseaux horaires d'un ordinateur](../../../docs/standard/datetime/enumerate-time-zones.md). La rubrique [Recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) contient également une liste d’identificateurs de fuseau horaire sélectionnés.  
  
 Si le fuseau horaire est trouvé, la méthode renvoie son objet <xref:System.TimeZoneInfo>.  Si le fuseau horaire n’est pas trouvé, la méthode lève une exception <xref:System.TimeZoneNotFoundException>. Si le fuseau horaire est trouvé, mais que ses données sont endommagées ou incomplètes, la méthode lève une exception <xref:System.InvalidTimeZoneException>.  
  
 Si votre application repose sur un fuseau horaire qui doit être présent, vous devez d’abord appeler la méthode <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pour récupérer les informations de fuseau horaire à partir du registre. Si l’appel de méthode échoue, votre gestionnaire d’exceptions doit alors créer une nouvelle instance du fuseau horaire ou le recréer en désérialisant un objet <xref:System.TimeZoneInfo> sérialisé. Pour obtenir un exemple, consultez [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)   
 [Comment : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](../../../docs/standard/datetime/access-utc-and-local.md)