---
title: "Trop de clients pour cette DLL | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID47"
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Trop de clients pour cette DLL
La bibliothèque de liens dynamiques \(DLL\) de [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] autorise uniquement l’accès à un nombre limité d’applications hôtes. Votre application et les autres applications qui sont des hôtes [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] \(dont certaines sont accessibles par votre application\) tentent toutes d’accéder à la DLL [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] en même temps.  
  
### Pour corriger cette erreur  
  
-   Réduisez le nombre d’applications ouvertes accédant à [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
## Voir aussi  
 [Error Types](../../visual-basic/programming-guide/language-features/error-types.md)