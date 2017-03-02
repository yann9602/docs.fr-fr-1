---
title: "Vue d’ensemble des fuseaux horaires"
description: "Vue d’ensemble des fuseaux horaires"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e3a10f62-d403-4441-8621-adc964e32c07
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 200d502d12750a28d2a54058f53b4bbef78973c7
ms.lasthandoff: 03/02/2017

---

# <a name="time-zone-overview"></a>Vue d’ensemble des fuseaux horaires

La classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) simplifie la création d’applications prenant en charge les fuseaux horaires. La classe [TimeZoneInfo](xref:System.TimeZoneInfo) prend en charge l’utilisation du fuseau horaire local et du temps universel coordonné (UTC), ainsi que n’importe quel fuseau horaire sur lequel des informations sont prédéfinies dans le Registre. Vous pouvez également utiliser [TimeZoneInfo](xref:System.TimeZoneInfo) pour définir des fuseaux horaires personnalisés sur lesquels le système ne dispose d’aucune information.

## <a name="time-zone-essentials"></a>Éléments principaux des fuseaux horaires

Un fuseau horaire est une région géographique dans laquelle la même heure est utilisée. En général, mais pas toujours, des fuseaux horaires adjacents ont une heure d’écart. L’heure dans n’importe quel fuseau horaire du monde peut être exprimée comme un décalage par rapport au temps universel coordonné (UTC).

La plupart des fuseaux horaires du monde prennent en charge l’heure d’été. L’heure d’été essaie d’optimiser les heures de clarté en avançant l’heure d’une heure au printemps ou au début de l’été, puis en rétablissant l’heure normale (ou standard) à la fin de l’été ou en automne. Ces variations par rapport à l’heure d’hiver sont appelées règles d’ajustement.

Le passage à l’heure d’été ou à l’heure d’hiver dans un fuseau horaire particulier peut être défini par une règle d’ajustement fixe ou flottante. Une règle d’ajustement fixe définit une date particulière à laquelle le passage à l’heure d’été ou à l’heure d’hiver se produit chaque année. Par exemple, le passage à l’heure d’hiver qui se produit chaque année le 25 octobre suit une règle d’ajustement fixe. Les règles d’ajustement flottantes sont beaucoup plus courantes. Elles définissent un jour particulier d’une semaine particulière d’un mois particulier pour le passage à l’heure d’été ou à l’heure d’hiver. Par exemple, le passage à l’heure d’été qui se produit le troisième dimanche de mars suit une règle d’ajustement flottante.

Pour les fuseaux horaires qui prennent en charge des règles d’ajustement, le passage à l’heure d’hiver et à l’heure d’été crée deux types d’heures anormales : des heures non valides et des heures ambiguës. Une heure non valide est une heure inexistante, créée par le passage à l’heure d’été. Par exemple, si ce passage a lieu un jour particulier à 2:00 et fait que l’heure devient 3:00, tout intervalle de temps compris entre 2:00 et 2:59:59 est non valide. Une heure ambiguë est une heure qui peut correspondre à deux heures différentes dans un même fuseau horaire. Elle est créée par le passage à l’heure d’hiver. Par exemple, si ce passage a lieu un jour particulier à 2:00 et fait que l’heure devient 1:00, tout intervalle de temps compris entre 1:00 et 1:59:59 peut être interprété comme une heure d’hiver ou une heure d’été. 

## <a name="time-zone-terminology"></a>Terminologie relative aux fuseaux horaires

Le tableau suivant définit les termes couramment utilisés lors de l’utilisation de fuseaux horaires et du développement d’applications prenant en charge les fuseaux horaires.

Terme | Définition
---- | ----------
Règle d’ajustement | Règle qui définit les dates de passage à l’heure d’été et de retour à l’heure d’hiver. Chaque règle d’ajustement comporte une date de début et de fin qui définit quand la règle est en place (par exemple, la règle d’ajustement est en place du 1er janvier 1986 jusqu’au 31 décembre 2020), un delta (la valeur selon laquelle l’heure d’hiver change suite à l’application de la règle d’ajustement) et des informations sur la date et l’heure spécifiques auxquelles les transitions doivent avoir lieu pendant la période d’ajustement. Les transitions peuvent suivre une règle fixe ou une règle flottante.
Heure ambiguë | Heure qui peut correspondre à deux heures différentes dans un même fuseau horaire. Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire. Par exemple, si ce passage a lieu un jour particulier à 2:00 et fait que l’heure devient 1:00, tout intervalle de temps compris entre 1:00 et 1:59:59 peut être interprété comme une heure d’hiver ou une heure d’été. 
Règle fixe | Règle d’ajustement qui définit une date particulière pour le passage à l’heure d’été ou à l’heure d’hiver. Par exemple, le passage à l’heure d’hiver qui se produit chaque année le 25 octobre suit une règle d’ajustement fixe.
Règle flottante | Règle d’ajustement qui définit un jour particulier d’une semaine particulière d’un mois particulier pour le passage à l’heure d’été ou à l’heure d’hiver. Par exemple, le passage à l’heure d’été qui se produit le troisième dimanche de mars suit une règle d’ajustement flottante.
Heure non valide | Heure inexistante, créée par le passage à l’heure d’été. Elle intervient lorsque l’heure est avancée, par exemple lors du passage de l’heure d’hiver d’un fuseau horaire à son heure d’été. Par exemple, si ce passage a lieu un jour particulier à 2:00 et fait que l’heure devient 3:00, tout intervalle de temps compris entre 2:00 et 2:59:59 est non valide.
Durée de transition | Informations sur un changement d’heure spécifique, tel que le passage de l’heure d’été à l’heure d’hiver, ou vice versa, dans un fuseau horaire particulier.

## <a name="time-zones-and-the-timezoneinfo-class"></a>Fuseaux horaires et classe TimeZoneInfo

Dans .NET, un objet [System.TimeZoneInfo](xref:System.TimeZoneInfo) représente un fuseau horaire, en fonction des informations fournies par le système d’exploitation. La dépendance de la classe [TimeZoneInfo](xref:System.TimeZoneInfo) sur le système d’exploitation signifie qu’une application prenant en charge les fuseaux horaires ne peut pas être sûre qu’un fuseau horaire particulier est défini sur tous les systèmes d’exploitation. Par conséquent, la tentative d’instancier un fuseau horaire spécifique (autre que le fuseau horaire local ou le fuseau horaire qui représente l’heure UTC) doit utiliser la gestion des exceptions. Elle doit également fournir une méthode permettant à l’application de poursuivre si un objet [TimeZoneInfo](xref:System.TimeZoneInfo) requis ne peut pas être instancié.

Étant donné que chaque fuseau horaire est caractérisé par un décalage de base par rapport à l’heure UTC, ainsi que par un décalage par rapport à l’heure UTC qui reflète toutes les règles d’ajustement existantes, une heure dans un fuseau horaire peut être facilement convertie en une heure dans un autre fuseau horaire. À cet effet, l’objet [TimeZoneInfo](xref:System.TimeZoneInfo) inclut plusieurs méthodes de conversion, y compris :

* [ConvertTime (DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)), qui convertit une valeur [System.DateTime](xref:System.DateTime) en une heure dans un fuseau horaire particulier.

* [ConvertTime(DateTime, TimeZoneInfo, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo,System.TimeZoneInfo)), qui convertit une valeur [DateTime](xref:System.DateTime) d’un fuseau horaire vers un autre.

* [ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)), qui convertit une valeur [System.DateTimeOffset](xref:System.DateTimeOffset) en une heure dans un fuseau horaire particulier. 

Pour plus d’informations sur la conversion d’heures entre fuseaux horaires, consultez [Conversion d’heures entre fuseaux horaires](converting-between-time-zones.md).

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)
