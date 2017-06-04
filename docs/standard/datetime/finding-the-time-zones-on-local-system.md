---
title: "Recherche des fuseaux horaires d&#233;finis sur un syst&#232;me local | Microsoft Docs"
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
  - "accès au fuseau horaire local"
  - "identificateurs de fuseau horaire (.NET Framework)"
  - "fuseaux horaires (.NET Framework), recherche du fuseau horaire local"
  - "fuseaux horaires (.NET Framework), locaux"
  - "fuseaux horaires (.NET Framework), récupérer"
  - "fuseaux horaires (.NET Framework), UTC"
  - "temps UTC, recherche du fuseau horaire local"
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Recherche des fuseaux horaires d&#233;finis sur un syst&#232;me local
La classe <xref:System.TimeZoneInfo> n'expose pas de constructeur public.  En conséquence, le mot clé `new` ne peut pas être utilisé pour créer un objet <xref:System.TimeZoneInfo>.  Pour instancier des objets <xref:System.TimeZoneInfo>, vous devez donc soit récupérer dans le Registre des informations sur les fuseaux horaires prédéfinis, soit créer un fuseau horaire personnalisé.  Cette rubrique explique comment instancier un fuseau horaire à partir de données stockées dans le Registre.  En outre, les propriétés `static` \(`shared` en Visual Basic\) de la classe <xref:System.TimeZoneInfo> permettent d'accéder au temps universel coordonné \(UTC\) et au fuseau horaire local.  
  
> [!NOTE]
>  Si les fuseaux horaires ne sont pas définis dans le Registre, vous pouvez créer des fuseaux horaires personnalisés en appelant les surcharges de la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>.  La création d'un fuseau horaire personnalisé est décrite dans les rubriques [Comment : créer des fuseaux horaires sans règles d'ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) et [Comment : créer des fuseaux horaires avec des règles d'ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).  Vous pouvez également instancier un objet <xref:System.TimeZoneInfo> en le restaurant à partir d'une chaîne sérialisée à l'aide de la méthode <xref:System.TimeZoneInfo.FromSerializedString%2A>.  La procédure de sérialisation et de désérialisation d'un objet <xref:System.TimeZoneInfo> est décrite dans les rubriques [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) et [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).  
  
## Accès aux fuseaux horaires individuels  
 La classe <xref:System.TimeZoneInfo> fournit deux objets de fuseaux horaires prédéfinis qui représentent l'heure UTC et le fuseau horaire local.  Ils sont disponibles dans les propriétés <xref:System.TimeZoneInfo.Utc%2A> et <xref:System.TimeZoneInfo.Local%2A>, respectivement.  Pour savoir comment accéder à l'heure UTC ou aux fuseaux horaires locaux, consultez [Comment : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](../../../docs/standard/datetime/access-utc-and-local.md).  
  
 Vous pouvez également instancier un objet <xref:System.TimeZoneInfo> qui représente tout fuseau horaire défini dans le Registre.  Pour obtenir des instructions sur l'instanciation d'un objet de fuseau horaire spécifique, consultez [Comment : instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).  
  
## Identificateurs de fuseau horaire  
 L'identificateur de fuseau horaire est un champ clé qui identifie le fuseau horaire de manière unique.  Alors que la plupart des clés sont relativement courtes, l'identificateur de fuseau horaire est long.  Dans la plupart des cas, sa valeur correspond à la propriété <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=fullName>, utilisée pour fournir le nom de l'heure standard du fuseau horaire.  Toutefois, il existe des exceptions.  Pour vous assurer que l'identificateur fourni est valide, la meilleure façon consiste à énumérer les fuseaux horaires disponibles sur votre système et à noter les identificateurs associés.  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Comment : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](../../../docs/standard/datetime/access-utc-and-local.md)   
 [Comment : instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)   
 [Conversion d'heures entre fuseaux horaires](../../../docs/standard/datetime/converting-between-time-zones.md)