---
title: "Analyse de chaînes dans .NET"
description: "Analyse de chaînes dans .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8103c0a6-61d3-40dd-a3e9-2a32ba6a4c05
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: c741ae793d491f691a355df6ad064b81d609c7e5
ms.lasthandoff: 03/13/2017

---

# <a name="parsing-strings-in-net"></a>Analyse de chaînes dans .NET

Une opération d’analyse convertit une chaîne qui représente un type de base .NET en ce type de base. Par exemple, une opération d'analyse permet de convertir une chaîne en nombre à virgule flottante ou en valeur de date et d'heure. La méthode la plus couramment utilisée pour effectuer une opération d’analyse est la méthode `Parse`. Étant donné que l’analyse est l’opération inverse de la mise en forme (qui consiste à convertir un type de base en sa représentation sous forme de chaîne), de nombreuses règles et conventions identiques s’appliquent. Tout comme la mise en forme utilise un objet qui implémente l’interface [IFormatProvider](xref:System.IFormatProvider) pour fournir des informations de mise en forme dépendantes de la culture, l’analyse utilise un objet qui implémente l’interface [IFormatProvider](xref:System.IFormatProvider) pour déterminer comment interpréter une représentation sous forme de chaîne. Pour plus d’informations, consultez [Mise en forme des types dans .NET](formatting-types.md).

## <a name="in-this-section"></a>Dans cette section

[Analyse de chaînes numériques dans .NET](parsing-numeric.md) : explique comment convertir des chaînes en types numériques .NET.

[Analyse des chaînes de date et d’heure dans .NET](parsing-datetime.md) : explique comment convertir des chaînes en types `DateTime` .NET.

[Analyse d’autres chaînes dans .NET](parsing-other.md) : explique comment convertir des chaînes en types [Char](xref:System.Char), [Boolean](xref:System.Boolean) et [Enum](xref:System.Enum).

[Mise en forme des types dans .NET](formatting-types.md) : décrit les concepts de mise en forme de base, tels que les spécificateurs de format et les fournisseurs de format.

[Conversion de type dans .NET](type-conversion.md) : explique comment convertir des types.

[Utilisation des types de base dans .NET](index.md) : décrit les opérations courantes que vous pouvez effectuer sur les types de base .NET.


