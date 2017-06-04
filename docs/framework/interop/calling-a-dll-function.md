---
title: "Calling a DLL Function | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "unmanaged functions, calling"
  - "unmanaged functions"
  - "COM interop, platform invoke"
  - "platform invoke, calling unmanaged functions"
  - "interoperation with unmanaged code, platform invoke"
  - "DLL functions"
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Calling a DLL Function
Même si l'appel à des fonctions DLL non managées est quasiment identique à l'appel à un autre code managé, certaines différences peuvent rendre les fonctions DLL déconcertantes au départ.  Cette section présente des rubriques qui décrivent certaines questions relatives à des appels peu courants.  
  
 Les structures qui sont retournées par les appels de code non managé doivent être des types de données avec la même représentation dans le code managé et non managé.  Ces types sont appelés *types blittables* parce qu'ils ne nécessitent pas de conversion \(consultez [Blittable and Non\-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)\).  Pour appeler une fonction dont la structure n'est pas blittable comme type de retour, vous pouvez définir un type d'assistance blittable de la même taille qu'un type non blittable et convertir les données après le retour de la fonction.  
  
## Dans cette section  
 [Passage de structures](../../../docs/framework/interop/passing-structures.md)  
 Identifie les questions de passage de structures de données avec une disposition prédéfinie.  
  
 [Fonctions de rappel](../../../docs/framework/interop/callback-functions.md)  
 Fournit des informations de base sur les fonctions de rappel.  
  
 [Comment : implémenter des fonctions de rappel](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 Décrit comment implémenter des fonctions de rappel dans du code managé.  
  
## Rubriques connexes  
 [Consuming Unmanaged DLL Functions](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Décrit comment appeler des fonctions DLL non managées à l'aide de l'appel de code non managé.  
  
 [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 Décrit comment déclarer des paramètres de méthode et comment passer des arguments à des fonctions exportées par des bibliothèques non managées.