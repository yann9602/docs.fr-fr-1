---
title: "Erreur du compilateur CS1569 | Microsoft Docs"
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
  - "CS1569"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1569"
ms.assetid: 1d5e89d6-0a05-4e4f-b472-9089146696bb
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1569
Erreur lors de la génération du fichier de documentation XML 'Filename' \('reason'\)  
  
 Lors d’une tentative d’écriture de la documentation XML dans le fichier nommé dans le message, une erreur s’est produite pour la raison spécifiée. La raison peut être par exemple « lecteur réseau introuvable » ou « accès refusé ». Souvent, la raison s’accompagne d’une suggestion de résolution de l’erreur. Par exemple, si l’erreur est « accès refusé », vous devez vérifier que vous avez l’autorisation d’écriture pour ce fichier.  
  
## Exemple  
  
```  
// 1569a.cs // compile with: /doc:CS1569.xml // post-build command: attrib +r CS1569.xml class Test { /// <summary>Test.</summary> public static void Main() {} }  
```  
  
## Exemple  
 L’exemple précédent a généré un fichier .xml qui a ensuite été défini en lecture seule. Cet exemple tente d’écrire dans ce même fichier. L’exemple suivant génère l’erreur CS1569.  
  
```  
// CS1569.cs // compile with: /doc:CS1569.xml // CS1569 expected class Test { /// <summary>Test.</summary> public static void Main() {} }  
  
```