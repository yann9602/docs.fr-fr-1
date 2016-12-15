---
title: "How to: Create a Registry Key and Set Its Value in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RegistryKey.CreateSubKey"
  - "RegistryKey.SetValue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "registry keys, creating"
  - "registry, adding values"
  - "registry, adding keys"
  - "registry keys, setting values"
  - "examples [Visual Basic], registry"
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a Registry Key and Set Its Value in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

La méthode `CreateSubKey` de l'objet `My.Computer.Registry` peut être utilisée pour créer une clé de Registre.  
  
## Procédure  
  
#### Pour créer une clé de Registre  
  
-   Utilisez la méthode `CreateSubKey`, en spécifiant sous quelle ruche placer la clé ainsi que le nom de la clé.  Le paramètre  `Subkey`  ne respecte pas la casse.  Cet exemple crée la clé de Registre `MyTestKey` sous HKEY\_CURRENT\_USER.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### Pour créer une clé de Registre et y définir une valeur  
  
1.  Utilisez la méthode `CreateSubkey`, en spécifiant sous quelle ruche placer la clé ainsi que le nom de la clé.  Cet exemple crée la clé de Registre `MyTestKey` sous HKEY\_CURRENT\_USER.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  Définissez la valeur avec la méthode `SetValue`.  Cet exemple définit la valeur de chaîne "  "MyTestKeyValue" sur "This is a test value".  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## Exemple  
 Cet exemple crée la clé de Registre `MyTestKey` sous HKEY\_CURRENT\_USER, puis définit la valeur de chaîne `MyTestKeyValue` à `This is a test value`.  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## Programmation fiable  
 Examinez la structure du Registre afin de trouver un emplacement approprié pour votre clé.  Par exemple, vous souhaiterez peut\-être ouvrir la clé HKEY\_CURRENT\_USER\\Software de l'utilisateur actuel et créer une clé avec le nom de votre société.  Vous pouvez ensuite ajouter les valeurs du Registre à la clé de votre société.  
  
 Lors de la lecture du Registre à partir d'une application Web, l'utilisateur en cours dépend de l'authentification et de l'emprunt d'identité implémentés dans l'application Web.  
  
 Pour des raisons de sécurité, il est préférable d'écrire des données dans le dossier utilisateur \(<xref:Microsoft.Win32.Registry.CurrentUser>\) plutôt que sur l'ordinateur local \(<xref:Microsoft.Win32.Registry.LocalMachine>\).  
  
 Lorsque vous créez une valeur de Registre, vous devez déterminer la marche à suivre si cette valeur existe déjà.  Il est possible qu'un autre processus, peut\-être nuisible, ait déjà créé la valeur et puisse y accéder.  Lorsque vous placez des données dans la valeur du Registre, elles sont disponibles pour les autres processus.  Pour empêcher cela, utilisez la méthode <xref:Microsoft.Win32.RegistryKey.GetValue%2A>.  Elle retourne `Nothing` si la clé n'existe pas.  
  
 Pour des raisons de sécurité, il est déconseillé de stocker des données confidentielles, telles que des mots de passe, en texte brut dans le Registre, même si la clé de Registre est protégée par des listes de contrôle d'accès \(ACL, Access Control Lists\).  
  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le nom de la clé est `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   L'utilisateur n'a pas l'autorisation de créer des clés de Registre \(<xref:System.Security.SecurityException>\).  
  
-   Le nom de la clé dépasse la limite de 255 caractères \(<xref:System.ArgumentException>\).  
  
-   La clé est fermée \(<xref:System.IO.IOException>\).  
  
-   La clé de Registre est en lecture seule \(<xref:System.UnauthorizedAccessException>\).  
  
## Sécurité .NET Framework  
 Pour exécuter ce processus, votre assembly requiert un niveau de privilège accordé par la classe <xref:System.Security.Permissions.RegistryPermission>.  Si vous exécutez le programme dans un contexte partiellement fiable, le processus peut lever une exception en raison de privilèges insuffisants.  De même, l'utilisateur doit posséder les listes de contrôles d'accès appropriées pour pouvoir créer des paramètres ou écrire dans ceux\-ci.  Par exemple, une application locale disposant d'une autorisation de sécurité d'accès du code peut ne pas avoir une autorisation du système d'exploitation.  Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../Topic/Code%20Access%20Security%20Basics.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>   
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)   
 [Notions fondamentales de la sécurité d'accès du code](../Topic/Code%20Access%20Security%20Basics.md)