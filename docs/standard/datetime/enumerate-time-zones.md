---
title: "Guide pratique : énumérer les fuseaux horaires d’un ordinateur"
description: "Guide pratique pour énumérer les fuseaux horaires d’un ordinateur"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c5ae4a6c-1790-4355-b5b1-879aaf956129
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f30ba2a483ff7e5867417969946c2774175d5e3d
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Guide pratique : énumérer les fuseaux horaires d’un ordinateur

Pour utiliser correctement un fuseau horaire désigné, le système doit pouvoir accéder aux informations le concernant. Par exemple, le système d’exploitation Windows stocke ces informations dans le Registre. Il existe de nombreux fuseaux horaires dans le monde, mais le Registre contient des informations sur un sous-ensemble de ces fuseaux horaires uniquement. De plus, le Registre est une structure dynamique dont le contenu peut être modifié délibérément ou accidentellement. Par conséquent, une application ne peut pas toujours supposer qu’un fuseau horaire particulier est défini et disponible sur un système. Pour de nombreuses applications qui utilisent des informations de fuseau horaire, il convient en premier lieu de déterminer si les fuseaux horaires requis sont disponibles sur le système local ou de fournir à l’utilisateur la liste des fuseaux horaires qu’il peut sélectionner. Il faut donc qu’une application énumère les fuseaux horaires définis sur un système local. 

## <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Pour énumérer les fuseaux horaires présents sur le système local

1. Appelez la méthode [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones). La méthode retourne une collection générique [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) d’objets [TimeZoneInfo](xref:System.TimeZoneInfo). Les entrées présentes dans la collection sont triées par leur propriété [DisplayName](xref:System.TimeZoneInfo.DisplayName). Exemple :

    ```csharp
    ReadOnlyCollection<TimeZoneInfo> tzCollection;
    tzCollection = TimeZoneInfo.GetSystemTimeZones();
    ```

    ```vb
    Dim tzCollection As ReadOnlyCollection(Of TimeZoneInfo) = TimeZoneInfo.GetSystemTimeZones
    ```

2. Énumérez les objets [TimeZoneInfo](xref:System.TimeZoneInfo) individuels qui figurent dans la collection en utilisant une boucle `foreach` (en C#) ou `For Each…Next` (en Visual Basic), et exécutez tout les traitements nécessaires sur chaque objet. Par exemple, le code suivant énumère la collection [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) d’objets [TimeZoneInfo](xref:System.TimeZoneInfo) retournée à l’étape 1 et répertorie le nom complet de chaque fuseau horaire sur la console.

    ```csharp
    foreach (TimeZoneInfo timeZone in tzCollection)
    Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName);
    ```

    ```vb
    For Each timeZone As TimeZoneInfo In tzCollection
        Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName)
    Next
    ```

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)

[Recherche des fuseaux horaires définis sur un système local](finding-the-time-zones-on-local-system.md)


