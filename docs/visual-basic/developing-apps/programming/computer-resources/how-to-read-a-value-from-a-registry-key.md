---
title: "How to: Read a Value from a Registry Key in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "registry keys, determining if a value exists in"
  - "My.Computer.Registry object, examples"
  - "registry, determining if values exist"
  - "registry keys, reading from"
  - "registry, reading"
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: 31
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 31
---
# How to: Read a Value from a Registry Key in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La méthode `GetValue` de l'objet `My.Computer.Registry` peut être utilisée pour lire des valeurs dans le Registre de Windows.  
  
 Si la clé, « software \\MyApp » dans l'exemple suivant, n'existe pas, une exception est levée.  Si `ValueName`, « nom » dans l'exemple suivant, n'existe pas, `Nothing` est retourné.  
  
 La méthode d' `GetValue` peut également être utilisée pour déterminer si une valeur donnée existe dans une clé de Registre spécifique.  
  
 Lorsque le code lit le Registre d'une application Web, l'utilisateur actuel est déterminé par l'authentification et l'emprunt d'identité qui est implémenté dans l'application Web.  
  
### Pour lire une valeur à partir d'une clé de Registre  
  
-   Utilisez la méthode `GetValue` \(en spécifiant le chemin d'accès et le nom\) pour lire une valeur de clé de Registre.  L'exemple suivant lit la valeur `Name` de `HKEY_CURRENT_USER\Software\MyApp` et l'affiche dans une boîte de message.  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, il se trouve dans **Système d'exploitation Windows \> Registre**.  Pour plus d'informations, consultez [Extraits de code](/visual-studio/ide/code-snippets).  
  
### Pour déterminer si une valeur existe dans une clé de Registre  
  
-   Utilisez la méthode `GetValue` pour récupérer la valeur.  Le code suivant vérifie si la valeur existe et retourne un message dans le cas contraire.  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## Programmation fiable  
 Le Registre contient des clés de niveau supérieur \(ou racine\) qui sont utilisées pour stocker des données.  Par exemple, la clé racine HKEY\_LOCAL\_MACHINE est utilisée pour stocker des paramètres au niveau de l'ordinateur utilisés par tous les utilisateurs, tandis que HKEY\_CURRENT\_USER est utilisé pour stocker des données spécifiques à un utilisateur individuel.  
  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le nom de la clé est `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   L'utilisateur n'a pas l'autorisation de lire à partir de clés de Registre \(<xref:System.Security.SecurityException>\).  
  
-   Le nom de la clé dépasse la limite de 255 caractères \(<xref:System.ArgumentException>\).  
  
## Sécurité .NET Framework  
 Pour exécuter ce processus, votre assembly requiert un niveau de privilège accordé par la classe <xref:System.Security.Permissions.RegistryPermission>.  Si vous exécutez le programme dans un contexte partiellement fiable, le processus peut lever une exception en raison de privilèges insuffisants.  De même, l'utilisateur doit posséder les listes de contrôles d'accès appropriées pour pouvoir créer des paramètres ou écrire dans ceux\-ci.  Par exemple, une application locale disposant d'une autorisation de sécurité d'accès du code peut ne pas avoir une autorisation du système d'exploitation.  Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../Topic/Code%20Access%20Security%20Basics.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 <xref:Microsoft.Win32.RegistryHive>   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)