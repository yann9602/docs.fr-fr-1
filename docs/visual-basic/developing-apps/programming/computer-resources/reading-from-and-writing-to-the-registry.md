---
title: "Reading from and Writing to the Registry (Visual Basic) | Microsoft Docs"
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
  - "My.Computer.Registry object, tasks"
  - "registry, writing to"
  - "registry, reading"
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Reading from and Writing to the Registry (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette rubrique décrit la tâche et les rubriques conceptuelles associées au Registre.  
  
 Lorsque vous programmez en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], vous pouvez choisir d'accéder au Registre via les fonctions fournies par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ou via les classes de Registre du .NET Framework.  Le Registre contient des informations provenant du système d'exploitation et des applications hébergées sur l'ordinateur.  L'utilisation du Registre peut compromettre la sécurité par l'accord d'accès inappropriés aux ressources du système ou aux informations protégées.  
  
## Dans cette section  
 [How to: Create a Registry Key and Set Its Value](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 Décrit comment utiliser les méthodes de `CreateSubKey` et d' `SetValue` d'objet d' `My.Computer.Registry` pour créer une clé de Registre et définir sa valeur.  
  
 [How to: Read a Value from a Registry Key](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 Décrit comment utiliser la méthode d' `GetValue` d'objet d' `My.Computer.Registry` pour lire une valeur d'une clé de Registre.  
  
 [How to: Delete a Registry Key](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 Décrit comment utiliser la méthode d' `DeleteSubKey` de propriété d' `My.Computer.Registry.CurrentUser` pour supprimer une clé de Registre.  
  
 [Lecture et écriture dans le Registre à l'aide de l'espace de noms Microsoft.Win32](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Décrit comment utiliser les classes d' `Registry` et d' `RegistryKey` de [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] pour accéder au Registre.  
  
 [Security and the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 Décrit les problèmes de sécurité liés à l'utilisation du Registre.  
  
## Rubriques connexes  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Répertorie et décrit les membres de l'objet `My.Computer.Registry`.  
  
 <xref:Microsoft.Win32.Registry>  
 Fournit une vue d'ensemble de la classe `Registry`, avec des liens vers les clés et les membres.