---
title: Dates, heures et fuseaux horaires
description: Dates, heures et fuseaux horaires
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 76e6cacc-1c0c-4a71-8cb8-018c112385ba
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: a4d0a68ac32c3d722a1479ca2b067892fd88bf52

---

# <a name="dates-times-and-time-zones"></a>Dates, heures et fuseaux horaires

Outre la structure [System.DateTime](xref:System.DateTime) élémentaire, .NET fournit les classes suivantes qui prennent en charge l’utilisation des fuseaux horaires :

* [System.TimeZoneInfo](xref:System.TimeZoneInfo)
    
  Utilisez cette classe pour travailler avec le fuseau horaire local du système et le fuseau horaire UTC.
  
* [System.DateTimeOffset](xref:System.DateTimeOffset)  

  Utilisez cette structure pour travailler avec des dates et heures dont le décalage (ou différence) par rapport à l'heure UTC est connu. La structure [DateTimeOffset](xref:System.DateTimeOffset)] associe une valeur de date et d’heure au décalage de cette heure par rapport à l’heure UTC. En raison de sa relation avec l’heure UTC, une valeur individuelle de date et d’heure identifie de façon univoque un point unique dans le temps. Cela rend une valeur [DateTimeOffset](xref:System.DateTimeOffset)] plus portable d’un ordinateur à un autre qu’une valeur [DateTime](xref:System.DateTime)]. 
  
Cette section de la documentation fournit les informations dont vous avez besoin pour travailler avec les fuseaux horaires et pour créer des applications prenant en charge les fuseaux horaires, qui peuvent convertir des dates et des heures d’un fuseau horaire à un autre.

## <a name="in-this-section"></a>Dans cette section

[Vue d’ensemble des fuseaux horaires](time-zone-overview.md) : Décrit la terminologie, les concepts et les problèmes impliqués dans la création d’applications prenant en charge les fuseaux horaires.
    
[Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](choosing-between-datetime.md) : Explique quand utiliser les types [System.DateTime](xref:System.DateTime), [System.DateTimeOffset](xref:System.DateTimeOffset) et [System.TimeZoneInfo](xref:System.TimeZoneInfo) lorsque vous travaillez avec des données de date et d’heure.
    
[Recherche des fuseaux horaires définis sur un système local](finding-the-time-zones-on-local-system.md) : Décrit comment énumérer les fuseaux horaires trouvés sur un système local.

[Instanciation d’un objet DateTimeOffset](instantiating-a-datetimeoffset-object.md) : Décrit comment un objet [System.DateTimeOffset](xref:System.DateTimeOffset) peut être instancié et comment une valeur [System.DateTime](xref:System.DateTime) peut être convertie en valeur [System.DateTimeOffset](xref:System.DateTimeOffset).

[Exécution d’opérations arithmétiques avec des dates et heures](performing-arithmetic-operations.md) : Traite les problèmes liés à l’ajout, la soustraction et la comparaison de valeurs [System.DateTime](xref:System.DateTime) et [System.DateTimeOffset](xref:System.DateTimeOffset).

[Conversion entre DateTime et DateTimeOffset](converting-between-datetime-and-offset.md) : Explique comment convertir des valeurs [System.DateTime](xref:System.DateTime) et [System.DateTimeOffset](xref:System.DateTimeOffset).

[Conversion d’heures entre fuseaux horaires](converting-between-time-zones.md) : Décrit comment convertir les heures d’un fuseau horaire dans un autre fuseau horaire.

[Guide pratique : énumérer les fuseaux horaires d’un ordinateur](enumerate-time-zones.md) : Fournit des exemples qui énumèrent les fuseaux horaires définis dans le Registre d’un ordinateur et qui permettent aux utilisateurs de sélectionner un fuseau horaire prédéfini dans une liste.

[Guide pratique : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](access-utc-and-local.md) : Décrit comment accéder au temps universel coordonné et au fuseau horaire local.

[Guide pratique : instancier un objet TimeZoneInfo](instantiate-time-zone-info.md) : Décrit comment instancier un objet [System.TimeZoneInfo](xref:System.TimeZoneInfo) à partir du Registre du système local.

[Guide pratique : utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure](use-time-zones-in-arithmetic.md) : Explique comment effectuer des opérations arithmétiques de date et d’heure qui reflètent les règles d’ajustement d’un fuseau horaire.

[Guide pratique : résoudre des heures ambiguës](resolve-ambiguous-times.md) : Décrit comment résoudre une heure ambiguë en la mappant sur l’heure d’hiver du fuseau horaire.

[Guide pratique : permettre aux utilisateurs de résoudre des heures ambiguës](let-users-resolve-ambiguous-times.md) : Décrit comment permettre à un utilisateur de déterminer le mappage entre une heure locale ambiguë et le temps universel coordonné.

## <a name="reference"></a>Référence

[System.TimeZoneInfo](xref:System.TimeZoneInfo)

[System.DateTimeOffset](xref:System.DateTimeOffset)

[System.DateTime](xref:System.DateTime)



<!--HONumber=Nov16_HO1-->


