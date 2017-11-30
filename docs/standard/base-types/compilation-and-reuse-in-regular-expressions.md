---
title: "Compilation et réutilisation dans les expressions régulières"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET Framework regular expressions, engines
- .NET Framework regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 76acdf2d0d2f7805ec78ea44136bfc63441b9bc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Compilation et réutilisation dans les expressions régulières
Vous pouvez optimiser les performances des applications qui utilisent très souvent des expressions régulières en comprenant comment le moteur d’expression régulière compile les expressions et comment les expressions régulières sont mises en cache. Cette rubrique décrit la compilation et la mise en cache.  
  
## <a name="compiled-regular-expressions"></a>Expressions régulières compilées  
 Par défaut, le moteur d’expression régulière compile une expression régulière en une séquence d’instructions internes (il s’agit des codes généraux différents de MSIL, ou Microsoft Intermediate Language). Quand le moteur exécute une expression régulière, il interprète les codes internes.  
  
 Si un <xref:System.Text.RegularExpressions.Regex> objet est construit avec la <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> option, il compile l’expression régulière de code MSIL explicite au lieu d’instructions internes d’expressions régulières. Ainsi, le compilateur juste-à-temps (JIT) de .NET convertit l’expression en code machine natif pour de meilleures performances.  
  
Toutefois, le MSIL généré ne peut pas être déchargé. La seule façon de décharger du code consiste à décharger un domaine d’application dans son intégralité (autrement dit, à décharger tout le code de vos applications). En effet, une fois qu’une expression régulière est compilée avec le <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> option, ne libère les ressources utilisées par l’expression compilée, même si l’expression régulière a été créée par un <xref:System.Text.RegularExpressions.Regex> objet qui est lui-même un garbage collection.  
  
 Vous devez veiller à limiter le nombre d’expressions régulières différentes que vous compilez avec le <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> option permet d’éviter de consommer trop de ressources. Si une application doit utiliser un nombre important ou illimité d’expressions régulières, chaque expression doit être interprétée, et non compilée. Toutefois, si un petit nombre d’expressions régulières est utilisé à plusieurs reprises, elles doivent être compilées avec <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> pour de meilleures performances. Une alternative consiste à utiliser des expressions régulières précompilées. Vous pouvez compiler l’ensemble de vos expressions dans une DLL réutilisable à l’aide de la <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> (méthode). Cela évite de devoir compiler lors de l’exécution tout en bénéficiant toujours de la rapidité d’expressions régulières compilées.  
  
## <a name="the-regular-expressions-cache"></a>Cache des expressions régulières  
 Pour améliorer les performances, le moteur d’expression régulière gère un cache à l’échelle de l’application des expressions régulières compilées. Ce cache stocke les modèles d’expression régulière utilisés uniquement dans les appels de méthode statique. (Les modèles d’expression régulière fournis aux méthodes d’instance ne sont pas mis en cache.) Ainsi, la nécessité de réanalyser une expression en code d’octet principal à chacune de ses utilisations est évité.  
  
 Le nombre maximal d’expressions régulières mises en cache est déterminé par la valeur de la `static` (`Shared` en Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> propriété. Par défaut, le moteur d’expression régulière met en cache jusqu’à 15 expressions régulières compilées. Si le nombre d’expressions régulières compilées dépasse la taille du cache, l’expression régulière la plus anciennement utilisée est ignorée et la nouvelle expression régulière est mise en cache.  
  
 Votre application peut tirer parti des expressions régulières précompilées de l’une des deux manières suivantes :  
  
-   À l’aide d’une méthode statique de la <xref:System.Text.RegularExpressions.Regex> objet pour définir l’expression régulière. Si vous utilisez un modèle d’expression régulière qui a déjà été défini dans un autre appel de méthode statique, le moteur d’expression régulière le récupère à partir du cache. Si ce n’est pas le cas, le moteur compile l’expression régulière et l’ajoute au cache.  
  
-   En réutilisant un existant <xref:System.Text.RegularExpressions.Regex> objet tant que son modèle d’expression régulière est requis.  
  
 Raison de la charge de l’instanciation d’objet et de la compilation d’expressions régulières, création et destruction rapide de nombreux <xref:System.Text.RegularExpressions.Regex> objets est un processus très coûteux. Pour les applications qui utilisent un grand nombre d’expressions régulières différentes, vous pouvez optimiser les performances en utilisant des appels statique `Regex` méthodes et en augmentant la taille du cache d’expression régulière.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions régulières .NET](../../../docs/standard/base-types/regular-expressions.md)
