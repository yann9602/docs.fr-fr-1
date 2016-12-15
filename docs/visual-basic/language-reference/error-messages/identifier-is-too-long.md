---
title: "Identifier is too long | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30033"
  - "vbc30033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30033"
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Identifier is too long
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le nom ou l'identificateur de chaque élément de programmation est limité à 1023 caractères.  De plus, un nom qualifié complet ne peut pas dépasser 1023 caractères.  Cela signifie que la totalité de la chaîne d'identificateur \(`<namespace>.<...>.<namespace>.<class>.<element>`\) ne peut pas dépasser 1023 caractères, opérateurs d'accès au membre \(`.`\) inclus.  
  
 **ID d'erreur :** BC30033  
  
### Pour corriger cette erreur  
  
-   Réduisez la longueur de l'identificateur.  
  
## Voir aussi  
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)