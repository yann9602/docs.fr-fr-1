---
title: "dllMainReturnsFalse MDA | Microsoft Docs"
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
  - "managed debugging assistants (MDAs), DllMain returns false"
  - "DllMainReturnsFalse MDA"
  - "DllMain function"
  - "MDAs (managed debugging assistants), DllMain returns false"
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# dllMainReturnsFalse MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `dllMainReturnsFalse` est activé si la fonction `DllMain` managée d'un assembly utilisateur, appelée avec la raison DLL\_PROCESS\_ATTACH, retourne la valeur FALSE.  
  
## Symptômes  
 La fonction `DllMain` a retourné la valeur FALSE, indiquant qu'elle ne s'est pas exécutée correctement.  Cela peut entraîner des problèmes indéterminés car les fonctions `DllMain` contiennent en général un code d'initialisation important.  
  
## Cause  
 La fonction `DllMain` est appelée avec la raison DLL\_PROCESS\_ATTACH pour l'initialisation de la DLL lors du chargement.  Si elle retourne la valeur FALSE, cela signifie que l'initialisation de la DLL a échoué.  
  
## Résolution  
 Analysez le code de la fonction `DllMain` de l'échec de la DLL et identifiez la cause de l'erreur d'initialisation.  
  
## Effet sur le runtime  
 Ce MDA n'a aucun effet sur le CLR.  Il signale uniquement des données relatives à la valeur de retour pour `DllMain`.  
  
## Sortie  
 Un message indiquant qu'une fonction `DllMain`, appelée avec la raison DLL\_PROCESS\_ATTACH, a retourné la valeur FALSE.  Notez que ce MDA est activé uniquement si `DllMain` est implémentée dans le code managé.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)