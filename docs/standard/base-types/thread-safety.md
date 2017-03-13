---
title: "Sécurité des threads dans les expressions régulières"
description: "Sécurité des threads dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: dc64b681-b3aa-4911-8e30-0764a8b6a852
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 76cd207a9ff72f756a2fb48b9e02096507657cc0
ms.lasthandoff: 03/13/2017

---

# <a name="thread-safety-in-regular-expressions"></a>Sécurité des threads dans les expressions régulières

La classe [Regex](xref:System.Text.RegularExpressions.Regex) elle-même est thread-safe et immuable (en lecture seule). Autrement dit, des objets [Regex](xref:System.Text.RegularExpressions.Regex) peuvent être créés sur n’importe quel thread et partagés par plusieurs threads ; les méthodes de mise en correspondance peuvent être appelées à partir de n’importe quel thread et elles ne modifient jamais un état global.

Toutefois, les objets de résultat ([Match](xref:System.Text.RegularExpressions.Match) et [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection)) retournés par [Regex](xref:System.Text.RegularExpressions.Regex) doivent être utilisés sur un seul thread. Bien que bon nombre de ces objets soient logiquement immuables, leurs implémentations peuvent retarder le calcul de certains résultats pour améliorer les performances, et par conséquent, les appelants doivent en sérialiser l’accès.

S’il est nécessaire de partager des objets de résultat [Regex](xref:System.Text.RegularExpressions.Regex) sur plusieurs threads, ces objets peuvent être convertis en instances thread-safe en appelant leurs méthodes synchronisées. À l’exception des énumérateurs, toutes les classes d’expression régulière sont thread-safe ou peuvent être converties en objets thread-safe par une méthode synchronisée.

Les énumérateurs sont la seule exception. Une application doit sérialiser les appels aux énumérateurs de collections. La règle est que si une collection peut être énumérée simultanément sur plusieurs threads, vous devez synchroniser les méthodes d’énumération sur l’objet racine de la collection traversée par l’énumérateur.

## <a name="see-also"></a>Voir aussi

[Expressions régulières .NET](regular-expressions.md)


