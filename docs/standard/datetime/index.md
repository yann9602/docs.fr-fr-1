---
title: "Dates, heures et fuseaux horaires | Microsoft Docs"
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
  - "données de date et d'heure (.NET Framework)"
  - "heure (.NET Framework), fuseaux horaires"
  - "objet de fuseau horaire (.NET Framework)"
  - "fuseaux horaires (.NET Framework)"
  - "heures (.NET Framework), fuseaux horaires"
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# Dates, heures et fuseaux horaires
Outre la structure <xref:System.DateTime> de base, le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fournit les classes suivantes qui prennent en charge l'utilisation de fuseaux horaires :  
  
-   <xref:System.TimeZone>  
  
     Faites appel à cette classe pour utiliser le fuseau horaire local du système et le temps universel coordonné \(UTC, Coordinated Universal Time\).  Les fonctionnalités de la classe <xref:System.TimeZone> sont en grande partie remplacées par la classe <xref:System.TimeZoneInfo>.  
  
-   <xref:System.TimeZoneInfo>  
  
     Faites appel à cette classe pour utiliser tout fuseau horaire prédéfini sur un système, créer des fuseaux horaires et convertir facilement des dates et des heures d'un fuseau horaire à un autre.  Pour tout nouveau développement, utilisez la classe <xref:System.TimeZoneInfo> au lieu de la classe <xref:System.TimeZone>.  
  
-   <xref:System.DateTimeOffset>  
  
     Faite appel à cette structure pour utiliser des dates et heures dont le décalage \(ou différence\) par rapport à l'heure UTC est connu.  La structure <xref:System.DateTimeOffset> associe une valeur de date et d'heure à son décalage par rapport à l'heure UTC.  Par conséquent, une valeur de date et d'heure individuelle identifie de manière univoque un point unique dans le temps.  Ainsi, il est plus facile de porter une valeur <xref:System.DateTimeOffset> d'un ordinateur à un autre qu'une valeur <xref:System.DateTime>.  
  
 Cette section de la documentation indique comment utiliser des fuseaux horaires et créer des applications qui les prennent en charge et qui peuvent convertir des dates et des heures entre fuseaux horaires.  
  
## Dans cette section  
 [Vue d'ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)  
 Présente la terminologie, les concepts et les problèmes relatifs à la création d'applications prenant en charge des fuseaux horaires.  
  
 [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)  
 Indique quand utiliser les types <xref:System.DateTime>, <xref:System.DateTimeOffset> et <xref:System.TimeZoneInfo> lorsque vous travaillez avec des données de date et d'heure.  
  
 [Recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)  
 Décrit comment énumérer les fuseaux horaires trouvés sur un système local.  
  
 [Comment : énumérer les fuseaux horaires d'un ordinateur](../../../docs/standard/datetime/enumerate-time-zones.md)  
 Fournit des exemples qui énumèrent les fuseaux horaires définis dans le Registre d'un ordinateur et permettent aux utilisateurs de sélectionner un fuseau horaire prédéfini dans une liste.  
  
 [Comment : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](../../../docs/standard/datetime/access-utc-and-local.md)  
 Décrit comment accéder au temps universel coordonné et au fuseau horaire local.  
  
 [Comment : instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)  
 Décrit comment instancier un objet <xref:System.TimeZoneInfo> à partir du Registre du système local.  
  
 [Instanciation d'un objet DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md)  
 Indique comment instancier un objet <xref:System.DateTimeOffset> et convertir une valeur <xref:System.DateTime> en une valeur <xref:System.DateTimeOffset>.  
  
 [Comment : créer des fuseaux horaires sans règles d'ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)  
 Décrit comment créer un fuseau horaire personnalisé qui ne prend pas en charge le passage à\/de l'heure d'été.  
  
 [Comment : créer des fuseaux horaires avec des règles d'ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)  
 Décrit comment créer un fuseau horaire personnalisé qui prend en charge un ou plusieurs passages à\/de l'heure d'été.  
  
 [Enregistrement et restauration de fuseaux horaires](../../../docs/standard/datetime/saving-and-restoring-time-zones.md)  
 Décrit la prise en charge de <xref:System.TimeZoneInfo> à des fins de sérialisation et de désérialisation des données de fuseau horaire, et illustre quelques scénarios d'utilisation de ces fonctionnalités.  
  
 [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)  
 Décrit comment créer un fuseau horaire personnalisé et enregistrer ses informations dans un fichier de ressources.  
  
 [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)  
 Décrit comment instancier des fuseaux horaires personnalisés enregistrés dans un fichier de ressources incorporées.  
  
 [Exécution d'opérations arithmétiques avec des dates et heures](../../../docs/standard/datetime/performing-arithmetic-operations.md)  
 Discute les problèmes rencontrés lors de l'ajout, de la soustraction et de la comparaison des valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.  
  
 [Comment : utiliser des fuseaux horaires en arithmétique de date et heure](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)  
 Discute comment effectuer des opérations arithmétiques de date et heure qui reflètent les règles d'ajustement d'un fuseau horaire.  
  
 [Conversion entre DateTime et DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md)  
 Décrit comment convertir les valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.  
  
 [Conversion d'heures entre fuseaux horaires](../../../docs/standard/datetime/converting-between-time-zones.md)  
 Décrit comment convertir les heures d'un fuseau horaire à un autre.  
  
 [Comment : résoudre des heures ambiguës](../../../docs/standard/datetime/resolve-ambiguous-times.md)  
 Décrit comment résoudre une heure ambiguë en la mappant à l'heure d'hiver du fuseau horaire.  
  
 [Comment : permettre aux utilisateurs de résoudre des heures ambiguës](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)  
 Décrit comment un utilisateur peut déterminer le mappage entre une heure locale ambiguë et le temps universel coordonné.  
  
## Référence  
 <xref:System.TimeZoneInfo?displayProperty=fullName>