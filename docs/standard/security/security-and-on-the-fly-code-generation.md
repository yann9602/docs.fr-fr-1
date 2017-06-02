---
title: "S&#233;curit&#233; et g&#233;n&#233;ration de code imm&#233;diate | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sécurité du code, génération de code à la volée"
  - "génération de code à la volée"
  - "codage sécurisé, génération de code à la volée"
  - "sécurité (.NET Framework), génération de code à la volée"
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# S&#233;curit&#233; et g&#233;n&#233;ration de code imm&#233;diate
Certaines bibliothèques fonctionnent en générant du code et en l'exécutant afin d'effectuer certaines opérations pour l'appelant.  Le problème de base est la génération de code pour le compte de code d'un niveau de confiance moindre et son exécution à un niveau de confiance supérieur.  Ce problème se complique quand l'appelant peut influencer la génération du code ; vous devez donc vous assurer que seul du code que vous estimez sécurisé est généré.  
  
 Vous devez toujours savoir précisément quel code vous générez.  Cela signifie que vous devez avoir un contrôle strict sur toutes les valeurs que vous recevez d'un utilisateur, qu'il s'agisse de chaînes entourées de guillemets \(qui devraient être échappées, car elles ne peuvent pas inclure d'éléments de code inattendus\), d'identificateurs \(dont la validité doit être vérifiée\) ou de tout autre élément.  Les identificateurs peuvent être dangereux, car vous pouvez modifier un assembly compilé pour que ses identificateurs contiennent des caractères étranges qui risquent de le bloquer \(bien qu'il s'agisse rarement d'une faille en matière de sécurité\).  
  
 Nous vous recommandons de générer votre code à l'aide de l'émission de réflexion, qui vous aide souvent à éviter la plupart de ces problèmes.  
  
 Pendant la compilation du code, examinez s'il est possible pour un programme nuisible de le modifier.  Existe\-t\-il un laps de temps durant lequel du code nuisible peut changer du code source sur le disque avant sa lecture par le compilateur ou avant le chargement par votre code du fichier .dll ?  Si c'est le cas, vous devez protéger le répertoire contenant ces fichiers à l'aide de la sécurité d'accès du code ou d'une liste de contrôle d'accès dans le fichier système, en fonction de la situation.  
  
 Si un appelant peut influencer le code généré au point de provoquer une erreur de compilation, le risque dans ce cas d'une faille en matière de sécurité est possible.  
  
 Exécutez le code généré avec le niveau d'autorisation le moins élevé possible à l'aide de <xref:System.Security.Permissions.SecurityAction> ou [Deny](http://msdn.microsoft.com/fr-fr/6b4d2e01-c504-4ac3-b50e-d6f5e7f5df25).  
  
## Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)