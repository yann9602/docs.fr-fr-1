---
title: "Compilation et r&#233;utilisation dans les expressions r&#233;guli&#232;res | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework (expressions régulières), compilation"
  - ".NET Framework (expressions régulières), moteurs"
  - "compilation, expressions régulières"
  - "analyser du texte avec des expressions régulières, compilation"
  - "mise en correspondance de modèles avec des expressions régulières, compilation"
  - "expressions régulières, compilation"
  - "expressions régulières, moteurs"
  - "rechercher avec des expressions régulières, compilation"
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Compilation et r&#233;utilisation dans les expressions r&#233;guli&#232;res
Pour optimiser les performances des applications qui utilisent très souvent des expressions régulières, il est important de comprendre comment le moteur des expressions régulières compile des expressions et comment les expressions régulières sont mises en cache.  Cette rubrique traite de la compilation et de la mise en cache.  
  
## Expressions régulières compilées  
 Par défaut, le moteur des expressions régulières compile une expression régulière sous la forme d'une séquence d'instructions internes \(il s'agit de codes avancés différents du langage MSIL \(MSIL, Microsoft Intermediate Language\).  Lorsque le moteur exécute une expression régulière, il interprète les codes internes.  
  
 Si un objet <xref:System.Text.RegularExpressions.Regex> est construit avec l'option <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>, il compile l'expression régulière sous forme de code MSIL explicite au lieu d'instructions internes d'expressions régulières avancées.  Cela permet au compilateur juste\-à\-temps \(JIT\) du .NET Framework de convertir l'expression en code machine natif afin d'obtenir de meilleures performances.  
  
 Cependant, le MSIL généré ne peut pas être déchargé.  La seule façon de décharger du code consiste à décharger l'intégralité d'un domaine d'application \(c'est\-à\-dire à décharger tout le code de votre application.\).  Effectivement, une fois qu'une expression régulière est compilée avec l'option <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>, le .NET Framework ne libère plus les ressources utilisées par l'expression compilée, même si l'expression régulière a été créée par un objet <xref:System.Text.RegularExpressions.Regex> faisant lui\-même l'objet d'un garbage collection.  
  
 Vous devez veiller à limiter le nombre d'expressions régulières différentes que vous compilez avec l'option <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> afin d'éviter de consommer trop de ressources.  Si une application doit utiliser un nombre important ou illimité d'expressions régulières, chaque expression doit être interprétée, pas compilée.  Toutefois, si seules quelques expressions régulières sont utilisées de façon récurrente, elles doivent être compilées avec <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> dans le but d'obtenir de meilleures performances.  Une autre solution consiste à utiliser des expressions régulières précompilées.  Vous pouvez compiler l'ensemble de vos expressions dans un fichier .dll réutilisable à l'aide de la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A>.  Il devient alors inutile de compiler au moment de l'exécution, mais vous bénéficiez néanmoins de la rapidité d'expressions régulières compilées.  
  
## Cache d'expressions régulières  
 Pour améliorer les performances, le moteur des expressions régulières maintient un cache d'expressions régulières compilées au niveau de l'application.  Le cache stocke des modèles d'expressions régulières qui sont utilisés uniquement dans les appels de méthode statique. \(Les modèles d'expressions régulières fournis aux méthodes d'instance ne sont pas mis en cache.\) Cela évite toute nouvelle analyse d'une expression en code avancé lors de chaque utilisation.  
  
 Le nombre maximal d'expressions régulières mises en cache est déterminé par la valeur de la propriété `static` \(`Shared` en Visual Basic\) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=fullName>.  Par défaut, le moteur des expressions régulières met en cache jusqu'à 15 expressions régulières compilées.  Si le nombre d'expressions régulières compilées dépasse la taille de la mémoire cache, l'expression régulière la moins récemment utilisée est ignorée et la nouvelle expression régulière est mise en cache.  
  
> [!IMPORTANT]
>  La méthode de mise en cache des expressions régulières dans le .NET Framework version 2.0 diffère considérablement dans les versions 1.0 et 1.1 du .NET Framework.  Dans le .NET Framework 1.0 et 1.1, toutes les expressions régulières, qu'elles soient utilisées dans les appels de méthode statique ou d'instance, sont mises en cache.  Le cache est développé automatiquement pour stocker de nouvelles expressions régulières.  Seules les expressions régulières utilisées dans les appels de méthode statique sont mises en cache dans .NET Framework 2.0.  Par défaut, les 15 dernières expressions régulières sont mises en cache, bien que la taille du cache puisse être ajustée en définissant la valeur de la propriété <xref:System.Text.RegularExpressions.Regex.CacheSize%2A>.  
  
 Votre application peut tirer parti des expressions régulières précompilées de l'une des deux manières suivantes :  
  
-   En utilisant une méthode statique de l'objet <xref:System.Text.RegularExpressions.Regex> pour définir l'expression régulière.  Si vous utilisez un modèle d'expression régulière qui a déjà été défini dans un autre appel de méthode statique, le moteur des expressions régulières le récupérera dans le cache.  Dans le cas contraire, le moteur compilera l'expression régulière et l'ajoutera au cache.  
  
-   En réutilisant un objet <xref:System.Text.RegularExpressions.Regex> existant tant que son modèle d'expression régulière est requis.  
  
 La création et la destruction rapide de nombreux objets <xref:System.Text.RegularExpressions.Regex> est un processus très coûteux en raison du temps de traitement de l'instanciation d'objet et de la compilation d'expressions régulières.  Vous pouvez optimiser les performances des applications utilisant un grand nombre d'expressions régulières différentes en ayant recours aux appels de méthodes `Regex` statiques et en augmentant la taille du cache d'expression régulière.  
  
## Voir aussi  
 [Expressions régulières du .NET Framework](../../../docs/standard/base-types/regular-expressions.md)