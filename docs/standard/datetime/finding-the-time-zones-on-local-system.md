---
title: "Recherche des fuseaux horaires définis sur un système local"
description: "Recherche des fuseaux horaires définis sur un système local"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3a6ee323-f3cf-486d-aa0c-103931f1eba9
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 4f8913e3c193e7c76160ac45d576c4cf75d11fed

---

# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Recherche des fuseaux horaires définis sur un système local

La classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) n’expose pas de constructeur public. En conséquence, le mot clé `new` ne peut pas être utilisé pour créer un objet [TimeZoneInfo](xref:System.TimeZoneInfo). À la place, pour instancier des objets [TimeZoneInfo](xref:System.TimeZoneInfo), vous devez récupérer des informations sur les fuseaux horaires prédéfinis à partir du système d’exploitation. Cette rubrique explique comment instancier un fuseau horaire à partir de données stockées par le système d’exploitation. En outre, les propriétés `static` (`Shared` en Visual Basic) de la classe [TimeZoneInfo](xref:System.TimeZoneInfo) permettent d’accéder au temps universel coordonné (UTC) et au fuseau horaire local.

## <a name="accessing-individual-time-zones"></a>Accès aux fuseaux horaires individuels

La classe [TimeZoneInfo](xref:System.TimeZoneInfo) fournit deux objets de fuseau horaire prédéfinis qui représentent l’heure UTC et le fuseau horaire local. Ils sont disponibles à partir des propriétés [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) et [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local), respectivement. Pour savoir comment accéder aux fuseaux horaires UTC ou locaux, consultez [Guide pratique : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](access-utc-and-local.md). 

Vous pouvez également instancier un objet [TimeZoneInfo](xref:System.TimeZoneInfo) qui représente tout fuseau horaire défini par le système d’exploitation. Pour obtenir des instructions sur l’instanciation d’un objet de fuseau horaire spécifique, consultez [Guide pratique : instancier un objet TimeZoneInfo](instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identificateurs de fuseau horaire

L'identificateur de fuseau horaire est un champ clé qui identifie le fuseau horaire de manière unique. Alors que la plupart des clés sont relativement courtes, l'identificateur de fuseau horaire est long. Dans la plupart des cas, sa valeur correspond à la propriété [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName) qui est utilisée pour fournir le nom de l’heure d’hiver du fuseau horaire. Toutefois, il existe des exceptions. Pour vous assurer que l'identificateur fourni est valide, la meilleure façon consiste à énumérer les fuseaux horaires disponibles sur votre système et à noter les identificateurs associés. Pour obtenir des instructions sur l’énumération des fuseaux horaires, consultez [Guide pratique : énumérer les fuseaux horaires d’un ordinateur](enumerate-time-zones.md).

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)

[Guide pratique pour accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](access-utc-and-local.md)

[Guide pratique pour instancier un objet TimeZoneInfo](instantiate-time-zone-info.md)

[Guide pratique pour énumérer les fuseaux horaires d’un ordinateur](enumerate-time-zones.md)

[Conversion d’heures entre fuseaux horaires](converting-between-time-zones.md)


<!--HONumber=Nov16_HO1-->


