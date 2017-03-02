---
title: "Compilation et réutilisation dans les expressions régulières"
description: "Compilation et réutilisation dans les expressions régulières"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3adea434-e2ed-4023-b4f5-b0608b4cf53f
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 7b3acb4571cddc19520f8534828d94844c9d59e6
ms.lasthandoff: 03/02/2017

---

# <a name="compilation-and-reuse-in-regular-expressions"></a>Compilation et réutilisation dans les expressions régulières

Vous pouvez optimiser les performances des applications qui utilisent très souvent des expressions régulières en comprenant comment le moteur d’expression régulière compile les expressions et comment les expressions régulières sont mises en cache. Cette rubrique décrit la compilation et la mise en cache.

## <a name="compiled-regular-expressions"></a>Expressions régulières compilées

Par défaut, le moteur d’expression régulière compile une expression régulière en une séquence d’instructions internes (il s’agit des codes généraux différents de MSIL, ou Microsoft Intermediate Language). Quand le moteur exécute une expression régulière, il interprète les codes internes.

Si un objet [Regex](xref:System.Text.RegularExpressions.Regex) est construit avec l’option [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled), il compile l’expression régulière en code MSIL explicite plutôt qu’en instructions internes d’expression régulière générale. Ainsi, le compilateur juste-à-temps (JIT) de .NET convertit l’expression en code machine natif pour de meilleures performances.

Toutefois, le MSIL généré ne peut pas être déchargé. La seule façon de décharger du code consiste à décharger un domaine d’application dans son intégralité (autrement dit, à décharger tout le code de vos applications). En effet, une fois qu’une expression régulière est compilée avec l’option [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled), .NET ne libère jamais les ressources utilisées par l’expression compilée, même si l’expression régulière a été créée par un objet [Regex](xref:System.Text.RegularExpressions.Regex) lui-même libéré par nettoyage de la mémoire.

Vous devez veiller à limiter le nombre d’expressions régulières différentes que vous compilez avec l’option [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) pour éviter de consommer trop de ressources. Si une application doit utiliser un nombre important ou illimité d’expressions régulières, chaque expression doit être interprétée, et non compilée. Toutefois, si un petit nombre d’expressions régulières est utilisé à plusieurs reprises, elles doivent être compilées avec l’option [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) pour de meilleures performances. 

## <a name="the-regular-expressions-cache"></a>Cache des expressions régulières

Pour améliorer les performances, le moteur d’expression régulière gère un cache à l’échelle de l’application des expressions régulières compilées. Ce cache stocke les modèles d’expression régulière utilisés uniquement dans les appels de méthode statique. (Les modèles d’expression régulière fournis aux méthodes d’instance ne sont pas mis en cache.) Ainsi, la nécessité de réanalyser une expression en code d’octet principal à chacune de ses utilisations est évité.

Le nombre maximal d’expressions régulières mises en cache est déterminé par la valeur de la propriété `static` (`Shared` en Visual Basic) [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize). Par défaut, le moteur d’expression régulière met en cache jusqu’à 15 expressions régulières compilées. Si le nombre d’expressions régulières compilées dépasse la taille du cache, l’expression régulière la plus anciennement utilisée est ignorée et la nouvelle expression régulière est mise en cache. 

Votre application peut tirer parti des expressions régulières précompilées de l’une des deux manières suivantes :

* En utilisant une méthode statique de l’objet [Regex](xref:System.Text.RegularExpressions.Regex) pour définir l’expression régulière. Si vous utilisez un modèle d’expression régulière qui a déjà été défini dans un autre appel de méthode statique, le moteur d’expression régulière le récupère à partir du cache. Si ce n’est pas le cas, le moteur compile l’expression régulière et l’ajoute au cache.

* En réutilisant un objet [Regex](xref:System.Text.RegularExpressions.Regex) existant tant que son modèle d’expression régulière est nécessaire.


En raison de la surcharge liée à l’instanciation d’objets et à la compilation d’expressions régulières, la création et la destruction rapide d’un grand nombre d’objets [Regex](xref:System.Text.RegularExpressions.Regex) est un processus très coûteux. Pour les applications qui utilisent un grand nombre d’expressions régulières différentes, vous pouvez optimiser les performances en utilisant des appels de méthodes [Regex](xref:System.Text.RegularExpressions.Regex) statiques et en augmentant éventuellement la taille du cache des expressions régulières.

## <a name="see-also"></a>Voir aussi

[Expressions régulières .NET](regular-expressions.md)


