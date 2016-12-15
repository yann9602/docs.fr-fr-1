---
title: "How to: Validate File Names and Paths in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "file names, validating"
  - "strings [Visual Basic], validating"
  - "Boolean values"
  - "paths, validating"
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Validate File Names and Paths in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cet exemple retourne une valeur `Boolean` qui indique si une chaîne représente un nom de fichier ou un chemin d'accès.  La validation vérifie si le nom contient des caractères qui ne sont pas autorisés par le système de fichiers.  
  
## Exemple  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 Cet exemple ne vérifie pas si le nom a placé des deux\-points incorrectement, ou des répertoires sans nom, ou encore si la longueur du nom dépasse la longueur maximale définie par le système.  Il ne vérifie pas non plus si l'application a l'autorisation nécessaire pour accéder à la ressource du système de fichiers avec le nom spécifié.  
  
## Voir aussi  
 <xref:System.IO.Path.GetInvalidPathChars%2A>   
 [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)