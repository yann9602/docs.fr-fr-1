---
title: "How to: Copy a Directory to Another Directory in Visual Basic | Microsoft Docs"
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
  - "I/O [Visual Basic], copying directories"
  - "I/O [Visual Basic], copying folders"
  - "folders [Visual Basic], copying"
  - "directories [Visual Basic], copying"
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Copy a Directory to Another Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Utilisez la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> pour copier un répertoire dans un autre répertoire.  Cette méthode copie le contenu du répertoire, ainsi que le répertoire lui\-même.  Si le répertoire cible n'existe pas, il sera créé.  Si un répertoire portant le même nom existe à l'emplacement cible et que `overwrite` a la valeur `False`, le contenu des deux répertoires sera fusionné.  Vous pouvez spécifier un nouveau nom pour le répertoire pendant l'opération.  
  
 Lors de la copie de fichiers dans un répertoire, des exceptions provoquées par un fichier spécifique, comme un fichier existant au cours d'une fusion alors que `overwrite` a la valeur `False`, peuvent être levées.  Lorsque de telles exceptions sont levées, elles sont consolidées en une seule exception dont la propriété `Data` comporte des entrées dans lesquelles le chemin d'accès au fichier ou au répertoire constitue la clé et le message d'exception spécifique est contenu dans la valeur correspondante.  
  
### Pour copier un répertoire dans un autre répertoire  
  
-   Utilisez la méthode `CopyDirectory` en spécifiant les noms de répertoires source et de destination.  L'exemple suivant copie le répertoire nommé `TestDirectory1` dans `TestDirectory2` en remplaçant les fichiers existants.  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-copy-a-directory-_1.vb)]  
  
     Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, il est localisé dans **Système de fichiers \- Traitement de lecteurs, de dossiers et de fichiers**.  Pour plus d'informations, consultez [Extraits de code](/visual-studio/ide/code-snippets).  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le nouveau nom spécifié pour le répertoire contient le signe deux\-points \(:\) ou une barre oblique \(\\ ou \/\) \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès n'est pas valide pour l'une des raisons suivantes : il correspond à une chaîne de longueur nulle, ne contient que des espaces blancs, comporte des caractères non valides ou représente un chemin d'accès de périphérique \(commençant par \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `destinationDirectoryName` a la valeur `Nothing` ou est une chaîne vide \(<xref:System.ArgumentNullException>\).  
  
-   Le dossier source n'existe pas \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   La source est un répertoire racine \(<xref:System.IO.IOException>\).  
  
-   Le chemin d'accès combiné pointe sur un fichier existant \(<xref:System.IO.IOException>\).  
  
-   Le chemin source et le chemin cible sont identiques \(<xref:System.IO.IOException>\).  
  
-   `ShowUI` a la valeur `UIOption.AllDialogs` et l'utilisateur annule l'opération, ou un ou plusieurs fichiers du répertoire ne peuvent pas être copiés \(<xref:System.OperationCanceledException>\).  
  
-   L'opération est cyclique \(<xref:System.InvalidOperationException>\).  
  
-   Le chemin d'accès contient le signe deux\-points \(:\) \(<xref:System.NotSupportedException>\).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système \(<xref:System.IO.PathTooLongException>\).  
  
-   Un nom de fichier ou de dossier du chemin d'accès contient un signe deux\-points \(:\) ou n'a pas un format correct \(<xref:System.NotSupportedException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès \(<xref:System.Security.SecurityException>\).  
  
-   Un fichier de destination existe mais est inaccessible \(<xref:System.UnauthorizedAccessException>\).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>   
 [How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [How to: Get the Collection of Files in a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)