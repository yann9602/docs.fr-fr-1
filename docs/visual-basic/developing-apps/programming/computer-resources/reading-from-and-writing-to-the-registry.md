---
title: "Lecture et écriture dans le Registre (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: db564b428d585829b220674271f4636bfcc68562
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>Lecture et écriture dans le Registre (Visual Basic)
Cette rubrique décrit les rubriques de concepts et de tâches associées au Registre.  
  
 Lorsque vous programmez en [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], vous pouvez choisir d’accéder au Registre via les fonctions fournies par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ou les classes registry du .NET Framework. Le Registre contient des informations provenant du système d’exploitation et des applications hébergées sur la machine. L’utilisation du Registre peut compromettre la sécurité en accordant un accès inapproprié à des ressources système ou à des informations protégées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique : créer une clé de Registre et définir sa valeur](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 Décrit comment utiliser les méthodes `CreateSubKey` et `SetValue` de l’objet `My.Computer.Registry` pour créer une clé de Registre et définir sa valeur.  
  
 [Guide pratique : lire une valeur à partir d’une clé de Registre](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 Décrit comment utiliser la méthode `GetValue` de l’objet `My.Computer.Registry` pour lire une valeur à partir d’une clé de Registre.  
  
 [Guide pratique : supprimer une clé de Registre](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 Décrit comment utiliser la méthode `DeleteSubKey` de la propriété `My.Computer.Registry.CurrentUser` pour supprimer une clé de Registre.  
  
 [Lecture et écriture dans le Registre à l’aide de l’espace de noms Microsoft.Win32](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Décrit comment utiliser les classes `Registry` et `RegistryKey` du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pour accéder au Registre.  
  
 [Sécurité et Registre](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 Décrit les problèmes de sécurité impliquant le Registre.  
  
## <a name="related-sections"></a>Rubriques connexes  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Répertorie et décrit les membres de l’objet `My.Computer.Registry`.  
  
 <xref:Microsoft.Win32.Registry>  
 Présente une vue d’ensemble de la classe `Registry`, ainsi que des liens vers des clés et des membres individuels.
