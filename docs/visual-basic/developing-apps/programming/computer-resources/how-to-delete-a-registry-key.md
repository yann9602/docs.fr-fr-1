---
title: "How to: Delete a Registry Key in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.DeleteSetting"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "GetSetting function"
  - "registry, deleting values"
  - "GetAllSettings function"
  - "registry keys, deleting"
  - "registry, deleting keys"
  - "examples [Visual Basic], registry"
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# How to: Delete a Registry Key in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les méthodes <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> et <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> peuvent être utilisées pour supprimer des clés de Registre.  
  
## Procédure  
  
#### Pour supprimer une clé de Registre  
  
-   Utilisez la méthode `DeleteSubKey` pour supprimer une clé de Registre.  Cet exemple supprime la clé Software\/TestApp dans la ruche CurrentUser.  Vous pouvez spécifier la chaîne appropriée dans le code ou faire en sorte que celui\-ci repose sur des informations fournies par l'utilisateur.  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## Programmation fiable  
 La méthode `DeleteSubKey` retourne une chaîne vide si la paire clé\/valeur n'existe pas.  
  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le nom de la clé est `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   L'utilisateur n'a pas l'autorisation de supprimer des clés de Registre \(<xref:System.Security.SecurityException>\).  
  
-   Le nom de la clé dépasse la limite de 255 caractères \(<xref:System.ArgumentException>\).  
  
-   La clé de Registre est en lecture seule \(<xref:System.UnauthorizedAccessException>\).  
  
## Sécurité .NET Framework  
 Les appels au Registre échouent lorsque l'utilisateur ne dispose pas des autorisations d'exécution nécessaires \(<xref:System.Security.Permissions.RegistryPermission>\) ou de l'accès correct \(tel que déterminé par les listes de contrôle d'accès\) pour créer ou modifier des paramètres.  Par exemple, une application locale disposant d'une autorisation de sécurité d'accès du code peut ne pas avoir une autorisation du système d'exploitation.  
  
## Voir aussi  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>   
 <xref:Microsoft.Win32.RegistryKey>   
 [Security and the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)