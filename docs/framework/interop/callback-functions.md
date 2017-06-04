---
title: "Callback Functions | Microsoft Docs"
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
  - "callback function"
  - "platform invoke, calling unmanaged functions"
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Callback Functions
Une fonction de rappel désigne du code figurant dans une application managée qui permet à une fonction DLL non managée d'effectuer une tâche.  Les appels à une fonction de rappel sont indirectement passés à une application managée via une fonction DLL avant de revenir à l'implémentation managée.  Certaines des nombreuses fonctions DLL appelées à l'aide de l'appel de code non managé nécessitent une fonction de rappel dans du code managé pour fonctionner correctement.  
  
 Pour appeler la plupart des fonctions DLL à partir d'un code managé, il vous suffit de créer une définition managée de la fonction, puis de l'appeler.  La procédure est simple.  
  
 L'utilisation d'une fonction DLL nécessitant une fonction de rappel implique des étapes supplémentaires.  Vous devez d'abord déterminer si la fonction nécessite un rappel en consultant la documentation sur la fonction.  Vous devez ensuite créer la fonction de rappel dans votre application managée.  Vous devez enfin appeler la fonction DLL, en passant un pointeur vers la fonction de rappel sous la forme d'un argument.  L'illustration ci\-dessous récapitule ces étapes.  
  
 ![Rappel d'appel de plateforme](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")  
Fonction de rappel et implémentation  
  
 Les fonctions de rappel sont idéales dans les cas où une tâche est effectuée à maintes reprises.  Elles sont aussi fréquemment utilisées avec des fonctions d'énumération, telles que **EnumFontFamilies**, **EnumPrinters** et **EnumWindows**, dans l'interface API Win32.  La fonction **EnumWindows** se décline dans toutes les fenêtres existantes de votre ordinateur ; dans chacune, elle appelle la fonction de rappel pour exécuter une tâche.  Pour obtenir des instructions et un exemple, consultez [Comment faire: Implémenter des fonctions de rappel](../../../docs/framework/interop/how-to-implement-callback-functions.md).  
  
## Voir aussi  
 [How to: Implement Callback Functions](../../../docs/framework/interop/how-to-implement-callback-functions.md)   
 [Calling a DLL Function](../../../docs/framework/interop/calling-a-dll-function.md)