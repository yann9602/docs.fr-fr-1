---
title: "Erreur du compilateur CS1033 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1033"
ms.assetid: eb0f4001-84a6-4918-a648-cf710d038de7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1033
Le fichier source a dépassé la limite de 16 707 565 lignes pouvant être représentées dans le PDB ; les informations de débogage seront incorrectes  
  
 Un fichier de code source dépasse le nombre maximal de lignes autorisées que le compilateur peut traiter. Pour résoudre cette erreur, créez deux ou plusieurs fichiers de code source à partir du fichier d’origine. Le nombre maximal de lignes est égal à 268 435 454. Si vous utilisez **\/debug**, l’utilisation de plus de 16 707 566 lignes entraîne des informations de débogage endommagées.