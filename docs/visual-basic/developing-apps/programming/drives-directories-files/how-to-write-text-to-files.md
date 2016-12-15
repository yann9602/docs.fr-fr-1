---
title: "How to: Write Text to Files in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "files, writing to"
  - "text, writing to files"
  - "writing to files"
  - "examples [Visual Basic], text files"
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Write Text to Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> peut être utilisée pour écrire du texte dans des fichiers.  Si le fichier cible n'existe pas, il est créé.  
  
## Procédure  
  
#### Pour écrire du texte dans un fichier  
  
-   Utilisez la méthode `WriteAllText` pour écrire du texte dans un fichier en spécifiant le fichier et le texte à écrire.  Cet exemple écrit la ligne `"This is new text."` dans le fichier nommé `test.txt` en ajoutant le texte à un texte existant dans le fichier.  
  
     [!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]  
  
#### Pour écrire une série de chaînes dans un fichier  
  
-   Parcourez la collection de chaînes.  Utilisez la méthode `WriteAllText` pour écrire du texte dans un fichier en spécifiant le fichier cible et la chaîne à ajouter et en affectant à `append` la valeur `True`.  
  
     Cet exemple écrit les noms des fichiers du répertoire `Documents and Settings` dans `FileList.txt`, ce qui insère un retour chariot entre chacun d'eux pour une meilleure lisibilité.  
  
     [!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le chemin d'accès n'est pas valide pour l'une des raisons suivantes : il correspond à une chaîne de longueur nulle, ne contient que des espaces blancs, comporte des caractères non valides ou représente un chemin d'accès de périphérique \(commençant par \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `File` pointe vers un chemin d'accès qui n'existe pas \(<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>\).  
  
-   Le fichier est utilisé par un autre processus, ou une erreur E\/S se produit \(<xref:System.IO.IOException>\).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système \(<xref:System.IO.PathTooLongException>\).  
  
-   Un nom de fichier ou de répertoire du chemin d'accès contient un signe deux\-points \(:\) ou n'a pas un format correct \(<xref:System.NotSupportedException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès \(<xref:System.Security.SecurityException>\).  
  
-   Le disque est plein et l'appel à `WriteAllText` échoue \(<xref:System.IO.IOException>\).  
  
 Si vous exécutez le programme dans un contexte partiellement fiable, le code peut lever une exception en raison de privilèges insuffisants.  Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../Topic/Code%20Access%20Security%20Basics.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 [How to: Read from Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)