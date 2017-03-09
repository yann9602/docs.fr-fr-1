---
title: "Path/File access error | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID75"
dev_langs: 
  - "VB"
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Path/File access error
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Au cours d'une opération d'accès au fichier ou au disque, le système d'exploitation n'a pas pu établir de liaison entre le chemin d'accès et le nom de fichier.  
  
### Pour corriger cette erreur  
  
1.  Assurez\-vous que la spécification de fichier est correctement mise en forme.  Un nom de fichier peut contenir un chemin d'accès qualifié complet \(absolu\) ou relatif.  Un chemin d'accès qualifié complet commence par le nom du lecteur \(si le chemin d'accès se trouve sur un autre lecteur\) et répertorie le chemin explicite de la racine au fichier.  Tout chemin non complet est relatif au lecteur actif et au répertoire en cours.  
  
2.  Vérifiez que vous n'avez pas tenté d'enregistrer un fichier qui remplacerait un fichier existant en lecture seule.  Si tel est le cas, modifiez l'attribut de lecture seule du fichier cible ou enregistrez le fichier sous un nom différent.  
  
3.  Vérifiez que vous n'avez pas tenté d'ouvrir un fichier en lecture seule en mode séquentiel`Output`ou `Append`.  Si tel est le cas, ouvrez le fichier en mode `Input` ou modifiez l'attribut en lecture seule du fichier.  
  
4.  Vérifiez que vous n'avez pas tenté de modifier un projet [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] à l'intérieur d'une base de données ou d'un document.  
  
## Voir aussi  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)