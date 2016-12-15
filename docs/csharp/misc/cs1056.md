---
title: "Erreur du compilateur CS1056 | Microsoft Docs"
ms.custom: ""
ms.date: "09/30/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1056"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1056"
ms.assetid: bf66d164-ab5b-4181-b93e-a1d29620b4d2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1056
Caractère inattendu 'character'  
  
 Le compilateur C\# a rencontré un caractère inattendu et ne peut pas identifier le jeton en cours de traitement. Par exemple, si le compilateur rencontre le caractère de l’euro pendant le traitement d’un identificateur, il ne peut pas classer l’identificateur parce que le caractère de l’euro n’est valide qu’à l’intérieur d’une chaîne et que le compilateur sait qu’il ne traite pas une chaîne.