---
title: "x:Code Intrinsic XAML Type | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Code"
  - "x:Code"
  - "xCode"
helpviewer_keywords: 
  - "Code directive in XAML [XAML Services]"
  - "x:Code XAML directive element [XAML Services]"
  - "XAML [XAML Services], x:Code directive element"
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: 19
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 19
---
# x:Code Intrinsic XAML Type
Autorise le positionnement de code dans une production XAML.  Un tel code peut être compilé par une implémentation du processeur XAML qui compile le code XAML, ou laissé dans la production XAML pour une utilisation ultérieure, par exemple l'interprétation par une exécution.  
  
## Utilisation d'éléments objet XAML  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## Notes  
 Le code figurant dans l'élément de directive XAML `x:Code` est toujours interprété dans l'espace de noms XML général et les espaces de noms XAML fournis.  Par conséquent, il est habituellement nécessaire de placer le code utilisé pour `x:Code` à l'intérieur d'un segment `CDATA`.  
  
 `x:Code` n'est pas autorisé pour tous les mécanismes de déploiement d'une production XAML.  Dans des infrastructures spécifiques \(par exemple WPF\) le code doit être compilé.  Dans d'autres infrastructures, l'utilisation `x:Code` peut être refusée de façon générale.  
  
 Pour les infrastructures qui autorisent le contenu `x:Code` managé, le compilateur de langage correct à utiliser pour le contenu `x:Code` est déterminé par les paramètres et les cibles du projet contenant utilisé pour compiler l'application.  
  
## Remarques sur l'utilisation de WPF  
 Le code déclaré dans `x:Code` pour WPF a plusieurs limitations notables :  
  
-   L'élément de directive `x:Code` doit être un élément enfant immédiat de l'élément racine de la production XAML.  
  
-   [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) doit être fourni sur l'élément racine parent.  
  
-   Le code placé dans `x:Code` sera traité par compilation pour figurer dans la portée de la classe partielle qui est déjà en cours de création pour cette page XAML.  Par conséquent, tous les codes que vous définissez doivent être des membres ou variables de cette classe partielle.  
  
-   Vous ne pouvez pas définir de classes supplémentaires autrement qu'en imbriquant une classe à l'intérieur de la classe partielle \(l'imbrication est autorisée mais elle n'est pas générale car les classes imbriquées ne peuvent pas être référencées dans XAML\).  Il est impossible de définir ou d'ajouter des éléments à des espaces de noms CLR autres que l'espace de noms utilisé pour la classe partielle existante.  
  
-   Les références à des entités de code en dehors de l'espace de noms CLR de la classe partielle doivent être entièrement qualifiées.  Si des membres déclarés sont des substitutions des membres substituables de classes partielles, vous devez le spécifier à l'aide du mot clé de substitution spécifique au langage.  Si les membres déclarés en `x:Code` conflit avec des membres de la classe partielle créée hors du XAML, de sorte que le compilateur signale le conflit, le fichier XAML ne pourra pas compiler ou charger.  
  
## Voir aussi  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [Code\-behind et XAML dans WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)